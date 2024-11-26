<script>
    import { onMount } from 'svelte';
    import { fade } from 'svelte/transition';

    const skills = [
        { name: 'HTML', level: 95 },
        { name: 'CSS', level: 90 },
        { name: 'JavaScript', level: 90 },
        { name: 'PHP', level: 90},
        { name: 'Java' , level: 80},
        { name: 'React', level: 85 },
        { name: 'Svelte', level: 70 },
        { name: 'Flutter', level: 60 },
        { name: 'Node.js', level: 75 },
        { name: 'Python', level: 80 },
        { name: 'Django', level: 75 },
        { name: 'Laravel', level: 90 },
        { name: 'Express', level: 75 },
        { name: 'MongoDB', level: 70 },
        { name: 'MySQL', level: 75 },
        { name: 'LUA', level: 80 },
        { name: 'C++', level: 70 },
        { name: 'C#', level: 70}
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

