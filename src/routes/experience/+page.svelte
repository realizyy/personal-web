<script>
    const experiences = [
        {
            company: 'Tech Corp',
            position: 'Senior Developer',
            period: 'Jan 2020 - Present',
            description: 'Led a team of developers in creating innovative web applications.',
        },
        {
            company: 'Web Solutions Inc.',
            position: 'Full Stack Developer',
            period: 'Mar 2017 - Dec 2019',
            description: 'Developed and maintained various client projects using modern web technologies.',
        },
        {
            company: 'StartUp XYZ',
            position: 'Junior Developer',
            period: 'Jun 2015 - Feb 2017',
            description: 'Assisted in the development of the company\'s main product and gained valuable experience.',
        },
    ];
</script>

<div class="container mx-auto px-4 py-8">
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

