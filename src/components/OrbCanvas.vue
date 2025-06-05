<template>
  <canvas ref="canvasRef" class="w-full h-full"></canvas>
</template>

<script setup>
import { onMounted, ref } from 'vue'
// eslint-disable-next-line no-undef
const props = defineProps({
  hue: { type: Number, default: 0 },
  hoverIntensity: { type: Number, default: 0.5 },
})

const canvasRef = ref(null)

onMounted(() => {
  const canvas = canvasRef.value
  if (!canvas) return
  const gl = canvas.getContext('webgl')
  if (!gl) return

  canvas.width = canvas.offsetWidth
  canvas.height = canvas.offsetHeight

  const vertexShaderSource = `
    precision mediump float;
    attribute vec2 position;
    void main() {
      gl_Position = vec4(position, 0, 1);
    }
  `
  const fragmentShaderSource = `
    precision mediump float;
    uniform float uTime;
    uniform vec2 uMouse;
    uniform float uHue;
    uniform float uIntensity;

    float rand(vec2 co){
      return fract(sin(dot(co.xy, vec2(12.9898,78.233))) * 43758.5453);
    }

    void main() {
      vec2 uv = gl_FragCoord.xy / vec2(${canvas.width.toFixed(1)}, ${canvas.height.toFixed(1)});
      vec2 dist = uMouse - uv;
      float d = length(dist);
      float brightness = 0.1 / d * uIntensity;

      vec3 color = vec3(0.5 + 0.5 * sin(uTime + uHue * 6.2831 + uv.xyx + vec3(0, 2, 4)));
      color *= brightness;
      gl_FragColor = vec4(color, 1.0);
    }
  `

  function compileShader(type, source) {
    const shader = gl.createShader(type)
    gl.shaderSource(shader, source)
    gl.compileShader(shader)
    if (!gl.getShaderParameter(shader, gl.COMPILE_STATUS)) {
      console.error(gl.getShaderInfoLog(shader))
    }
    return shader
  }

  const vertexShader = compileShader(gl.VERTEX_SHADER, vertexShaderSource)
  const fragmentShader = compileShader(gl.FRAGMENT_SHADER, fragmentShaderSource)

  const program = gl.createProgram()
  gl.attachShader(program, vertexShader)
  gl.attachShader(program, fragmentShader)
  gl.linkProgram(program)
  gl.useProgram(program)

  const vertices = new Float32Array([
    -1, -1,
     1, -1,
    -1,  1,
     1,  1
  ])

  const buffer = gl.createBuffer()
  gl.bindBuffer(gl.ARRAY_BUFFER, buffer)
  gl.bufferData(gl.ARRAY_BUFFER, vertices, gl.STATIC_DRAW)

  const positionLocation = gl.getAttribLocation(program, 'position')
  gl.enableVertexAttribArray(positionLocation)
  gl.vertexAttribPointer(positionLocation, 2, gl.FLOAT, false, 0, 0)

  const timeLoc = gl.getUniformLocation(program, 'uTime')
  const mouseLoc = gl.getUniformLocation(program, 'uMouse')
  const hueLoc = gl.getUniformLocation(program, 'uHue')
  const intensityLoc = gl.getUniformLocation(program, 'uIntensity')

  let startTime = Date.now()
  let mouse = [0.5, 0.5]

  canvas.addEventListener('mousemove', (e) => {
    const rect = canvas.getBoundingClientRect()
    mouse = [
      (e.clientX - rect.left) / rect.width,
      1.0 - (e.clientY - rect.top) / rect.height
    ]
  })

  function render() {
    const time = (Date.now() - startTime) / 1000
    gl.uniform1f(timeLoc, time)
    gl.uniform2fv(mouseLoc, mouse)
    gl.uniform1f(hueLoc, props.hue)
    gl.uniform1f(intensityLoc, props.hoverIntensity)

    gl.drawArrays(gl.TRIANGLE_STRIP, 0, 4)
    requestAnimationFrame(render)
  }

  render()
})
</script>
