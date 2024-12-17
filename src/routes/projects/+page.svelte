<script>
    import { onMount } from 'svelte';
    import ProjectCarousel from '$lib/components/Carousel/ProjectCarousel.svelte';

    let lightboxOpen = false;
    let currentProject = null;
    let currentImageIndex = 0;

    const projects = [
        {
            title: 'Dkampus',
            description: 'Dkampus is a platform food delivery service for students in Local University.',
            images: ['https://realizy.my.id/DK-1.png', 'https://realizy.my.id/DK-2.png', 'https://realizy.my.id/DK-3.png', "https://realizy.my.id/DK-4.png", "https://realizy.my.id/DK-5.png", "https://realizy.my.id/DK-6.png", "https://realizy.my.id/DK-7.png"],
            tags: ['Laravel', 'Node.js', 'Firebase'],
            private: [
                {
                    Repository: 'https://www.github.com/Dkampus/DKampus-Laravel',
                },
            ],
        },
        {
            title: 'Dkampus V.2',
            description: 'Ongoing to remake of Dkampus with new features and framework.',
            images: ['https://realizy.my.id/DKSV-1.png', 'https://realizy.my.id/DKSV-2.png', 'https://realizy.my.id/DKSV-3.png'],
            tags: ['Svelte', 'Node.js', 'Typescript'],
        },
        {
            title: 'Unit3C',
            description: 'Unit3C is a platform for sertificate computing course for my university.',
            images: ['https://realizy.my.id/U3C-1.png'],
            tags: ['HTML', 'CSS'],
        },
        {
            title: 'Event website for XYZ Company',
            description: 'A website for XYZ Company to promote their event.',
            images: ['https://realizy.my.id/PSR-1.png', 'https://realizy.my.id/PSR-2.png'],
            tags: ['Laravel', 'Tailwind', 'Node.js'],
        },
        {
            title: 'Dashboard Banker for XYZ Company',
            description: 'A dashboard for XYZ Company to manage their customer data and transaction.',
            images: ['https://realizy.my.id/BC-1.png'],
            tags: ['Vue.js', 'Node.js', 'Express'],
        },
    ];

    function openLightbox(project, index) {
        currentProject = project;
        currentImageIndex = index;
        lightboxOpen = true;
        document.body.style.overflow = 'hidden';
    }

    function closeLightbox() {
        lightboxOpen = false;
        document.body.style.overflow = 'auto';
    }

    function nextImage() {
        currentImageIndex = (currentImageIndex + 1) % currentProject.images.length;
    }

    function prevImage() {
        currentImageIndex = (currentImageIndex - 1 + currentProject.images.length) % currentProject.images.length;
    }

    onMount(() => {
        const handleKeydown = (e) => {
            if (lightboxOpen) {
                if (e.key === 'Escape') closeLightbox();
                if (e.key === 'ArrowRight') nextImage();
                if (e.key === 'ArrowLeft') prevImage();
            }
        };

        window.addEventListener('keydown', handleKeydown);

        return () => {
            window.removeEventListener('keydown', handleKeydown);
        };
    });
</script>

<div class="container mx-auto min-h-screen px-4 py-8">
    <h1 class="text-4xl font-bold mb-8 text-center">Projects</h1>
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
        {#each projects as project}
            <div class="card bg-base-100 shadow-xl">
                <figure class="cursor-pointer" on:click={() => openLightbox(project, 0)}>
                    <ProjectCarousel images={project.images} title={project.title} />
                </figure>
                <div class="card-body">
                    <h2 class="card-title">{project.title}
                        {#if project.private}
                            <a class="hover:opacity-80 transition-opacity" href="{project.private[0].Repository}" target="_blank" rel="noreferrer">
                                <svg viewBox="0 0 16 16" fill="currentColor" class="w-5 h-5 sm:w-5 sm:h-5">
                                    <path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"></path>
                                </svg>
                            </a>
                        {/if}
                    </h2>
                    <p>{project.description}</p>
                    <div class="card-actions justify-end">
                        {#each project.tags as tag}
                            <div class="badge badge-outline">{tag}</div>
                        {/each}
                    </div>
                </div>
            </div>
        {/each}
    </div>
</div>

{#if lightboxOpen}
    <div class="fixed inset-0 bg-black bg-opacity-75 z-50 flex items-center justify-center" on:click={closeLightbox}>
        <div class="relative max-w-4xl w-full h-full flex items-center justify-center" on:click|stopPropagation>
            <img
                    src={currentProject.images[currentImageIndex]}
                    alt={`${currentProject.title} - Image ${currentImageIndex + 1}`}
                    class="max-w-full max-h-full object-contain"
            />
            <button class="absolute top-4 right-4 text-white text-2xl" on:click={closeLightbox}>&times;</button>
            <button class="absolute left-4 top-1/2 transform -translate-y-1/2 text-white text-4xl" on:click={prevImage}>&lt;</button>
            <button class="absolute right-4 top-1/2 transform -translate-y-1/2 text-white text-4xl" on:click={nextImage}>&gt;</button>
            <div class="absolute bottom-4 left-1/2 transform -translate-x-1/2 text-white">
                {currentImageIndex + 1} / {currentProject.images.length}
            </div>
        </div>
    </div>
{/if}
