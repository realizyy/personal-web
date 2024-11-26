<script>
    const projects = [
        {
            title: 'Project 1',
            description: 'A brief description of Project 1',
            image: 'https://placehold.co/600x400/png',
            tags: ['React', 'Node.js', 'MongoDB'],
        },
        {
            title: 'Project 2',
            description: 'A brief description of Project 2',
            image: 'https://placehold.co/600x400/png',
            tags: ['Svelte', 'Firebase', 'Tailwind CSS'],
        },
        {
            title: 'Project 3',
            description: 'A brief description of Project 3',
            image: 'https://placehold.co/600x400/png',
            tags: ['Vue.js', 'Express', 'PostgreSQL'],
        },
    ];
</script>

<div class="container mx-auto min-h-screen px-4 py-8">
    <h1 class="text-4xl font-bold mb-8 text-center">Projects</h1>
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
        {#each projects as project}
            <div class="card bg-base-100 shadow-xl">
                <figure><img src={project.image} alt={project.title} /></figure>
                <div class="card-body">
                    <h2 class="card-title">{project.title}</h2>
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

