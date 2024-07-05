<div class="card gap-16 items-center mx-auto max-w-screen-xl lg:grid lg:grid-cols-2 overflow-hidden rounded-lg p-8 bg-gray-50 dark:bg-gray-900">
	<div class="bg-gray-50 dark:bg-gray-900 p-4 mb-4 text-white flex items-center space-x-4 w-full justify-center lg:col-span-2">
		<input type="file" id="fileInput" accept="image/*" on:change={handleImageUpload} class="hidden" />
		<button class="bg-white dark:bg-gray-800 dark:text-white text-black py-2 px-4 border border-gray-200 dark:border-gray-700 rounded" on:click={() => document.getElementById('fileInput').click()}>Upload Image</button>
		<span>{fileName}</span>
	  </div>
	
	  <div class="canvas-container">
		<h2 class="text-xl font-semibold mb-2 text-gray-900 dark:text-gray-200">Original Image</h2>
		<canvas id="canvasOriginal" class="border border-gray-900 rounded dark:border-gray-300" width="500" height="500"></canvas>
	  </div>
	
	  <div class="canvas-container">
		<h2 class="text-xl font-semibold mb-2 text-gray-900 dark:text-gray-200">Filtered Image</h2>
		<canvas id="canvasFiltered" class="border border-gray-900 rounded dark:border-gray-300" width="500" height="500"></canvas>
	  </div>
	
	  <div class="buttons lg:col-span-2 mt-6">
		{#each filters as filter}
		  <button class="px-2 py-4 font-normal text-black dark:text-white bg-white dark:bg-gray-800 cursor-pointer border border-gray-200 dark:border-gray-700 rounded" on:click={() => applyFilter(filter)}>{filter}</button>
		{/each}
	  </div>
  </div>
  
  <style>
	.buttons {
	  display: grid;
	  grid-template-columns: repeat(4, 1fr);
	  gap: 10px;
	  justify-content: center;
	}
	.canvas-container {
	  width: 100%;
	  display: flex;
	  flex-direction: column;
	  align-items: center;
	}
	canvas {
	  border: 1px solid gray;
	  max-width: 100%;
	  max-height: 100%;
	}
  </style>