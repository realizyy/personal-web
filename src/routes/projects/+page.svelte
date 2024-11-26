<script>
    const projects = [
        {
            title: 'Dkampus',
            description: 'Dkampus is a platform food delivery service for students in Local University.',
            image: 'https://placehold.co/600x400/png',
            tags: ['Laravel', 'Node.js', 'Firebase'],
        },
        {
            title: 'Dkampus V.2',
            description: 'Remake of Dkampus with new features and better performance.',
            image: 'https://placehold.co/600x400/png',
            tags: ['Svelte', 'Node.js', 'Typescript'],
        },
        {
            title: 'Unit3C',
            description: 'Unit3C is a platform for sertificate computing course for my university.',
            image: 'https://placehold.co/600x400/png',
            tags: ['HTML', 'CSS'],
        },
        {
            title: 'Event website for XYZ Company',
            description: 'A website for XYZ Company to promote their event.',
            image: 'https://placehold.co/600x400/png',
            tags: ['Laravel', 'Tailwind', 'Node.js'],
        },
        {
            title: 'Dashboard Banker for XYZ Company',
            description: 'A dashboard for XYZ Company to manage their customer data and transaction.',
            image: 'https://placehold.co/600x400/png',
            tags: ['Vue.js', 'Node.js', 'Express'],
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

