<script>
  let filters = [
    'Protanopia', 'Tritanopia',
    'Deuteranopia', 'Achromatopsia',
    'Protanomaly', 'Tritanomaly',
    'Deuteranomaly', 'Achromatomaly'
  ];

  const filterMatrices = {
    normal: {
      R: [1, 0, 0],
      G: [0, 1, 0],
      B: [0, 0, 1]
    },
    Protanopia: {
      R: [0.56667, 0.43333, 0],
      G: [0.55833, 0.44167, 0],
      B: [0, 0.24167, 0.75833]
    },
    Protanomaly: {
      R: [0.81667, 0.18333, 0],
      G: [0.33333, 0.66667, 0],
      B: [0, 0.125, 0.875]
    },
    Deuteranopia: {
      R: [0.625, 0.375, 0],
      G: [0.7, 0.3, 0],
      B: [0, 0.3, 0.7]
    },
    Deuteranomaly: {
      R: [0.8, 0.2, 0],
      G: [0.25833, 0.74167, 0],
      B: [0, 0.14167, 0.85833]
    },
    Tritanopia: {
      R: [0.95, 0.05, 0],
      G: [0, 0.43333, 0.56667],
      B: [0, 0.475, 0.525]
    },
    Tritanomaly: {
      R: [0.96667, 0.03333, 0],
      G: [0, 0.73333, 0.26667],
      B: [0, 0.18333, 0.81667]
    },
    Achromatopsia: {
      R: [0.299, 0.587, 0.114],
      G: [0.299, 0.587, 0.114],
      B: [0.299, 0.587, 0.114]
    },
    Achromatomaly: {
      R: [0.618, 0.32, 0.062],
      G: [0.163, 0.775, 0.062],
      B: [0.163, 0.32, 0.516]
    },
    Sepia: {
      R: [0.393, 0.769, 0.189],
      G: [0.349, 0.686, 0.168],
      B: [0.272, 0.534, 0.131]
    },
    Invert: {
      R: [-1, 0, 255],
      G: [0, -1, 255],
      B: [0, 0, -1]
    },
    Brightness: {
      R: [1.5, 0, 0],
      G: [0, 1.5, 0],
      B: [0, 0, 1.5]
    },
    Contrast: {
      R: [1.5, 0, -128 * 0.5],
      G: [0, 1.5, -128 * 0.5],
      B: [0, 0, 1.5]
    }
  };
  function drawOriginalImage() {
    const img = new Image();
    img.src = imageUrl;
    img.onload = () => {
      canvasOriginal.width = img.width;
      canvasOriginal.height = img.height;
      ctxOriginal.drawImage(img, 0, 0);
    };
  }

  function applyFilter(filter) {
    drawFilteredImage(filter);
  }
</script>
<div class="card gap-16 items-center mx-auto max-w-screen-xl lg:grid lg:grid-cols-2 overflow-hidden rounded-lg p-8 bg-gray-50 dark:bg-gray-900">
  
</div>

<style>
  
</style>