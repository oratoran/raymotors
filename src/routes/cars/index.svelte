<script context="module">
  const cars = import.meta.glob('./*.svx')

  let body = []

  for (const path in cars) {
    body.push(cars[path]().then(({metadata}) => metadata))
  }
  /**
    * @type {import('@sveltejs/kit').Load}
    */
  export async function load({ page, fetch }) {
    const cars = await Promise.all(body)
    return {
      props: {
        cars
      }
    };
  }
</script>

<script>
  // import Slider from '$lib/Slider/index.svelte'
  // import Example from '$lib/Example.svelte.md'
  import Tag from "$lib/Tag.svelte";
  export let cars;
</script>

<svelte:head>
<title>Ray Motors Klasik Araçlar</title>
</svelte:head>

<h1 class="text-4xl text-center">Ray Motors Klasik Araçlar</h1>
<p class="text-center">Klasik araçlarımızın tüm listesi aşağıdadır. İlgilendiğiniz araç için teklifte bulunabilirsiniz.</p>

<ul class="list-none sm:flex sm:flex-wrap xl:w-5/6 mx-auto ">
  {#each cars as {title, image, tags, outline, slug}}
  <li class=" list-none w-full sm:w-1/2 md:w-1/3">
    <a
      class="space-y-3 text-gray-50"
      rel="prefetch"
      href="cars/{slug}"
    >
    <div class="p-4 bg-gray-800 rounded shadow-md m-4 ">
      <img src="/images/cars/{image}" alt="{title}" class="w-auto rounded">
      <div class="h-48">
          <p class="text-sm font-normal text-gray-500">
              Tags: {#each tags as tag}
              <Tag { tag }/>
              {/each}
          </p>
              <h2>
              {title}
              </h2>
              <p class="text-base sm:text-sm ">
                  {outline}
              </p>
          </div>
      </div>
    
    

      
    </a>
  </li>
  {/each}
</ul>