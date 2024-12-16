<script>
    import emblaCarouselSvelte from 'embla-carousel-svelte';
    import Autoplay from "embla-carousel-autoplay";

    let emblaApi;
    let options = { loop: true };
    let plugins = [Autoplay({ delay: 3000, stopOnInteraction: false })];

    function onInit(event) {
        emblaApi = event.detail;
    }

    let Skill = {
        Laravel: {
            name: "Laravel",
            logo: "/logos/laravel.svg"
        },
        JavaScript: {
            name: "JavaScript",
            logo: "/logos/js.png"
        },
        Angular: {
            name: "Angular",
            logo: "/logos/angular.png"
        },
        React: {
            name: "React",
            logo: "/logos/react.svg"
        },
        Vue: {
            name: "Vue",
            logo: "/logos/vue.png"
        },
        Svelte: {
            name: "Svelte",
            logo: "/logos/svelte.png"
        },
        Typescript: {
            name: "Typescript",
            logo: "/logos/ts.png"
        },
        TailwindCSS: {
            name: "TailwindCSS",
            logo: "/logos/tailwind.svg"
        },
        Android: {
            name: "Android Development",
            logo: "/logos/android.png"
        },
        Flutter: {
            name: "Flutter",
            logo: "/logos/flutter.svg"
        },
        Rust: {
            name: "Rust",
            logo: "/logos/rust.svg"
        },
        Python: {
            name: "Python",
            logo: "/logos/python.png"
        },
        Bootstrap: {
            name: "Bootstrap",
            logo: "/logos/bootstrap.svg"
        },
        Firebase: {
            name: "Firebase",
            logo: "/logos/firebase.png"
        },
        Vite: {
            name: "Vite",
            logo: "/logos/vite.png"
        }
    }
</script>

<div class="embla overflow-hidden w-full max-w-md mx-auto" use:emblaCarouselSvelte="{{ options, plugins }}"
     on:emblaInit="{onInit}">
    <div class="embla__container flex">
        {#each Object.values(Skill) as {name, logo}}
            <div class="embla__slide flex-[0_0_50%] sm:flex-[0_0_33.33%] min-w-0 flex justify-center items-center p-4">
                <div class="flex flex-col items-center">
                    <img src="{logo}" alt="{name}" class="w-16 h-16 sm:w-20 sm:h-20 md:w-24 md:h-24 object-contain"/>
                    <p class="text-center text-sm sm:text-base md:text-lg font-light mt-2">{name}</p>
                </div>
            </div>
        {/each}
    </div>
</div>

<style>
    .embla__slide {
        flex: 0 0 50%;
    }

    @media (min-width: 640px) {
        .embla__slide {
            flex: 0 0 33.33%;
        }
    }
</style>

