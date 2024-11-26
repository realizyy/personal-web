<script>
    import { onMount } from 'svelte';
    import { fade } from 'svelte/transition';

    const skills = [
        { name: 'JavaScript', level: 90 },
        { name: 'React', level: 85 },
        { name: 'Svelte', level: 80 },
        { name: 'Node.js', level: 75 },
        { name: 'Python', level: 70 },
        { name: 'SQL', level: 65 },
    ];

    let visible = false;

    onMount(() => {
        visible = true;
    });
</script>

<div class="container mx-auto min-h-screen px-4 py-8">
    <h1 class="text-4xl font-bold mb-8 text-center">Skills</h1>
    <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
        {#each skills as skill}
            {#if visible}
                <div class="card bg-base-100 shadow-xl" transition:fade="{{ duration: 300 }}">
                    <div class="card-body">
                        <h2 class="card-title">{skill.name}</h2>
                        <progress class="progress progress-primary w-full" value={skill.level} max="100"></progress>
                        <p class="text-right">{skill.level}%</p>
                    </div>
                </div>
            {/if}
        {/each}
    </div>
</div>

