<script>
    const experiences = [
        {
            company: 'Dcreativ Indonesia',
            position: 'Frontend Web Developer',
            period: 'Oct 2023 - Sep 2024',
            description: 'Developing and maintaining the company\'s website and web application.',
        },
        {
            company: 'VML | Wunderman Thompson Indonesia',
            position: 'Web Developer',
            period: 'Sep 2023 - Dec 2023',
            description: 'Assisted in the development of the company\'s main product and gained valuable experience.',
        },
    ];
</script>

<div class="container mx-auto min-h-screen px-4 py-8">
    <h1 class="text-4xl font-bold mb-8 text-center">Experience</h1>
    <div class="space-y-6">
        {#each experiences as exp}
            <div class="card bg-base-100 shadow-xl">
                <div class="card-body">
                    <h2 class="card-title">{exp.position}</h2>
                    <h3 class="text-lg font-semibold">{exp.company}</h3>
                    <p class="text-sm text-base-content text-opacity-60">{exp.period}</p>
                    <p>{exp.description}</p>
                </div>
            </div>
        {/each}
    </div>
</div>

