<script>
    let name = '';
    let email = '';
    let message = '';

    function handleSubmit() {
        // Handle form submission logic here
        console.log('Form submitted:', { name, email, message });
        // Reset form fields
        name = '';
        email = '';
        message = '';
    }
</script>

<div class="container mx-auto min-h-screen px-4 py-8">
    <h1 class="text-4xl font-bold mb-8 text-center">Contact</h1>
    <div class="card bg-base-100 shadow-xl max-w-lg mx-auto">
        <div class="card-body">
            <form on:submit|preventDefault={handleSubmit}>
                <div class="form-control">
                    <label class="label" for="name">
                        <span class="label-text">Name</span>
                    </label>
                    <input type="text" id="name" bind:value={name} placeholder="Your name" class="input input-bordered" required />
                </div>
                <div class="form-control mt-4">
                    <label class="label" for="email">
                        <span class="label-text">Email</span>
                    </label>
                    <input type="email" id="email" bind:value={email} placeholder="Your email" class="input input-bordered" required />
                </div>
                <div class="form-control mt-4">
                    <label class="label" for="message">
                        <span class="label-text">Message</span>
                    </label>
                    <textarea id="message" bind:value={message} placeholder="Your message" class="textarea textarea-bordered h-24" required></textarea>
                </div>
                <div class="form-control mt-6">
                    <button type="submit" class="btn btn-primary">Send Message</button>
                </div>
            </form>
        </div>
    </div>
</div>

