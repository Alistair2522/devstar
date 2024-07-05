<script>
    import { onMount } from 'svelte';
  
  
    onMount(() => {
      canvasOriginal = document.getElementById('canvasOriginal');
      ctxOriginal = canvasOriginal.getContext('2d');
      canvasFiltered = document.getElementById('canvasFiltered');
      ctxFiltered = canvasFiltered.getContext('2d');
    });
  
    function handleImageUpload(event) {
      const file = event.target.files[0];
      if (file) {
        imageFile = file;
        fileName = file.name;
        const reader = new FileReader();
        reader.onload = (e) => {
          imageUrl = e.target.result;
          drawOriginalImage();
          drawFilteredImage('normal');
        };
        reader.readAsDataURL(file);
      }
    }


    function saveImage() {
      const link = document.createElement('a');
      link.download = 'filtered_image.png';
      link.href = canvasFiltered.toDataURL();
      link.click();
    }
    
    function shareOnSocialMedia(platform) {
    switch (platform) {
    case 'facebook':
      const facebookUrl = `https://www.facebook.com/sharer/`;
      window.open(facebookUrl, '_blank');
      break;
    case 'instagram':
      const instagramUrl = `https://www.instagram.com/`;
      window.open(instagramUrl, '_blank');
      break;
    case 'twitter':
      const twitterUrl = `https://twitter.com/intent/tweet`;
      window.open(twitterUrl, '_blank');
      break;
    default:
      console.error(`Unknown platform: ${platform}`);
  }
}


  </script>
  <div class="card gap-16 items-center mx-auto max-w-screen-xl lg:grid lg:grid-cols-2 overflow-hidden rounded-lg p-8 bg-gray-50 dark:bg-gray-900">
      <div class="buttons lg:col-span-2 mt-6">
        {#each filters as filter}
          <button class="px-2 py-4 font-normal text-black dark:text-white bg-white dark:bg-gray-800 cursor-pointer border border-gray-200 dark:border-gray-700 rounded" on:click={() => applyFilter(filter)}>{filter}</button>
        {/each}
  
        <button class="px-2 py-4 font-normal text-black dark:text-white bg-white dark:bg-gray-800 cursor-pointer border border-gray-200 dark:border-gray-700 rounded" on:click={saveImage}>Save Image</button>
        <button class="px-2 py-4 font-normal text-black dark:text-white bg-white dark:bg-gray-800 cursor-pointer border border-gray-200 dark:border-gray-700 rounded" on:click={() => shareOnSocialMedia('facebook')}>Share on Facebook</button>
        <button class="px-2 py-4 font-normal text-black dark:text-white bg-white dark:bg-gray-800 cursor-pointer border border-gray-200 dark:border-gray-700 rounded" on:click={() => shareOnSocialMedia('twitter')}>Share on Twitter</button>
        <button class="px-2 py-4 font-normal text-black dark:text-white bg-white dark:bg-gray-800 cursor-pointer border border-gray-200 dark:border-gray-700 rounded" on:click={() => shareOnSocialMedia('instagram')}>Share on Instagram</button>
      </div>

      <div class="loading-indicator" id="loading-indicator" style="display: none;">
        <svg viewBox="25 25 50 50">
          <circle cx="50" cy="50" r="20" fill="none" stroke-width="2" stroke-miterlimit="10" />
        </svg>
      </div>
  </div>
  
  <style>
    
  </style>