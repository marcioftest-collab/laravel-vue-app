<script setup>
import { Head, Link } from '@inertiajs/vue3';

defineProps({
    canLogin: {
        type: Boolean,
    },
    canRegister: {
        type: Boolean,
    },
    laravelVersion: {
        type: String,
        required: true,
    },
    phpVersion: {
        type: String,
        required: true,
    },
});
</script>

<template>
    <Head title="Welcome | Premium App" />
    
    <div class="relative min-h-screen overflow-hidden bg-slate-950 font-sans antialiased selection:bg-cyan-500 selection:text-white">
        <!-- Animated Background Blobs -->
        <div class="absolute -top-[10%] -left-[10%] h-[500px] w-[500px] rounded-full bg-violet-600/20 blur-[120px] animate-pulse"></div>
        <div class="absolute top-[20%] -right-[10%] h-[400px] w-[400px] rounded-full bg-cyan-600/20 blur-[120px] animate-pulse delay-700"></div>
        <div class="absolute bottom-0 left-[20%] h-[300px] w-[600px] rounded-full bg-blue-600/20 blur-[120px]"></div>

        <div class="relative flex min-h-screen flex-col">
            <!-- Navigation -->
            <header class="container mx-auto flex items-center justify-between px-6 py-8">
                <div class="flex items-center gap-2">
                    <div class="flex h-10 w-10 items-center justify-center rounded-xl bg-gradient-to-br from-violet-600 to-cyan-500 shadow-lg shadow-violet-500/20">
                        <svg class="h-6 w-6 text-white" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z" />
                        </svg>
                    </div>
                    <span class="text-xl font-bold tracking-tight text-white">Antigravity</span>
                </div>

                <nav v-if="canLogin" class="flex items-center gap-4">
                    <Link
                        v-if="$page.props.auth.user"
                        :href="route('dashboard')"
                        class="rounded-full px-5 py-2 text-sm font-medium text-slate-300 transition hover:text-white hover:bg-white/5"
                    >
                        Dashboard
                    </Link>

                    <template v-else>
                        <Link
                            :href="route('login')"
                            class="rounded-full px-5 py-2 text-sm font-medium text-slate-300 transition hover:text-white hover:bg-white/5"
                        >
                            Log in
                        </Link>

                        <Link
                            v-if="canRegister"
                            :href="route('register')"
                            class="rounded-full bg-white px-6 py-2 text-sm font-semibold text-slate-950 transition hover:bg-slate-200"
                        >
                            Get Started
                        </Link>
                    </template>
                </nav>
            </header>

            <!-- Hero Section -->
            <main class="container mx-auto flex flex-1 flex-col items-center justify-center px-6 py-12 text-center lg:py-24">
                <div class="inline-flex items-center gap-2 rounded-full border border-white/10 bg-white/5 px-4 py-1.5 text-sm font-medium text-cyan-400 backdrop-blur-md">
                    <span class="relative flex h-2 w-2">
                        <span class="absolute inline-flex h-full w-full animate-ping rounded-full bg-cyan-400 opacity-75"></span>
                        <span class="relative inline-flex h-2 w-2 rounded-full bg-cyan-500"></span>
                    </span>
                    Laravel 12 + Vue 3 Scaffolding
                </div>
                
                <h1 class="mt-8 max-w-4xl text-5xl font-extrabold tracking-tight text-white sm:text-7xl lg:text-8xl">
                    Deployed with <span class="bg-gradient-to-r from-violet-400 via-cyan-400 to-emerald-400 bg-clip-text text-transparent">Automated</span> <span class="bg-gradient-to-r from-emerald-400 via-cyan-400 to-violet-400 bg-clip-text text-transparent italic">Pipelines</span>
                </h1>
                
                <p class="mt-8 max-w-2xl text-lg text-slate-400 sm:text-xl">
                    The ultimate starting point for your next masterpiece. Craft stunning user experiences with Laravel's robust backend and Vue's dynamic frontend.
                </p>

                <div class="mt-12 flex flex-col gap-4 sm:flex-row">
                    <button class="group relative flex items-center justify-center gap-2 rounded-2xl bg-gradient-to-r from-violet-600 to-cyan-600 px-8 py-4 font-bold text-white transition-all hover:scale-105 hover:shadow-[0_0_40px_8px_rgba(124,58,237,0.3)]">
                        Launch Project
                        <svg class="h-5 w-5 transition-transform group-hover:translate-x-1" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 5l7 7m0 0l-7 7m7-7H3" />
                        </svg>
                    </button>
                    <button class="flex items-center justify-center gap-2 rounded-2xl border border-white/10 bg-white/5 px-8 py-4 font-bold text-white backdrop-blur-md transition-all hover:bg-white/10">
                        View Demo
                    </button>
                </div>

                <!-- Feature Grid -->
                <div class="mt-32 grid w-full max-w-6xl grid-cols-1 gap-8 sm:grid-cols-2 lg:grid-cols-3">
                    <div class="group relative rounded-3xl border border-white/5 bg-white/5 p-8 text-left backdrop-blur-xl transition hover:border-violet-500/30 hover:bg-white/[0.07]">
                        <div class="mb-4 inline-flex h-12 w-12 items-center justify-center rounded-2xl bg-violet-600/10 text-violet-400">
                            <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 20l4-16m4 4l4 4-4 4M6 16l-4-4 4-4" />
                            </svg>
                        </div>
                        <h3 class="text-xl font-bold text-white">Full Stack Inertia</h3>
                        <p class="mt-2 text-slate-400">The power of single-page apps without the complexity of building an API.</p>
                    </div>

                    <div class="group relative rounded-3xl border border-white/5 bg-white/5 p-8 text-left backdrop-blur-xl transition hover:border-cyan-500/30 hover:bg-white/[0.07]">
                        <div class="mb-4 inline-flex h-12 w-12 items-center justify-center rounded-2xl bg-cyan-600/10 text-cyan-400">
                            <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 15v2m-6 4h12a2 2 0 002-2v-6a2 2 0 00-2-2H6a2 2 0 00-2 2v6a2 2 0 002 2zm10-10V7a4 4 0 00-8 0v4h8z" />
                            </svg>
                        </div>
                        <h3 class="text-xl font-bold text-white">Advanced Auth</h3>
                        <p class="mt-2 text-slate-400">Robust authentication, verification, and profile management out of the box.</p>
                    </div>

                    <div class="group relative rounded-3xl border border-white/5 bg-white/5 p-8 text-left backdrop-blur-xl transition hover:border-emerald-500/30 hover:bg-white/[0.07]">
                        <div class="mb-4 inline-flex h-12 w-12 items-center justify-center rounded-2xl bg-emerald-600/10 text-emerald-400">
                            <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z" />
                            </svg>
                        </div>
                        <h3 class="text-xl font-bold text-white">Vite Optimized</h3>
                        <p class="mt-2 text-slate-400">Lightning fast HMR and optimized production bundles for maximum performance.</p>
                    </div>
                </div>
            </main>

            <!-- Footer -->
            <footer class="mt-auto border-t border-white/5 px-6 py-12 backdrop-blur-md">
                <div class="container mx-auto flex flex-col items-center justify-between gap-6 md:flex-row">
                    <p class="text-sm text-slate-500">
                        &copy; 2026 Antigravity. Built with Laravel v{{ laravelVersion }} and Vue.
                    </p>
                    <div class="flex gap-8 text-sm font-medium text-slate-400">
                        <a href="#" class="transition hover:text-white">Documentation</a>
                        <a href="#" class="transition hover:text-white">GitHub</a>
                        <a href="#" class="transition hover:text-white">Twitter</a>
                    </div>
                </div>
            </footer>
        </div>
    </div>
</template>

<style scoped>
@keyframes blob {
    0% { transform: translate(0px, 0px) scale(1); }
    33% { transform: translate(30px, -50px) scale(1.1); }
    66% { transform: translate(-20px, 20px) scale(0.9); }
    100% { transform: translate(0px, 0px) scale(1); }
}
.animate-blob {
    animation: blob 7s infinite;
}
</style>
