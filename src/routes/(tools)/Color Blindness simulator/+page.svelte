<script>
  
	let imageUrl = '';
	let imageFile;
	let fileName = '';
	let canvasOriginal;
	let ctxOriginal;
	let canvasFiltered;
	let ctxFiltered;
	let filters = [
	  'Protanopia', 'Tritanopia',
	  'Deuteranopia', 'Achromatopsia',
	  'Protanomaly', 'Tritanomaly',
	  'Deuteranomaly', 'Achromatomaly'
	];
  

  
	function drawFilteredImage(filter) {
	  const img = new Image();
	  img.src = imageUrl;
	  img.onload = () => {
		canvasFiltered.width = img.width;
		canvasFiltered.height = img.height;
		ctxFiltered.clearRect(0, 0, canvasFiltered.width, canvasFiltered.height);
		ctxFiltered.drawImage(img, 0, 0);
		
		const imageData = ctxFiltered.getImageData(0, 0, canvasFiltered.width, canvasFiltered.height);
		const data = imageData.data;
		const matrix = filterMatrices[filter];
	
		for (let i = 0; i < data.length; i += 4) {
		  const r = data[i];
		  const g = data[i + 1];
		  const b = data[i + 2];
		  data[i] = r * matrix.R[0] + g * matrix.R[1] + b * matrix.R[2];
		  data[i + 1] = r * matrix.G[0] + g * matrix.G[1] + b * matrix.G[2];
		  data[i + 2] = r * matrix.B[0] + g * matrix.B[1] + b * matrix.B[2];
		}
  
		ctxFiltered.putImageData(imageData, 0, 0);
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