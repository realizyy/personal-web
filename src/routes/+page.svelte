<script>
    import { onMount } from "svelte";
    import Carousel from "$lib/components/Carousel/Carousel.svelte";
    onMount(() => {
        console.log("Hello There~");
    });
</script>

<div class="col self-center flex-1 md:flex-row md:slef-stretch justify-center lg:justify-between items-center p-y-0px p-x-10px">
    <div class="md:flex-1">
        <h1 class="font-black tracking-[4px] text-center text-2.5em sm:text-[3em] md:text-[3.5em] lg:text-[4em] md:text-left">
            Realizy,
        </h1>
        <p class="text-center md:text-left text-[1.2em] font-extralight">
            Hello, It's me Muhammad Real Andri Faqih, a Neubbs Software Engineer.
        </p>
        <div class="flex justify-center md:justify-start py-2 px-0 gap-3">
            <a class="decoration-none" href="#" target="_blank" rel="noreferrer">
                <svg class="inline-block" viewBox="0 0 16 16" fill="#FFFFFF" height="20px" width="20px">
                    <path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"></path>
                </svg>
            </a>
            <a class="decoration-none" href="#" target="_blank" rel="noreferrer">
                <svg class="inline-block" viewBox="0 0 24 24" fill="#FFFFFF" height="20px" width="20px">
                    <path d="M20.5 2h-17A1.5 1.5 0 002 3.5v17A1.5 1.5 0 003.5 22h17a1.5 1.5 0 001.5-1.5v-17A1.5 1.5 0 0020.5 2zM8 19H5v-9h3zM6.5 8.25A1.75 1.75 0 118.3 6.5a1.78 1.78 0 01-1.8 1.75zM19 19h-3v-4.74c0-1.42-.6-1.93-1.38-1.93A1.74 1.74 0 0013 14.19a.66.66 0 000 .14V19h-3v-9h2.9v1.3a3.11 3.11 0 012.7-1.4c1.55 0 3.36.86 3.36 3.66z"></path>
                </svg>
            </a>
            <a class="decoration-none" href="#" target="_blank" rel="noreferrer">
                <svg class="inline-block" viewBox="0 0 24 24" fill="#FFFFFF" height="20px" width="20px">
                    <path d="m17.12 21.857h-14.977v-6.428h-2.143v8.571h19.259v-8.571h-2.139zm-12.616-7.018.442-2.102 10.486 2.21-.442 2.09zm1.379-5.009.898-1.955 9.71 4.54-.898 1.942zm2.692-4.768 1.366-1.647 8.218 6.87-1.366 1.647zm5.313-5.062 6.388 8.585-1.716 1.286-6.386-8.585zm-9.616 19.701v-2.13h10.714v2.13z"></path>
                </svg>
            </a>
            <a class="decoration-none" href="#" target="_blank" rel="noreferrer">
                <svg class="inline-block" viewBox="0 0 24 24" fill="#FFFFFF" height="20px" width="20px">
                    <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10h5v-2h-5c-4.34 0-8-3.66-8-8s3.66-8 8-8 8 3.66 8 8v1.43c0 .79-.71 1.57-1.5 1.57s-1.5-.78-1.5-1.57V12c0-2.76-2.24-5-5-5s-5 2.24-5 5 2.24 5 5 5c1.38 0 2.64-.56 3.54-1.47.65.89 1.77 1.47 2.96 1.47 1.97 0 3.5-1.6 3.5-3.57V12c0-5.52-4.48-10-10-10zm0 13c-1.66 0-3-1.34-3-3s1.34-3 3-3 3 1.34 3 3-1.34 3-3 3z"></path>
                </svg>
            </a>
        </div>
    </div>
    <div class="flex justify-center md:justify-start">
        <Carousel />
    </div>
</div>
