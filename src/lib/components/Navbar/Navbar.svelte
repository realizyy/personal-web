<script>
    import { onMount } from 'svelte';
    let isOpen = false;

    function toggleMenu() {
        isOpen = !isOpen;
    }

    let randomRomanNumber = '';

    function toRoman(num) {
        const romanNumerals = [
            { value: 1000, numeral: 'M' },
            { value: 900, numeral: 'CM' },
            { value: 500, numeral: 'D' },
            { value: 400, numeral: 'CD' },
            { value: 100, numeral: 'C' },
            { value: 90, numeral: 'XC' },
            { value: 50, numeral: 'L' },
            { value: 40, numeral: 'XL' },
            { value: 10, numeral: 'X' },
            { value: 9, numeral: 'IX' },
            { value: 5, numeral: 'V' },
            { value: 4, numeral: 'IV' },
            { value: 1, numeral: 'I' }
        ];
        let result = '';
        for (const { value, numeral } of romanNumerals) {
            while (num >= value) {
                result += numeral;
                num -= value;
            }
        }
        return result;
    }

    function getRandomNumber(min, max) {
        return Math.floor(Math.random() * (max - min + 1)) + min;
    }

    function typeEffect(text, callback) {
        let i = 0;
        function typing() {
            if (i < text.length) {
                randomRomanNumber += text.charAt(i);
                i++;
                setTimeout(typing, 100);
            } else {
                callback();
            }
        }
        randomRomanNumber = '';
        typing();
    }

    onMount(() => {
        const updateRandomRomanNumber = () => {
            const newRomanNumber = toRoman(getRandomNumber(1, 100));
            typeEffect(newRomanNumber, () => {});
        };

        updateRandomRomanNumber();
        const interval = setInterval(updateRandomRomanNumber, 3000);

        const handleResize = () => {
            if (window.innerWidth >= 1024) {
                isOpen = false;
            }
        };

        window.addEventListener('resize', handleResize);

        return () => {
            clearInterval(interval);
            window.removeEventListener('resize', handleResize);
        };
    });
</script>

<nav class="bg-base-300 shadow-lg rounded-b-xl">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex items-center justify-between h-16">
            <div class="flex items-center">
                <!-- Glitch Random Text -->
                <div class="glitch-container">
                    <h1 class="glitch" data-text={randomRomanNumber}>{randomRomanNumber}</h1>
                </div>
            </div>
            <div class="hidden lg:block">
                <div class="ml-10 flex items-baseline space-x-4">
                    <a href="/" class="text-base-content hover:bg-base-200 hover:text-primary px-3 py-2 rounded-md">Home</a>
                    <a href="/skills" class="text-base-content hover:bg-base-200 hover:text-primary px-3 py-2 rounded-md">Skills</a>
                    <a href="/projects" class="text-base-content hover:bg-base-200 hover:text-primary px-3 py-2 rounded-md">Projects</a>
                    <a href="/experience" class="text-base-content hover:bg-base-200 hover:text-primary px-3 py-2 rounded-md">Experience</a>
                    <a href="/education" class="text-base-content hover:bg-base-200 hover:text-primary px-3 py-2 rounded-md">Education</a>
                    <a href="/contact" class="text-base-content hover:bg-base-200 hover:text-primary px-3 py-2 rounded-md">Contact</a>
                </div>
            </div>
            <div class="lg:hidden">
                <button on:click={toggleMenu} class="inline-flex items-center justify-center p-2 rounded-md text-base-content hover:text-primary hover:bg-base-200 focus:outline-none focus:ring-2 focus:ring-inset focus:ring-white" aria-expanded="false">
                    <span class="sr-only">Open main menu</span>
                    <svg class="h-6 w-6" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" aria-hidden="true">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
                    </svg>
                </button>
            </div>
        </div>
    </div>

    {#if isOpen}
        <div class="lg:hidden">
            <div class="px-2 pt-2 pb-3 space-y-1 sm:px-3">
                <a href="/" class="text-base-content hover:bg-base-200 hover:text-primary block px-3 py-2 rounded-md text-base font-medium">Home</a>
                <a href="/skills" class="text-base-content hover:bg-base-200 hover:text-primary block px-3 py-2 rounded-md text-base font-medium">Skills</a>
                <a href="/projects" class="text-base-content hover:bg-base-200 hover:text-primary block px-3 py-2 rounded-md text-base font-medium">Projects</a>
                <a href="/experience" class="text-base-content hover:bg-base-200 hover:text-primary block px-3 py-2 rounded-md text-base font-medium">Experience</a>
                <a href="/education" class="text-base-content hover:bg-base-200 hover:text-primary block px-3 py-2 rounded-md text-base font-medium">Education</a>
                <a href="/contact" class="text-base-content hover:bg-base-200 hover:text-primary block px-3 py-2 rounded-md text-base font-medium">Contact</a>
            </div>
        </div>
    {/if}
</nav>

<style>
    .glitch-container {
        display: inline-block;
        font-family: 'Arial', sans-serif;
        line-height: 1;
    }

    .glitch {
        color: currentColor;
        font-size: inherit;
        font-weight: bold;
        text-transform: uppercase;
        position: relative;
        display: inline-block;
    }

    .glitch::before,
    .glitch::after {
        content: attr(data-text);
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
    }

    .glitch::before {
        left: 2px;
        text-shadow: -2px 0 #ff00c1;
        clip: rect(44px, 450px, 56px, 0);
        animation: glitch-anim 5s infinite linear alternate-reverse;
    }

    .glitch::after {
        left: -2px;
        text-shadow: -2px 0 #00fff9, 2px 2px #ff00c1;
        animation: glitch-anim2 1s infinite linear alternate-reverse;
    }

    @keyframes glitch-anim {
        0% {
            clip: rect(31px, 9999px, 94px, 0);
            transform: skew(0.85deg);
        }
        5% {
            clip: rect(70px, 9999px, 71px, 0);
            transform: skew(0.85deg);
        }
        10% {
            clip: rect(21px, 9999px, 45px, 0);
            transform: skew(0.16deg);
        }
        15% {
            clip: rect(95px, 9999px, 6px, 0);
            transform: skew(0.48deg);
        }
        20% {
            clip: rect(54px, 9999px, 64px, 0);
            transform: skew(0.05deg);
        }
        25% {
            clip: rect(89px, 9999px, 87px, 0);
            transform: skew(0.43deg);
        }
        30% {
            clip: rect(57px, 9999px, 73px, 0);
            transform: skew(0.07deg);
        }
        35% {
            clip: rect(86px, 9999px, 62px, 0);
            transform: skew(0.58deg);
        }
        40% {
            clip: rect(90px, 9999px, 30px, 0);
            transform: skew(0.13deg);
        }
        45% {
            clip: rect(5px, 9999px, 56px, 0);
            transform: skew(0.8deg);
        }
        50% {
            clip: rect(46px, 9999px, 83px, 0);
            transform: skew(0.63deg);
        }
        55% {
            clip: rect(93px, 9999px, 78px, 0);
            transform: skew(0.02deg);
        }
        60% {
            clip: rect(89px, 9999px, 40px, 0);
            transform: skew(0.02deg);
        }
        65% {
            clip: rect(98px, 9999px, 85px, 0);
            transform: skew(0.1deg);
        }
        70% {
            clip: rect(24px, 9999px, 4px, 0);
            transform: skew(0.08deg);
        }
        75% {
            clip: rect(66px, 9999px, 93px, 0);
            transform: skew(0.3deg);
        }
        80% {
            clip: rect(97px, 9999px, 13px, 0);
            transform: skew(0.01deg);
        }
        85% {
            clip: rect(36px, 9999px, 26px, 0);
            transform: skew(0.88deg);
        }
        90% {
            clip: rect(2px, 9999px, 53px, 0);
            transform: skew(0.08deg);
        }
        95% {
            clip: rect(95px, 9999px, 34px, 0);
            transform: skew(0.08deg);
        }
        100% {
            clip: rect(90px, 9999px, 5px, 0);
            transform: skew(0.01deg);
        }
    }

    @keyframes glitch-anim2 {
        0% {
            clip: rect(65px, 9999px, 91px, 0);
            transform: skew(0.6deg);
        }
        5% {
            clip: rect(95px, 9999px, 54px, 0);
            transform: skew(0.59deg);
        }
        10% {
            clip: rect(90px, 9999px, 94px, 0);
            transform: skew(0.94deg);
        }
        15% {
            clip: rect(86px, 9999px, 82px, 0);
            transform: skew(0.71deg);
        }
        20% {
            clip: rect(94px, 9999px, 4px, 0);
            transform: skew(0.02deg);
        }
        25% {
            clip: rect(42px, 9999px, 2px, 0);
            transform: skew(0.05deg);
        }
        30% {
            clip: rect(60px, 9999px, 35px, 0);
            transform: skew(0.17deg);
        }
        35% {
            clip: rect(51px, 9999px, 11px, 0);
            transform: skew(0.48deg);
        }
        40% {
            clip: rect(9px, 9999px, 31px, 0);
            transform: skew(0.24deg);
        }
        45% {
            clip: rect(39px, 9999px, 16px, 0);
            transform: skew(0.62deg);
        }
        50% {
            clip: rect(98px, 9999px, 70px, 0);
            transform: skew(0.1deg);
        }
        55% {
            clip: rect(99px, 9999px, 61px, 0);
            transform: skew(0.83deg);
        }
        60% {
            clip: rect(66px, 9999px, 62px, 0);
            transform: skew(0.02deg);
        }
        65% {
            clip: rect(69px, 9999px, 7px, 0);
            transform: skew(0.05deg);
        }
        70% {
            clip: rect(48px, 9999px, 59px, 0);
            transform: skew(0.39deg);
        }
        75% {
            clip: rect(65px, 9999px, 34px, 0);
            transform: skew(0.3deg);
        }
        80% {
            clip: rect(23px, 9999px, 35px, 0);
            transform: skew(0.61deg);
        }
        85% {
            clip: rect(18px, 9999px, 64px, 0);
            transform: skew(0.75deg);
        }
        90% {
            clip: rect(10px, 9999px, 82px, 0);
            transform: skew(0.97deg);
        }
        95% {
            clip: rect(62px, 9999px, 31px, 0);
            transform: skew(0.59deg);
        }
        100% {
            clip: rect(96px, 9999px, 46px, 0);
            transform: skew(0.09deg);
        }
    }
</style>