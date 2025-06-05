<template>
  <div ref="container" class="w-full h-full" />
</template>

<script>
import { Renderer, Program, Mesh, Triangle, Vec3 } from 'ogl'

export default {
  name: 'OrbComponent',
  props: {
    hue: { type: Number, default: 0 },
    hoverIntensity: { type: Number, default: 0.2 },
    rotateOnHover: { type: Boolean, default: true },
    forceHoverState: { type: Boolean, default: false }
  },
  mounted() {
    const container = this.$refs.container
    const vert = `
      precision highp float;
      attribute vec2 position;
      varying vec2 vUv;
      void main() {
        vUv = position * 0.5 + 0.5;
        gl_Position = vec4(position, 0, 1);
      }
    `
    const frag = `
      precision highp float;
      uniform float iTime;
      uniform vec3 iResolution;
      uniform float hue;
      uniform float hover;
      uniform float hoverIntensity;
      uniform float rot;
      varying vec2 vUv;

      vec3 hsl2rgb(vec3 hsl) {
        vec3 rgb = clamp( abs(mod(hsl.x*6. + vec3(0.,4.,2.), 6.) -3.) -1., 0., 1. );
        return hsl.z + hsl.y * (rgb - 0.5)*(1. - abs(2.*hsl.z - 1.));
      }

      float circle(vec2 uv, vec2 disc_center, float disc_radius, float border_size) {
        uv -= disc_center;
        uv *= iResolution.xy / min(iResolution.x, iResolution.y);
        float dist = sqrt(dot(uv, uv));
        return smoothstep(disc_radius+border_size, disc_radius-border_size, dist);
      }

      float random(vec2 st) {
        return fract(sin(dot(st.xy, vec2(12.9898,78.233))) * 43758.5453123);
      }

      void main() {
        vec2 uv = vUv;
        vec3 color = vec3(0.0);
        vec3 outerColor = hsl2rgb(vec3(hue, 1.0, 0.5));
        vec3 innerColor = hsl2rgb(vec3(hue + 0.1, 1.0, 0.5));

        float radius = 0.3 + 0.02 * sin(iTime);
        float border = 0.008 + hover * 0.015;
        float outerCircle = circle(uv, vec2(0.5), radius, border);
        float innerCircle = circle(uv, vec2(0.5), radius - 0.05, border);

        vec2 p = uv - vec2(0.5);
        float a = atan(p.y, p.x) + rot;
        float r = length(p);
        float rays = smoothstep(0.01, 0.02, sin(10.0 * a + iTime * 2.0) * 0.5 + 0.5);
        rays *= smoothstep(0.2, 0.0, abs(r - radius));
        color += outerColor * outerCircle;
        color += innerColor * innerCircle;
        color += rays * hoverIntensity;

        gl_FragColor = vec4(color, max(outerCircle, rays * 0.6));
      }
    `

    const renderer = new Renderer({ alpha: true, premultipliedAlpha: false })
    const gl = renderer.gl
    gl.clearColor(0, 0, 0, 0)
    container.appendChild(gl.canvas)

    const geometry = new Triangle(gl)
    const program = new Program(gl, {
      vertex: vert,
      fragment: frag,
      uniforms: {
        iTime: { value: 0 },
        iResolution: {
          value: new Vec3(
            gl.canvas.width,
            gl.canvas.height,
            gl.canvas.width / gl.canvas.height
          ),
        },
        hue: { value: this.hue },
        hover: { value: 0 },
        rot: { value: 0 },
        hoverIntensity: { value: this.hoverIntensity },
      }
    })

    const mesh = new Mesh(gl, { geometry, program })

    const resize = () => {
      const dpr = window.devicePixelRatio || 1
      const width = container.clientWidth
      const height = container.clientHeight
      renderer.setSize(width * dpr, height * dpr)
      gl.canvas.style.width = width + 'px'
      gl.canvas.style.height = height + 'px'
      program.uniforms.iResolution.value.set(
        gl.canvas.width,
        gl.canvas.height,
        gl.canvas.width / gl.canvas.height
      )
    }
    window.addEventListener('resize', resize)
    resize()

    let targetHover = 0
    let lastTime = 0
    let currentRot = 0
    const rotationSpeed = 0.3

    const handleMouseMove = (e) => {
      const rect = container.getBoundingClientRect()
      const x = e.clientX - rect.left
      const y = e.clientY - rect.top
      const width = rect.width
      const height = rect.height
      const size = Math.min(width, height)
      const centerX = width / 2
      const centerY = height / 2
      const uvX = ((x - centerX) / size) * 2.0
      const uvY = ((y - centerY) / size) * 2.0

      if (Math.sqrt(uvX * uvX + uvY * uvY) < 0.8) {
        targetHover = 1
      } else {
        targetHover = 0
      }
    }

    const handleMouseLeave = () => {
      targetHover = 0
    }

    container.addEventListener('mousemove', handleMouseMove)
    container.addEventListener('mouseleave', handleMouseLeave)

    let rafId
    const update = (t) => {
      rafId = requestAnimationFrame(update)
      const dt = (t - lastTime) * 0.001
      lastTime = t
      program.uniforms.iTime.value = t * 0.001
      program.uniforms.hue.value = this.hue
      program.uniforms.hoverIntensity.value = this.hoverIntensity

      const effectiveHover = this.forceHoverState ? 1 : targetHover
      program.uniforms.hover.value += (effectiveHover - program.uniforms.hover.value) * 0.1

      if (this.rotateOnHover && effectiveHover > 0.5) {
        currentRot += dt * rotationSpeed
      }
      program.uniforms.rot.value = currentRot

      renderer.render({ scene: mesh })
    }
    rafId = requestAnimationFrame(update)

    this.$once('hook:beforeDestroy', () => {
      cancelAnimationFrame(rafId)
      window.removeEventListener('resize', resize)
      container.removeEventListener('mousemove', handleMouseMove)
      container.removeEventListener('mouseleave', handleMouseLeave)
      container.removeChild(gl.canvas)
      gl.getExtension('WEBGL_lose_context')?.loseContext()
    })
  }
}
</script>
