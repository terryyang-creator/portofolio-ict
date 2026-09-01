<style>
    body {
        font-family: 'Fredoka', 'Fredoka One', cursive, sans-serif;
        background-color: #FDFBF7;
        color: #4A3E3D;
        -webkit-tap-highlight-color: transparent;
    }

    /* Smooth Scrolling with Offset for Sticky Navbar */
    html {
        scroll-behavior: smooth;
        scroll-padding-top: 5.5rem;
    }
    
    .font-display {
        font-family: 'Fredoka One', cursive, sans-serif;
    }

    .soft-shadow {
        box-shadow: 0 10px 30px -5px rgba(142, 119, 102, 0.08);
    }

    .soft-shadow-hover {
        transition: all 0.25s cubic-bezier(0.4, 0, 0.2, 1);
    }

    .soft-shadow-hover:active,
    .soft-shadow-hover:hover {
        transform: translateY(-3px);
        box-shadow: 0 14px 35px -5px rgba(142, 119, 102, 0.15);
    }

    @keyframes soft-pulse {
        0%, 100% { opacity: 1; transform: scale(1); }
        50% { opacity: 0.5; transform: scale(1.15); }
    }
    .animate-soft-pulse {
        animation: soft-pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
    }

    /* Custom scrollbar for modals */
    ::-webkit-scrollbar {
        width: 6px;
    }
    ::-webkit-scrollbar-track {
        background: #F5EFE6;
    }
    .dark ::-webkit-scrollbar-track {
        background: #1E1A17;
    }
    ::-webkit-scrollbar-thumb {
        background: #D8C4B6;
        border-radius: 999px;
    }
    .dark ::-webkit-scrollbar-thumb {
        background: #4A4039;
    }
</style>


<!-- Floating Mobile Header -->
<header id="main-header" class="sticky top-0 z-40 backdrop-blur-md bg-[#FDFBF7]/90 dark:bg-[#181513]/90 border-b border-[#F0E5D8] dark:border-[#3D352F] px-4 py-2.5 transition-all duration-300">
    <div class="max-w-md mx-auto space-y-2">
        <div class="flex items-center justify-between">
            <a href="#hero" class="flex items-center gap-2 group">
                <div class="w-8 h-8 rounded-full bg-[#E8DFCA] dark:bg-[#2D2723] flex items-center justify-center font-display text-base text-[#8C6D58] dark:text-[#EADBC8] border border-[#D8C4B6] dark:border-[#4A4039] group-hover:bg-[#EADBC8] transition-colors">
                    T
                </div>
                <span class="font-display text-lg tracking-wide text-[#5C4B43] dark:text-[#EADBC8]" id="nav-header-name">Terry.Yang</span>
            </a>
            
            <div class="flex items-center gap-2">
                <!-- Dark Mode Toggle Button -->
                <button id="theme-toggle-btn" onclick="toggleDarkMode()" aria-label="Toggle Dark Mode" class="flex items-center justify-center w-8 h-8 rounded-full bg-[#F5EFE6] dark:bg-[#2D2723] hover:bg-[#EADBC8] dark:hover:bg-[#3D352F] text-[#786254] dark:text-[#EADBC8] border border-[#D8C4B6] dark:border-[#4A4039] transition-colors">
                    <span id="theme-icon" class="text-sm">🌙</span>
                </button>

                <!-- Admin Lock/Dashboard Toggle Button -->
                <button id="admin-toggle-btn" onclick="openAdminModal()" class="flex items-center gap-1.5 text-xs font-semibold bg-[#F5EFE6] dark:bg-[#2D2723] hover:bg-[#EADBC8] dark:hover:bg-[#3D352F] text-[#786254] dark:text-[#EADBC8] px-3 py-1.5 rounded-full border border-[#D8C4B6] dark:border-[#4A4039] transition-colors">
                    <span id="admin-icon">🔒</span>
                    <span id="admin-btn-text">Admin</span>
                </button>
            </div>
        </div>

        <!-- Mobile Sticky Nav Links with Smooth Scroll -->
        <nav class="flex items-center justify-between gap-1 border-t border-[#F0E5D8]/60 dark:border-[#3D352F]/60 pt-2 text-[11px] font-semibold text-[#786254] dark:text-[#C4B5A5]">
            <a href="#hero" class="hover:text-[#3C3633] dark:hover:text-[#FDFBF7] px-2 py-0.5 rounded-lg hover:bg-[#F5EFE6] dark:hover:bg-[#2D2723] transition-colors">Profil</a>
            <a href="#skills" class="hover:text-[#3C3633] dark:hover:text-[#FDFBF7] px-2 py-0.5 rounded-lg hover:bg-[#F5EFE6] dark:hover:bg-[#2D2723] transition-colors">Keahlian</a>
            <a href="#projects" class="hover:text-[#3C3633] dark:hover:text-[#FDFBF7] px-2 py-0.5 rounded-lg hover:bg-[#F5EFE6] dark:hover:bg-[#2D2723] transition-colors">Proyek ICT</a>
            <a href="#contact" class="hover:text-[#3C3633] dark:hover:text-[#FDFBF7] px-2 py-0.5 rounded-lg hover:bg-[#F5EFE6] dark:hover:bg-[#2D2723] transition-colors">Kontak</a>
        </nav>
    </div>
</header>

<!-- Admin Top Banner (Visible when logged in) -->
<div id="admin-banner" class="hidden bg-[#8C6D58] dark:bg-[#5C4535] text-[#FDFBF7] px-4 py-2.5 shadow-inner">
    <div class="max-w-md mx-auto flex items-center justify-between text-xs">
        <div class="flex items-center gap-1.5">
            <span class="w-2 h-2 rounded-full bg-emerald-400"></span>
            <span class="font-medium">Mode Admin Aktif</span>
        </div>
        <div class="flex items-center gap-2">
            <button onclick="openProfileEditModal()" class="bg-[#FFFDF9]/20 hover:bg-[#FFFDF9]/30 px-2.5 py-1 rounded-lg transition-colors">
                ✏️ Profil
            </button>
            <button onclick="openAdminCredModal()" class="bg-[#FFFDF9]/20 hover:bg-[#FFFDF9]/30 px-2.5 py-1 rounded-lg transition-colors">
                🔑 Password
            </button>
            <button onclick="openAddProjectModal()" class="bg-[#EADBC8] text-[#3C3633] font-semibold px-2.5 py-1 rounded-lg hover:bg-[#D9C3AD] transition-colors">
                ➕ Proyek
            </button>
            <button onclick="logoutAdmin()" class="text-xs underline text-red-200 hover:text-red-100 ml-1">
                Keluar
            </button>
        </div>
    </div>
</div>

<main class="max-w-md mx-auto px-5 pt-6 space-y-7 sm:max-w-lg md:max-w-xl">

    <!-- Hero Section -->
    <section id="hero" class="text-center p-6 sm:p-8 rounded-3xl bg-gradient-to-b from-[#F5EFE6] via-[#EADBC8]/40 to-[#FFFDF9] dark:from-[#26211E] dark:via-[#2D2723] dark:to-[#1E1A17] border border-[#EADBC8] dark:border-[#3D352F] soft-shadow relative overflow-hidden transition-colors">
        <!-- Decorative Background Glow Effect -->
        <div class="absolute -top-12 -left-12 w-32 h-32 bg-[#EADBC8]/40 dark:bg-[#8C6D58]/20 rounded-full blur-2xl pointer-events-none"></div>
        <div class="absolute -bottom-12 -right-12 w-32 h-32 bg-[#D8C4B6]/30 dark:bg-[#5C4535]/20 rounded-full blur-2xl pointer-events-none"></div>

        <!-- Status Badge -->
        <div class="relative z-10 inline-flex items-center gap-2 px-3.5 py-1 rounded-full bg-[#FFFDF9]/90 dark:bg-[#26211E]/90 backdrop-blur-sm border border-[#EADBC8] dark:border-[#3D352F] text-xs text-[#786254] dark:text-[#C4B5A5] mb-5 shadow-sm">
            <span class="w-2 h-2 rounded-full bg-[#A8BBA2] animate-soft-pulse"></span>
            <span id="display-status-badge">Mutiara Bangsa 2 School • Kelas ICT</span>
        </div>

        <!-- Profile Picture -->
        <div class="relative z-10 w-28 h-28 mx-auto mb-4 group">
            <div class="absolute inset-0 rounded-full bg-gradient-to-tr from-[#EADBC8] to-[#D8C4B6] dark:from-[#3D352F] dark:to-[#5C4535] rotate-6 scale-105 shadow-md"></div>
            <div class="absolute inset-0 rounded-full bg-[#F5EFE6] dark:bg-[#26211E] -rotate-3 scale-100"></div>
            <img id="display-avatar" 
                 src="https://placehold.co/200x200/E8DFCA/6E5B4F?text=Terry+Y" 
                 alt="Foto Profil Terry Yang" 
                 class="relative w-full h-full object-cover rounded-full border-4 border-[#FFFDF9] dark:border-[#26211E] shadow-sm">
        </div>

        <!-- Title & Bio -->
        <div class="relative z-10 space-y-2">
            <h1 id="display-name" class="font-display text-3xl sm:text-4xl text-[#3C3633] dark:text-[#FDFBF7] tracking-wide">
                Halo, Saya Terry Yang 👋
            </h1>
            <p id="display-bio" class="text-base font-normal text-[#786254] dark:text-[#C4B5A5] leading-relaxed max-w-sm mx-auto">
                Siswa Mutiara Bangsa 2 School yang antusias mengeksplorasi dunia ICT, pemrograman web, dan teknologi visual digital.
            </p>
        </div>
    </section>

    <!-- Quick Stats Grid -->
    <section class="grid grid-cols-3 gap-3">
        <div class="bg-[#FFFDF9] dark:bg-[#26211E] border border-[#F0E5D8] dark:border-[#3D352F] rounded-2xl p-3 text-center soft-shadow">
            <div class="font-display text-xl text-[#8C6D58] dark:text-[#D8C4B6]" id="stat-school">MB 2</div>
            <div class="text-[11px] text-[#8C7A6B] dark:text-[#A89889] font-medium mt-0.5">Sekolah</div>
        </div>
        <div class="bg-[#FFFDF9] dark:bg-[#26211E] border border-[#F0E5D8] dark:border-[#3D352F] rounded-2xl p-3 text-center soft-shadow">
            <div class="font-display text-xl text-[#8C6D58] dark:text-[#D8C4B6]" id="stat-class">ICT</div>
            <div class="text-[11px] text-[#8C7A6B] dark:text-[#A89889] font-medium mt-0.5">Kelas Komputer</div>
        </div>
        <div class="bg-[#FFFDF9] dark:bg-[#26211E] border border-[#F0E5D8] dark:border-[#3D352F] rounded-2xl p-3 text-center soft-shadow">
            <div class="font-display text-xl text-[#8C6D58] dark:text-[#D8C4B6]" id="stat-projects-count">0</div>
            <div class="text-[11px] text-[#8C7A6B] dark:text-[#A89889] font-medium mt-0.5">Proyek Selesai</div>
        </div>
    </section>

    <!-- About & Skill Chips -->
    <section id="skills" class="bg-[#FFFDF9] dark:bg-[#26211E] border border-[#F0E5D8] dark:border-[#3D352F] rounded-3xl p-5 soft-shadow space-y-4">
        <div class="flex items-center justify-between">
            <div class="flex items-center gap-2">
                <span class="text-xl">✨</span>
                <h2 class="font-display text-xl text-[#3C3633] dark:text-[#FDFBF7]">Keahlian ICT</h2>
            </div>
            <button onclick="openProfileEditModal()" class="admin-only hidden text-xs font-semibold text-[#8C6D58] dark:text-[#D8C4B6] hover:underline">
                + Edit Skills
            </button>
        </div>
        <p class="text-xs text-[#786254] dark:text-[#C4B5A5] leading-relaxed">
            Keterampilan teknis dan praktis yang saya pelajari dan kembangkan selama pembelajaran komputer.
        </p>
        
        <!-- Skill Badges Container -->
        <div id="skills-container" class="flex flex-wrap gap-2 pt-1">
            <!-- Dynamic Skills Rendered Here -->
        </div>
    </section>

    <!-- Portfolio Projects -->
    <section id="projects" class="space-y-4">
        <div class="flex items-center justify-between px-1">
            <h2 class="font-display text-xl text-[#3C3633] dark:text-[#FDFBF7] flex items-center gap-2">
                <span>📂</span> Proyek Komputer ICT
            </h2>
            <div class="flex items-center gap-2">
                <span class="text-xs text-[#8C7A6B] dark:text-[#A89889]">Showcase Karya</span>
                <button onclick="openAddProjectModal()" class="admin-only hidden bg-[#EADBC8] dark:bg-[#3D352F] hover:bg-[#D9C3AD] dark:hover:bg-[#4A4039] text-[#3C3633] dark:text-[#FDFBF7] text-xs px-2.5 py-1 rounded-full font-semibold border border-[#D8C4B6] dark:border-[#4A4039] transition-colors">
                    + Proyek Baru
                </button>
            </div>
        </div>

        <!-- Dynamic Projects List Container -->
        <div id="projects-list-container" class="space-y-4">
            <!-- Dynamic Content Loaded via LocalStorage -->
        </div>
    </section>

    <!-- Layanan / What I Do -->
    <section class="bg-[#F5EFE6] dark:bg-[#231E1B] border border-[#EADBC8] dark:border-[#3D352F] rounded-3xl p-5 space-y-4">
        <h2 class="font-display text-xl text-[#3C3633] dark:text-[#FDFBF7] flex items-center gap-2">
            <span>🏫</span> Pembelajaran ICT di Sekolah
        </h2>
        <div class="space-y-3">
            <div class="bg-[#FFFDF9] dark:bg-[#26211E] p-3.5 rounded-2xl border border-[#F0E5D8] dark:border-[#3D352F] flex items-start gap-3">
                <div class="w-8 h-8 rounded-xl bg-[#E8DFCA] dark:bg-[#322A25] flex items-center justify-center text-sm shrink-0">
                    💻
                </div>
                <div>
                    <h4 class="font-display text-sm text-[#3C3633] dark:text-[#FDFBF7]">Pemrograman & HTML/CSS</h4>
                    <p class="text-[11px] text-[#786254] dark:text-[#C4B5A5] mt-0.5">Mempelajari struktur dasar halaman web, styling tampilan, dan pembuatan antarmuka ramah mobile.</p>
                </div>
            </div>

            <div class="bg-[#FFFDF9] dark:bg-[#26211E] p-3.5 rounded-2xl border border-[#F0E5D8] dark:border-[#3D352F] flex items-start gap-3">
                <div class="w-8 h-8 rounded-xl bg-[#E8DFCA] dark:bg-[#322A25] flex items-center justify-center text-sm shrink-0">
                    🎯
                </div>
                <div>
                    <h4 class="font-display text-sm text-[#3C3633] dark:text-[#FDFBF7]">Keterampilan Teknologi Digital</h4>
                    <p class="text-[11px] text-[#786254] dark:text-[#C4B5A5] mt-0.5">Eksplorasi software produktivitas, logika dasar komputer, dan komunikasi visual di Mutiara Bangsa 2.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="bg-[#FFFDF9] dark:bg-[#26211E] border border-[#F0E5D8] dark:border-[#3D352F] rounded-3xl p-5 text-center soft-shadow space-y-4">
        <div class="inline-block p-3 rounded-2xl bg-[#F5EFE6] dark:bg-[#2D2723] border border-[#EADBC8] dark:border-[#3D352F] text-2xl mb-1">
            💌
        </div>
        <h2 class="font-display text-2xl text-[#3C3633] dark:text-[#FDFBF7]">Hubungi Terry</h2>
        <p class="text-xs text-[#786254] dark:text-[#C4B5A5] max-w-xs mx-auto leading-relaxed">
            Ingin berdiskusi atau melihat lebih banyak tugas dan proyek ICT Mutiara Bangsa 2 School? Silakan sapa Terry!
        </p>

        <div class="space-y-2.5 pt-2">
            <a id="contact-email-link" href="mailto:terry@example.com" 
               class="w-full flex items-center justify-center gap-2 py-3 px-4 rounded-2xl bg-[#EADBC8] dark:bg-[#3D352F] hover:bg-[#D9C3AD] dark:hover:bg-[#4A4039] text-[#3C3633] dark:text-[#FDFBF7] font-display text-sm border border-[#D8C4B6] dark:border-[#4A4039] transition-transform active:scale-95">
                <svg class="w-5 h-5 text-[#6E5B4F] dark:text-[#EADBC8]" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"></path>
                </svg>
                <span>Kirim Email Ke Terry</span>
            </a>
        </div>
    </section>

</main>

<!-- Footer -->
<footer class="max-w-md mx-auto mt-8 px-5 text-center text-[11px] text-[#8C7A6B] dark:text-[#A89889] space-y-3">
    <!-- Social Media Icons Row -->
    <div class="flex items-center justify-center gap-3 pt-2 pb-1">
        <!-- GitHub -->
        <a id="footer-github" href="https://github.com" target="_blank" rel="noopener noreferrer" aria-label="GitHub Terry Yang"
           class="w-9 h-9 rounded-full bg-[#F5EFE6] dark:bg-[#26211E] hover:bg-[#EADBC8] dark:hover:bg-[#3D352F] text-[#6E5B4F] dark:text-[#EADBC8] flex items-center justify-center border border-[#EADBC8] dark:border-[#3D352F] shadow-sm transition-transform active:scale-95" title="GitHub">
            <svg class="w-4 h-4 fill-current" viewBox="0 0 24 24">
                <path d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0024 12c0-6.63-5.37-12-12-12z"/>
            </svg>
        </a>
        <!-- Instagram -->
        <a id="footer-instagram" href="https://instagram.com" target="_blank" rel="noopener noreferrer" aria-label="Instagram Terry Yang"
           class="w-9 h-9 rounded-full bg-[#F5EFE6] dark:bg-[#26211E] hover:bg-[#EADBC8] dark:hover:bg-[#3D352F] text-[#6E5B4F] dark:text-[#EADBC8] flex items-center justify-center border border-[#EADBC8] dark:border-[#3D352F] shadow-sm transition-transform active:scale-95" title="Instagram">
            <svg class="w-4 h-4 fill-current" viewBox="0 0 24 24">
                <path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/>
            </svg>
        </a>
        <!-- YouTube -->
        <a id="footer-youtube" href="https://youtube.com" target="_blank" rel="noopener noreferrer" aria-label="YouTube Terry Yang"
           class="w-9 h-9 rounded-full bg-[#F5EFE6] dark:bg-[#26211E] hover:bg-[#EADBC8] dark:hover:bg-[#3D352F] text-[#6E5B4F] dark:text-[#EADBC8] flex items-center justify-center border border-[#EADBC8] dark:border-[#3D352F] shadow-sm transition-transform active:scale-95" title="YouTube">
            <svg class="w-4 h-4 fill-current" viewBox="0 0 24 24">
                <path d="M23.498 6.186a3.016 3.016 0 0 0-2.122-2.136C19.505 3.545 12 3.545 12 3.545s-7.505 0-9.377.505A3.017 3.017 0 0 0 .502 6.186C0 8.07 0 12 0 12s0 3.93.502 5.814a3.016 3.016 0 0 0 2.122 2.136c1.871.505 9.376.505 9.376.505s7.505 0 9.377-.505a3.015 3.015 0 0 0 2.122-2.136C24 15.93 24 12 24 12s0-3.93-.502-5.814zM9.545 15.568V8.432L15.818 12l-6.273 3.568z"/>
            </svg>
        </a>
        <!-- TikTok -->
        <a id="footer-tiktok" href="https://tiktok.com" target="_blank" rel="noopener noreferrer" aria-label="TikTok Terry Yang"
           class="w-9 h-9 rounded-full bg-[#F5EFE6] dark:bg-[#26211E] hover:bg-[#EADBC8] dark:hover:bg-[#3D352F] text-[#6E5B4F] dark:text-[#EADBC8] flex items-center justify-center border border-[#EADBC8] dark:border-[#3D352F] shadow-sm transition-transform active:scale-95" title="TikTok">
            <svg class="w-4 h-4 fill-current" viewBox="0 0 24 24">
                <path d="M12.525 0h3.08c.049 1.493.697 2.859 1.77 3.854 1.07.994 2.525 1.543 4.025 1.543v3.155c-1.928-.086-3.701-.76-5.143-1.898v8.213c0 2.179-.838 4.225-2.359 5.753-1.521 1.527-3.565 2.37-5.744 2.37-2.179 0-4.223-.843-5.744-2.37C.889 19.092.05 17.046.05 14.867c0-2.179.839-4.225 2.36-5.753C3.93 7.587 5.974 6.744 8.153 6.744c.47 0 .937.04 1.393.118v3.256a6.007 6.007 0 0 0-1.393-.162c-1.332 0-2.584.518-3.526 1.46-.942.942-1.46 2.194-1.46 3.526 0 1.332.518 2.584 1.46 3.526.942.942 2.194 1.46 3.526 1.46 1.332 0 2.584-.518 3.526-1.46.942-.942 1.46-2.194 1.46-3.526V0z"/>
            </svg>
        </a>
        <!-- LinkedIn -->
        <a id="footer-linkedin" href="https://linkedin.com" target="_blank" rel="noopener noreferrer" aria-label="LinkedIn Terry Yang"
           class="w-9 h-9 rounded-full bg-[#F5EFE6] dark:bg-[#26211E] hover:bg-[#EADBC8] dark:hover:bg-[#3D352F] text-[#6E5B4F] dark:text-[#EADBC8] flex items-center justify-center border border-[#EADBC8] dark:border-[#3D352F] shadow-sm transition-transform active:scale-95" title="LinkedIn">
            <svg class="w-4 h-4 fill-current" viewBox="0 0 24 24">
                <path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"/>
            </svg>
        </a>
    </div>

    <p>© 2026 Terry Yang • Mutiara Bangsa 2 School.</p>
    <div class="flex items-center justify-center gap-1 text-[10px] text-[#A08E7E]">
        <span>Portofolio & CMS Backend ICT • Tersimpan Secara Lokal (LocalStorage)</span>
    </div>
</footer>

<!-- MODAL 1: Admin Login Dialog -->
<div id="login-modal" class="fixed inset-0 z-50 bg-black/40 dark:bg-black/60 backdrop-blur-sm hidden flex items-center justify-center p-4">
    <div class="bg-[#FFFDF9] dark:bg-[#26211E] border border-[#EADBC8] dark:border-[#3D352F] w-full max-w-sm rounded-3xl p-6 soft-shadow space-y-4">
        <div class="flex items-center justify-between border-b border-[#F0E5D8] dark:border-[#3D352F] pb-3">
            <h3 class="font-display text-xl text-[#3C3633] dark:text-[#FDFBF7] flex items-center gap-2">
                🛡️ Login Admin Aman
            </h3>
            <button onclick="closeAdminModal()" class="text-gray-400 hover:text-gray-600 dark:hover:text-gray-200 text-lg font-bold">
                ✕
            </button>
        </div>

        <p class="text-xs text-[#786254] dark:text-[#C4B5A5]">Masukkan username & password untuk mengelola konten portofolio.</p>

        <!-- Alert Notice for Errors & Lockout -->
        <div id="login-error" class="hidden bg-red-50 dark:bg-red-950/40 border border-red-200 dark:border-red-900/50 text-red-600 dark:text-red-300 text-xs p-3 rounded-xl font-medium leading-relaxed">
            Username atau Password salah!
        </div>

        <!-- Lockout Timer Notice -->
        <div id="lockout-notice" class="hidden bg-amber-50 dark:bg-amber-950/40 border border-amber-200 dark:border-amber-900/50 text-amber-800 dark:text-amber-300 text-xs p-3 rounded-xl font-medium space-y-1">
            <div class="flex items-center gap-1.5 font-bold">
                <span>⛔ Sesi Terkunci Sementara</span>
            </div>
            <p id="lockout-timer-text">Terlalu banyak percobaan gagal. Silakan tunggu 0 detik lagi.</p>
        </div>

        <form id="admin-login-form" onsubmit="handleAdminLogin(event)" class="space-y-3">
            <div>
                <label class="block text-xs font-semibold text-[#6E5B4F] dark:text-[#C4B5A5] mb-1">Username Admin</label>
                <input type="text" id="admin-username" required placeholder="Masukkan username (Default: admin)" autocomplete="username"
                       class="w-full px-3.5 py-2.5 rounded-xl border border-[#D8C4B6] dark:border-[#4A4039] bg-[#FDFBF7] dark:bg-[#1E1A17] text-[#3C3633] dark:text-[#FDFBF7] text-xs focus:outline-none focus:ring-2 focus:ring-[#8C6D58]">
            </div>
            <div>
                <label class="block text-xs font-semibold text-[#6E5B4F] dark:text-[#C4B5A5] mb-1">Password</label>
                <div class="relative">
                    <input type="password" id="admin-password" required placeholder="Masukkan password (Default: admin123)" autocomplete="current-password"
                           class="w-full px-3.5 py-2.5 pr-10 rounded-xl border border-[#D8C4B6] dark:border-[#4A4039] bg-[#FDFBF7] dark:bg-[#1E1A17] text-[#3C3633] dark:text-[#FDFBF7] text-xs focus:outline-none focus:ring-2 focus:ring-[#8C6D58]">
                    <button type="button" onclick="togglePasswordVisibility('admin-password', this)" class="absolute right-3 top-1/2 -translate-y-1/2 text-gray-400 hover:text-gray-600 dark:hover:text-gray-200 text-sm">
                        👁️
                    </button>
                </div>
            </div>
            <div class="pt-2 flex items-center justify-end gap-2">
                <button type="button" onclick="closeAdminModal()" class="px-4 py-2 text-xs font-medium text-[#786254] dark:text-[#C4B5A5] hover:bg-[#F5EFE6] dark:hover:bg-[#2D2723] rounded-xl">
                    Batal
                </button>
                <button type="submit" id="login-submit-btn" class="px-5 py-2 bg-[#8C6D58] hover:bg-[#785b47] text-white font-display text-xs rounded-xl shadow-sm transition-all disabled:opacity-50 disabled:cursor-not-allowed">
                    Masuk Admin
                </button>
            </div>
        </form>
        <div id="login-credentials-hint" class="bg-[#F5EFE6] dark:bg-[#2D2723] p-2.5 rounded-xl text-[10px] text-[#8C7A6B] dark:text-[#A89889] text-center">
            Autentikasi terenkripsi aktif • Web Crypto SHA-256
        </div>
    </div>
</div>

<!-- MODAL 2: Add / Edit Project Card -->
<div id="project-modal" class="fixed inset-0 z-50 bg-black/40 dark:bg-black/60 backdrop-blur-sm hidden flex items-center justify-center p-4">
    <div class="bg-[#FFFDF9] dark:bg-[#26211E] border border-[#EADBC8] dark:border-[#3D352F] w-full max-w-md rounded-3xl p-6 soft-shadow space-y-4 max-h-[90vh] overflow-y-auto">
        <div class="flex items-center justify-between border-b border-[#F0E5D8] dark:border-[#3D352F] pb-3">
            <h3 id="project-modal-title" class="font-display text-xl text-[#3C3633] dark:text-[#FDFBF7]">
                📂 Kelola Proyek ICT
            </h3>
            <button onclick="closeProjectModal()" class="text-gray-400 hover:text-gray-600 dark:hover:text-gray-200 text-lg font-bold">
                ✕
            </button>
        </div>

        <form id="project-form" onsubmit="handleSaveProject(event)" class="space-y-3 text-xs">
            <input type="hidden" id="project-id" value="">

            <div>
                <label class="block font-semibold text-[#6E5B4F] dark:text-[#C4B5A5] mb-1">Judul Proyek</label>
                <input type="text" id="project-title" required placeholder="Contoh: Aplikasi Kalkulator HTML"
                       class="w-full px-3.5 py-2.5 rounded-xl border border-[#D8C4B6] dark:border-[#4A4039] bg-[#FDFBF7] dark:bg-[#1E1A17] text-[#3C3633] dark:text-[#FDFBF7] focus:outline-none focus:ring-2 focus:ring-[#8C6D58]">
            </div>

            <div>
                <label class="block font-semibold text-[#6E5B4F] dark:text-[#C4B5A5] mb-1">Kategori / Badge</label>
                <input type="text" id="project-category" required placeholder="Contoh: Web App, Design, Python, ICT"
                       class="w-full px-3.5 py-2.5 rounded-xl border border-[#D8C4B6] dark:border-[#4A4039] bg-[#FDFBF7] dark:bg-[#1E1A17] text-[#3C3633] dark:text-[#FDFBF7] focus:outline-none focus:ring-2 focus:ring-[#8C6D58]">
            </div>

            <div>
                <label class="block font-semibold text-[#6E5B4F] dark:text-[#C4B5A5] mb-1">Link Destination / URL Target (Card Click)</label>
                <input type="url" id="project-url" required placeholder="https://github.com/terryyang/project-name atau https://..."
                       class="w-full px-3.5 py-2.5 rounded-xl border border-[#D8C4B6] dark:border-[#4A4039] bg-[#FDFBF7] dark:bg-[#1E1A17] text-[#3C3633] dark:text-[#FDFBF7] focus:outline-none focus:ring-2 focus:ring-[#8C6D58]">
            </div>

            <!-- Unggah File Gambar Kartu -->
            <div>
                <label class="block font-semibold text-[#6E5B4F] dark:text-[#C4B5A5] mb-1">Gambar Sampul Kartu (Unggah File / URL)</label>
                <div class="space-y-2">
                    <input type="file" id="project-image-file" accept="image/*" onchange="handleImageFileSelect(event)"
                           class="w-full text-xs text-[#786254] dark:text-[#C4B5A5] file:mr-3 file:py-2 file:px-3 file:rounded-xl file:border-0 file:text-xs file:font-semibold file:bg-[#EADBC8] dark:file:bg-[#3D352F] file:text-[#3C3633] dark:file:text-[#FDFBF7] hover:file:bg-[#D9C3AD] dark:hover:file:bg-[#4A4039] cursor-pointer border border-[#D8C4B6] dark:border-[#4A4039] rounded-xl p-1 bg-[#FDFBF7] dark:bg-[#1E1A17]">
                    <input type="url" id="project-image-url" placeholder="Atau tempel URL gambar (https://...)" oninput="handleImageUrlInput(event)"
                           class="w-full px-3.5 py-2.5 rounded-xl border border-[#D8C4B6] dark:border-[#4A4039] bg-[#FDFBF7] dark:bg-[#1E1A17] text-[#3C3633] dark:text-[#FDFBF7] focus:outline-none focus:ring-2 focus:ring-[#8C6D58]">
                </div>
                <!-- Live Preview Gambar -->
                <div id="image-preview-container" class="mt-2.5 hidden">
                    <div class="relative w-full h-32 rounded-2xl overflow-hidden border border-[#D8C4B6] dark:border-[#4A4039] bg-[#F5EFE6] dark:bg-[#2D2723]">
                        <img id="image-preview" src="" class="w-full h-full object-cover" alt="Preview Gambar Proyek">
                        <button type="button" onclick="clearProjectImage()" class="absolute top-2 right-2 bg-[#3C3633]/80 hover:bg-[#3C3633] text-white rounded-full w-6 h-6 text-xs flex items-center justify-center shadow transition-colors" title="Hapus Gambar">✕</button>
                    </div>
                </div>
            </div>

            <div>
                <label class="block font-semibold text-[#6E5B4F] dark:text-[#C4B5A5] mb-1">Deskripsi Proyek</label>
                <textarea id="project-desc" rows="3" required placeholder="Jelaskan ringkas tentang tugas/proyek ini..."
                          class="w-full px-3.5 py-2.5 rounded-xl border border-[#D8C4B6] dark:border-[#4A4039] bg-[#FDFBF7] dark:bg-[#1E1A17] text-[#3C3633] dark:text-[#FDFBF7] focus:outline-none focus:ring-2 focus:ring-[#8C6D58]"></textarea>
            </div>

            <div>
                <label class="block font-semibold text-[#6E5B4F] dark:text-[#C4B5A5] mb-1">Ikon Emoji (Opsional)</label>
                <input type="text" id="project-icon" placeholder="💻 / 🎨 / 📱 / 📊 / 🚀"
                       class="w-full px-3.5 py-2.5 rounded-xl border border-[#D8C4B6] dark:border-[#4A4039] bg-[#FDFBF7] dark:bg-[#1E1A17] text-[#3C3633] dark:text-[#FDFBF7] focus:outline-none focus:ring-2 focus:ring-[#8C6D58]">
            </div>

            <div class="pt-3 flex items-center justify-between">
                <button type="button" id="delete-project-btn" onclick="handleDeleteProject()" class="hidden px-3.5 py-2 bg-red-100 dark:bg-red-950/50 hover:bg-red-200 dark:hover:bg-red-900/60 text-red-700 dark:text-red-300 font-semibold rounded-xl text-xs transition-colors">
                    🗑️ Hapus
                </button>
                <div class="flex items-center gap-2 ml-auto">
                    <button type="button" onclick="closeProjectModal()" class="px-4 py-2 font-medium text-[#786254] dark:text-[#C4B5A5] hover:bg-[#F5EFE6] dark:hover:bg-[#2D2723] rounded-xl">
                        Batal
                    </button>
                    <button type="submit" class="px-5 py-2 bg-[#8C6D58] hover:bg-[#785b47] text-white font-display rounded-xl shadow-sm transition-all">
                        Simpan Proyek
                    </button>
                </div>
            </div>
        </form>
    </div>
</div>

<!-- MODAL 3: Edit Profile & Skills Dialog -->
<div id="profile-modal" class="fixed inset-0 z-50 bg-black/40 dark:bg-black/60 backdrop-blur-sm hidden flex items-center justify-center p-4">
    <div class="bg-[#FFFDF9] dark:bg-[#26211E] border border-[#EADBC8] dark:border-[#3D352F] w-full max-w-md rounded-3xl p-6 soft-shadow space-y-4 max-h-[90vh] overflow-y-auto">
        <div class="flex items-center justify-between border-b border-[#F0E5D8] dark:border-[#3D352F] pb-3">
            <h3 class="font-display text-xl text-[#3C3633] dark:text-[#FDFBF7]">
                ✏️ Edit Profil & Info Terry
            </h3>
            <button onclick="closeProfileModal()" class="text-gray-400 hover:text-gray-600 dark:hover:text-gray-200 text-lg font-bold">
                ✕
            </button>
        </div>

        <form id="profile-form" onsubmit="handleSaveProfile(event)" class="space-y-3 text-xs">
            <div>
                <label class="block font-semibold text-[#6E5B4F] dark:text-[#C4B5A5] mb-1">Nama Lengkap</label>
                <input type="text" id="edit-profile-name" required class="w-full px-3.5 py-2.5 rounded-xl border border-[#D8C4B6] dark:border-[#4A4039] bg-[#FDFBF7] dark:bg-[#1E1A17] text-[#3C3633] dark:text-[#FDFBF7]">
            </div>

            <div>
                <label class="block font-semibold text-[#6E5B4F] dark:text-[#C4B5A5] mb-1">Badge Sekolah / Status</label>
                <input type="text" id="edit-profile-status" required class="w-full px-3.5 py-2.5 rounded-xl border border-[#D8C4B6] dark:border-[#4A4039] bg-[#FDFBF7] dark:bg-[#1E1A17] text-[#3C3633] dark:text-[#FDFBF7]">
            </div>

            <div>
                <label class="block font-semibold text-[#6E5B4F] dark:text-[#C4B5A5] mb-1">Bio Ringkas</label>
                <textarea id="edit-profile-bio" rows="3" required class="w-full px-3.5 py-2.5 rounded-xl border border-[#D8C4B6] dark:border-[#4A4039] bg-[#FDFBF7] dark:bg-[#1E1A17] text-[#3C3633] dark:text-[#FDFBF7]"></textarea>
            </div>

            <div>
                <label class="block font-semibold text-[#6E5B4F] dark:text-[#C4B5A5] mb-1">URL Avatar / Foto Profil</label>
                <input type="url" id="edit-profile-avatar" required class="w-full px-3.5 py-2.5 rounded-xl border border-[#D8C4B6] dark:border-[#4A4039] bg-[#FDFBF7] dark:bg-[#1E1A17] text-[#3C3633] dark:text-[#FDFBF7]">
            </div>

            <div>
                <label class="block font-semibold text-[#6E5B4F] dark:text-[#C4B5A5] mb-1">Daftar Keahlian (Pisahkan dengan koma)</label>
                <input type="text" id="edit-profile-skills" placeholder="💻 HTML & CSS, 📱 Mobile Layout, 🎨 Visual Design" class="w-full px-3.5 py-2.5 rounded-xl border border-[#D8C4B6] dark:border-[#4A4039] bg-[#FDFBF7] dark:bg-[#1E1A17] text-[#3C3633] dark:text-[#FDFBF7]">
            </div>

            <!-- Tautan Media Sosial -->
            <div class="border-t border-[#F0E5D8] dark:border-[#3D352F] pt-3 space-y-2">
                <label class="block font-semibold text-[#6E5B4F] dark:text-[#C4B5A5]">Tautan Media Sosial (Footer)</label>
                <div class="grid grid-cols-1 gap-2 text-xs">
                    <div>
                        <span class="text-[#786254] dark:text-[#C4B5A5] font-medium">GitHub:</span>
                        <input type="url" id="edit-social-github" placeholder="https://github.com/username" class="w-full px-3 py-2 rounded-xl border border-[#D8C4B6] dark:border-[#4A4039] bg-[#FDFBF7] dark:bg-[#1E1A17] text-[#3C3633] dark:text-[#FDFBF7] mt-0.5">
                    </div>
                    <div>
                        <span class="text-[#786254] dark:text-[#C4B5A5] font-medium">Instagram:</span>
                        <input type="url" id="edit-social-instagram" placeholder="https://instagram.com/username" class="w-full px-3 py-2 rounded-xl border border-[#D8C4B6] dark:border-[#4A4039] bg-[#FDFBF7] dark:bg-[#1E1A17] text-[#3C3633] dark:text-[#FDFBF7] mt-0.5">
                    </div>
                    <div>
                        <span class="text-[#786254] dark:text-[#C4B5A5] font-medium">YouTube:</span>
                        <input type="url" id="edit-social-youtube" placeholder="https://youtube.com/@channel" class="w-full px-3 py-2 rounded-xl border border-[#D8C4B6] dark:border-[#4A4039] bg-[#FDFBF7] dark:bg-[#1E1A17] text-[#3C3633] dark:text-[#FDFBF7] mt-0.5">
                    </div>
                    <div>
                        <span class="text-[#786254] dark:text-[#C4B5A5] font-medium">TikTok:</span>
                        <input type="url" id="edit-social-tiktok" placeholder="https://tiktok.com/@username" class="w-full px-3 py-2 rounded-xl border border-[#D8C4B6] dark:border-[#4A4039] bg-[#FDFBF7] dark:bg-[#1E1A17] text-[#3C3633] dark:text-[#FDFBF7] mt-0.5">
                    </div>
                    <div>
                        <span class="text-[#786254] dark:text-[#C4B5A5] font-medium">LinkedIn:</span>
                        <input type="url" id="edit-social-linkedin" placeholder="https://linkedin.com/in/username" class="w-full px-3 py-2 rounded-xl border border-[#D8C4B6] dark:border-[#4A4039] bg-[#FDFBF7] dark:bg-[#1E1A17] text-[#3C3633] dark:text-[#FDFBF7] mt-0.5">
                    </div>
                </div>
            </div>

            <div class="pt-3 flex items-center justify-end gap-2">
                <button type="button" onclick="closeProfileModal()" class="px-4 py-2 font-medium text-[#786254] dark:text-[#C4B5A5] hover:bg-[#F5EFE6] dark:hover:bg-[#2D2723] rounded-xl">
                    Batal
                </button>
                <button type="submit" class="px-5 py-2 bg-[#8C6D58] hover:bg-[#785b47] text-white font-display rounded-xl shadow-sm transition-all">
                    Simpan Perubahan Profil
                </button>
            </div>
        </form>
    </div>
</div>

<!-- MODAL 4: Admin Credentials Change Dialog -->
<div id="admin-cred-modal" class="fixed inset-0 z-50 bg-black/40 dark:bg-black/60 backdrop-blur-sm hidden flex items-center justify-center p-4">
    <div class="bg-[#FFFDF9] dark:bg-[#26211E] border border-[#EADBC8] dark:border-[#3D352F] w-full max-w-sm rounded-3xl p-6 soft-shadow space-y-4">
        <div class="flex items-center justify-between border-b border-[#F0E5D8] dark:border-[#3D352F] pb-3">
            <h3 class="font-display text-xl text-[#3C3633] dark:text-[#FDFBF7] flex items-center gap-2">
                🔑 Pengaturan Akun Admin
            </h3>
            <button onclick="closeAdminCredModal()" class="text-gray-400 hover:text-gray-600 dark:hover:text-gray-200 text-lg font-bold">
                ✕
            </button>
        </div>

        <p class="text-xs text-[#786254] dark:text-[#C4B5A5]">Ubah username dan password admin. Password baru akan langsung di-hash menggunakan SHA-256 dan disimpan ke LocalStorage.</p>

        <div id="cred-error" class="hidden bg-red-50 dark:bg-red-950/40 border border-red-200 dark:border-red-900/50 text-red-600 dark:text-red-300 text-xs p-3 rounded-xl font-medium leading-relaxed">
            Pesan kesalahan kredensial
        </div>

        <form id="admin-cred-form" onsubmit="handleSaveAdminCreds(event)" class="space-y-3 text-xs">
            <div>
                <label class="block font-semibold text-[#6E5B4F] dark:text-[#C4B5A5] mb-1">Username Admin Baru</label>
                <input type="text" id="edit-admin-username" required placeholder="Username baru" autocomplete="username"
                       class="w-full px-3.5 py-2.5 rounded-xl border border-[#D8C4B6] dark:border-[#4A4039] bg-[#FDFBF7] dark:bg-[#1E1A17] text-[#3C3633] dark:text-[#FDFBF7] focus:outline-none focus:ring-2 focus:ring-[#8C6D58]">
            </div>

            <div>
                <label class="block font-semibold text-[#6E5B4F] dark:text-[#C4B5A5] mb-1">Password Baru (Min. 8 karakter)</label>
                <div class="relative">
                    <input type="password" id="edit-admin-password" required placeholder="Password baru" oninput="checkPasswordStrength(this.value)" autocomplete="new-password"
                           class="w-full px-3.5 py-2.5 pr-10 rounded-xl border border-[#D8C4B6] dark:border-[#4A4039] bg-[#FDFBF7] dark:bg-[#1E1A17] text-[#3C3633] dark:text-[#FDFBF7] focus:outline-none focus:ring-2 focus:ring-[#8C6D58]">
                    <button type="button" onclick="togglePasswordVisibility('edit-admin-password', this)" class="absolute right-3 top-1/2 -translate-y-1/2 text-gray-400 hover:text-gray-600 dark:hover:text-gray-200 text-sm">
                        👁️
                    </button>
                </div>

                <!-- Password Strength Bar -->
                <div class="mt-2 space-y-1">
                    <div class="h-1.5 w-full bg-[#EADBC8] dark:bg-[#3D352F] rounded-full overflow-hidden">
                        <div id="pwd-strength-bar" class="h-full w-0 transition-all duration-300 bg-red-500"></div>
                    </div>
                    <div class="flex items-center justify-between text-[10px] text-[#8C7A6B] dark:text-[#A89889]">
                        <span>Kekuatan Password: <b id="pwd-strength-text" class="text-red-500">Sangat Lemah</b></span>
                        <span>Minimal 8 karakter & angka</span>
                    </div>
                </div>
            </div>

            <div>
                <label class="block font-semibold text-[#6E5B4F] dark:text-[#C4B5A5] mb-1">Konfirmasi Password Baru</label>
                <input type="password" id="edit-admin-confirm-password" required placeholder="Ulangi password baru" autocomplete="new-password"
                       class="w-full px-3.5 py-2.5 rounded-xl border border-[#D8C4B6] dark:border-[#4A4039] bg-[#FDFBF7] dark:bg-[#1E1A17] text-[#3C3633] dark:text-[#FDFBF7] focus:outline-none focus:ring-2 focus:ring-[#8C6D58]">
            </div>

            <div class="pt-2 flex items-center justify-end gap-2">
                <button type="button" onclick="closeAdminCredModal()" class="px-4 py-2 font-medium text-[#786254] dark:text-[#C4B5A5] hover:bg-[#F5EFE6] dark:hover:bg-[#2D2723] rounded-xl">
                    Batal
                </button>
                <button type="submit" class="px-5 py-2 bg-[#8C6D58] hover:bg-[#785b47] text-white font-display rounded-xl shadow-sm transition-all">
                    Simpan Password Baru
                </button>
            </div>
        </form>
    </div>
</div>

<!-- Notification Toast Container -->
<div id="toast-msg" class="fixed bottom-5 left-1/2 -translate-x-1/2 z-50 bg-[#3C3633] dark:bg-[#FDFBF7] text-[#FFFDF9] dark:text-[#3C3633] text-xs font-semibold px-4 py-2.5 rounded-full shadow-lg transition-all transform opacity-0 translate-y-4 pointer-events-none">
    Pesan Notifikasi
</div>

<!-- Core JavaScript Application Logic with LocalStorage -->
<script>
    // Storage Keys for LocalStorage
    const STORAGE_KEY_PROFILE = "terry_portfolio_profile_v1";
    const STORAGE_KEY_PROJECTS = "terry_portfolio_projects_v1";
    const STORAGE_KEY_CREDS = "terry_portfolio_creds_v1";
    const STORAGE_KEY_ADMIN_SESSION = "terry_portfolio_admin_logged_in";

    // Global Security Salt & Web Crypto Hashing
    const SECURITY_SALT = "TerryYang_ICT_2026_SecureSalt_MB2!";
    const MAX_FAILED_ATTEMPTS = 5;
    const LOCKOUT_DURATION_MS = 5 * 60 * 1000; // 5 Menit lockout
    const INACTIVITY_TIMEOUT_MS = 15 * 60 * 1000; // 15 Menit auto-logout

    async function hashText(plainText) {
        if (!plainText) return "";
        const encoder = new TextEncoder();
        const data = encoder.encode(plainText + SECURITY_SALT);
        const hashBuffer = await crypto.subtle.digest('SHA-256', data);
        const hashArray = Array.from(new Uint8Array(hashBuffer));
        return hashArray.map(b => b.toString(16).padStart(2, '0')).join('');
    }

    let isAdminLoggedIn = false;
    let lockoutTimerInterval = null;
    let inactivityTimer = null;

    // Default Data Fallbacks
    const DEFAULT_PROFILE = {
        name: "Halo, Saya Terry Yang 👋",
        statusBadge: "Mutiara Bangsa 2 School • Kelas ICT",
        bio: "Siswa Mutiara Bangsa 2 School yang antusias mengeksplorasi dunia ICT, pemrograman web, dan teknologi visual digital.",
        avatarUrl: "https://placehold.co/200x200/E8DFCA/6E5B4F?text=Terry+Y",
        skills: [
            "💻 HTML & CSS",
            "📱 Mobile-First Layout",
            "🎨 Visual & Graphic Design",
            "📊 Presentasi & Data ICT",
            "🧩 Logic & Algoritma"
        ],
        socials: {
            github: "https://github.com",
            instagram: "https://instagram.com",
            youtube: "https://youtube.com",
            tiktok: "https://tiktok.com",
            linkedin: "https://linkedin.com"
        }
    };

    const DEFAULT_PROJECTS = [
        {
            id: "proj_1",
            title: "Landing Page Profil Mobile",
            category: "Web Project",
            url: "https://github.com/terryyang/landing-page",
            desc: "Desain portofolio berbasis HTML & Tailwind CSS tanpa JavaScript dengan fokus tampilan mobile yang responsif.",
            icon: "📱"
        },
        {
            id: "proj_2",
            title: "Presentasi & Grafis Digital",
            category: "Design & Media",
            url: "https://canva.com",
            desc: "Kumpulan tugas desain visual, infografis, dan materi presentasi interaktif untuk pembelajaran komputer Mutiara Bangsa 2.",
            icon: "🎨"
        }
    ];

    let stateProfile = { ...DEFAULT_PROFILE };
    let stateProjects = [...DEFAULT_PROJECTS];
    let adminCreds = { usernameHash: "", passwordHash: "" };
    window.currentProjectImageData = "";

    // Initialize Data from LocalStorage
    async function loadLocalStorageData() {
        // 1. Load Admin Credentials
        const savedCreds = localStorage.getItem(STORAGE_KEY_CREDS);
        if (savedCreds) {
            try {
                adminCreds = JSON.parse(savedCreds);
            } catch (e) {
                console.error("Error parsing saved creds:", e);
            }
        }
        
        if (!adminCreds.usernameHash || !adminCreds.passwordHash) {
            adminCreds = {
                usernameHash: await hashText("admin"),
                passwordHash: await hashText("admin123")
            };
            localStorage.setItem(STORAGE_KEY_CREDS, JSON.stringify(adminCreds));
        }

        // 2. Load Profile Data
        const savedProfile = localStorage.getItem(STORAGE_KEY_PROFILE);
        if (savedProfile) {
            try {
                stateProfile = { ...DEFAULT_PROFILE, ...JSON.parse(savedProfile) };
            } catch (e) {
                console.error("Error parsing saved profile:", e);
                stateProfile = { ...DEFAULT_PROFILE };
            }
        } else {
            stateProfile = { ...DEFAULT_PROFILE };
            localStorage.setItem(STORAGE_KEY_PROFILE, JSON.stringify(stateProfile));
        }

        // 3. Load Projects Data
        const savedProjects = localStorage.getItem(STORAGE_KEY_PROJECTS);
        if (savedProjects) {
            try {
                stateProjects = JSON.parse(savedProjects);
            } catch (e) {
                console.error("Error parsing saved projects:", e);
                stateProjects = [...DEFAULT_PROJECTS];
            }
        } else {
            stateProjects = [...DEFAULT_PROJECTS];
            localStorage.setItem(STORAGE_KEY_PROJECTS, JSON.stringify(stateProjects));
        }

        // 4. Load Admin Session Active state
        const savedAdminSession = sessionStorage.getItem(STORAGE_KEY_ADMIN_SESSION);
        if (savedAdminSession === 'true') {
            isAdminLoggedIn = true;
            resetInactivityTimer();
        }

        renderProfileUI();
        renderProjectsUI();
        updateAdminViewUI();
    }

    function renderProfileUI() {
        document.getElementById('display-name').textContent = stateProfile.name || DEFAULT_PROFILE.name;
        document.getElementById('nav-header-name').textContent = (stateProfile.name || 'Terry Yang').replace('Halo, Saya ', '').replace(' 👋', '');
        document.getElementById('display-status-badge').textContent = stateProfile.statusBadge || DEFAULT_PROFILE.statusBadge;
        document.getElementById('display-bio').textContent = stateProfile.bio || DEFAULT_PROFILE.bio;
        document.getElementById('display-avatar').src = stateProfile.avatarUrl || DEFAULT_PROFILE.avatarUrl;

        // Render Skills
        const skillsContainer = document.getElementById('skills-container');
        skillsContainer.innerHTML = '';
        const skillsList = Array.isArray(stateProfile.skills) ? stateProfile.skills : DEFAULT_PROFILE.skills;
        skillsList.forEach(skill => {
            const badge = document.createElement('span');
            badge.className = "px-3 py-1.5 rounded-xl bg-[#F5EFE6] dark:bg-[#2D2723] text-[#6E5B4F] dark:text-[#EADBC8] text-xs font-medium border border-[#EADBC8] dark:border-[#3D352F]";
            badge.textContent = skill;
            skillsContainer.appendChild(badge);
        });

        // Render Social Links
        const socials = { ...DEFAULT_PROFILE.socials, ...(stateProfile.socials || {}) };
        if (document.getElementById('footer-github')) document.getElementById('footer-github').href = socials.github || '#';
        if (document.getElementById('footer-instagram')) document.getElementById('footer-instagram').href = socials.instagram || '#';
        if (document.getElementById('footer-youtube')) document.getElementById('footer-youtube').href = socials.youtube || '#';
        if (document.getElementById('footer-tiktok')) document.getElementById('footer-tiktok').href = socials.tiktok || '#';
        if (document.getElementById('footer-linkedin')) document.getElementById('footer-linkedin').href = socials.linkedin || '#';
    }

    function renderProjectsUI() {
        const container = document.getElementById('projects-list-container');
        document.getElementById('stat-projects-count').textContent = stateProjects.length;

        if (stateProjects.length === 0) {
            container.innerHTML = `
                <div class="bg-[#FFFDF9] dark:bg-[#26211E] border border-[#F0E5D8] dark:border-[#3D352F] rounded-3xl p-6 text-center text-xs text-[#8C7A6B] dark:text-[#A89889]">
                    Belum ada proyek yang ditambahkan. Login sebagai Admin untuk menambahkan proyek baru!
                </div>
            `;
            return;
        }

        container.innerHTML = '';

        stateProjects.forEach(proj => {
            const card = document.createElement('article');
            card.className = "bg-[#FFFDF9] dark:bg-[#26211E] border border-[#F0E5D8] dark:border-[#3D352F] rounded-3xl overflow-hidden soft-shadow soft-shadow-hover relative transition-colors";
            
            const iconEmoji = proj.icon || '💻';
            const hasImage = Boolean(proj.imageUrl);

            const cardHeaderHtml = hasImage 
                ? `<div class="h-44 bg-[#F5EFE6] dark:bg-[#2D2723] relative overflow-hidden">
                    <img src="${escapeHtml(proj.imageUrl)}" alt="${escapeHtml(proj.title)}" class="w-full h-full object-cover" onerror="this.style.display='none'; this.nextElementSibling.style.display='flex';">
                    <div class="w-full h-full items-center justify-center bg-[#F5EFE6] dark:bg-[#2D2723]" style="display:none;">
                        <span class="text-5xl select-none">${iconEmoji}</span>
                    </div>
                   </div>`
                : `<div class="h-36 bg-[#F5EFE6] dark:bg-[#2D2723] flex items-center justify-center relative overflow-hidden">
                    <span class="text-5xl select-none">${iconEmoji}</span>
                   </div>`;

            card.innerHTML = `
                <div class="relative">
                    ${cardHeaderHtml}
                    <span class="absolute top-3 right-3 bg-[#FFFDF9]/95 dark:bg-[#26211E]/95 backdrop-blur-sm text-[#786254] dark:text-[#C4B5A5] text-[10px] font-semibold px-2.5 py-1 rounded-full border border-[#EADBC8] dark:border-[#3D352F] shadow-sm z-10">
                        ${escapeHtml(proj.category || 'ICT Project')}
                    </span>
                    ${isAdminLoggedIn ? `
                        <button onclick="openEditProjectModal('${proj.id}')" class="absolute top-3 left-3 bg-[#8C6D58] text-white text-[11px] font-semibold px-2.5 py-1 rounded-full shadow hover:bg-[#785b47] transition-all z-10">
                            ✏️ Edit Card
                        </button>
                    ` : ''}
                </div>
                <div class="p-5 space-y-2">
                    <h3 class="font-display text-lg text-[#3C3633] dark:text-[#FDFBF7]">${escapeHtml(proj.title)}</h3>
                    <p class="text-xs text-[#786254] dark:text-[#C4B5A5] leading-relaxed">${escapeHtml(proj.desc)}</p>
                    
                    <div class="pt-2 flex items-center justify-between text-xs">
                        <span class="text-[#8C7A6B] dark:text-[#A89889] font-medium">Mutiara Bangsa 2 ICT</span>
                        <a href="${escapeHtml(proj.url || '#')}" target="_blank" rel="noopener noreferrer" 
                           class="font-display bg-[#EADBC8] dark:bg-[#3D352F] hover:bg-[#D9C3AD] dark:hover:bg-[#4A4039] text-[#3C3633] dark:text-[#FDFBF7] px-3 py-1.5 rounded-xl border border-[#D8C4B6] dark:border-[#4A4039] flex items-center gap-1 transition-colors">
                            <span>Buka Link</span> ➔
                        </a>
                    </div>
                </div>
            `;
            container.appendChild(card);
        });
    }

    // Helper escape HTML
    function escapeHtml(str) {
        return String(str || '').replace(/&/g, '&amp;').replace(/</g, '&lt;').replace(/>/g, '&gt;').replace(/"/g, '&quot;');
    }

    // --- SECURITY: Rate Limiting & Lockout Utilities ---
    function checkLockoutStatus() {
        const lockoutUntil = parseInt(localStorage.getItem('admin_lockout_until') || '0', 10);
        const now = Date.now();
        if (now < lockoutUntil) {
            const remainingSec = Math.ceil((lockoutUntil - now) / 1000);
            return { locked: true, remainingSec };
        }
        return { locked: false, remainingSec: 0 };
    }

    function recordFailedAttempt() {
        let attempts = parseInt(localStorage.getItem('admin_failed_attempts') || '0', 10) + 1;
        localStorage.setItem('admin_failed_attempts', attempts.toString());

        if (attempts >= MAX_FAILED_ATTEMPTS) {
            const lockoutUntil = Date.now() + LOCKOUT_DURATION_MS;
            localStorage.setItem('admin_lockout_until', lockoutUntil.toString());
            localStorage.setItem('admin_failed_attempts', '0');
            return { locked: true, remainingSec: Math.ceil(LOCKOUT_DURATION_MS / 1000) };
        }
        return { locked: false, attemptsLeft: MAX_FAILED_ATTEMPTS - attempts };
    }

    function clearFailedAttempts() {
        localStorage.removeItem('admin_failed_attempts');
        localStorage.removeItem('admin_lockout_until');
    }

    function updateLockoutUI() {
        const status = checkLockoutStatus();
        const lockoutNotice = document.getElementById('lockout-notice');
        const loginError = document.getElementById('login-error');
        const submitBtn = document.getElementById('login-submit-btn');
        const timerText = document.getElementById('lockout-timer-text');

        if (status.locked) {
            lockoutNotice.classList.remove('hidden');
            loginError.classList.add('hidden');
            submitBtn.disabled = true;
            timerText.textContent = `Sistem dikunci demi keamanan karena 5x kesalahan. Coba lagi dalam ${status.remainingSec} detik.`;

            if (!lockoutTimerInterval) {
                lockoutTimerInterval = setInterval(() => {
                    updateLockoutUI();
                }, 1000);
            }
        } else {
            if (lockoutTimerInterval) {
                clearInterval(lockoutTimerInterval);
                lockoutTimerInterval = null;
            }
            lockoutNotice.classList.add('hidden');
            submitBtn.disabled = false;
        }
    }

    // --- SECURITY: Session Inactivity Timer ---
    function resetInactivityTimer() {
        if (!isAdminLoggedIn) return;
        clearTimeout(inactivityTimer);
        inactivityTimer = setTimeout(() => {
            logoutAdmin();
            showToast("🔒 Sesi berakhir karena 15 menit tidak ada aktivitas.");
        }, INACTIVITY_TIMEOUT_MS);
    }

    ['mousemove', 'keydown', 'click', 'scroll', 'touchstart'].forEach(evt => {
        window.addEventListener(evt, resetInactivityTimer, { passive: true });
    });

    // Toggle Password Visibility Eye Button
    window.togglePasswordVisibility = function(inputId, btnEl) {
        const input = document.getElementById(inputId);
        if (!input) return;
        if (input.type === 'password') {
            input.type = 'text';
            btnEl.textContent = '🙈';
        } else {
            input.type = 'password';
            btnEl.textContent = '👁️';
        }
    };

    // Modal Open / Close Handlers
    window.openAdminModal = function() {
        if (isAdminLoggedIn) {
            openProfileEditModal();
        } else {
            document.getElementById('login-modal').classList.remove('hidden');
            document.getElementById('login-error').classList.add('hidden');
            document.getElementById('admin-password').value = "";
            updateLockoutUI();
        }
    };

    window.closeAdminModal = function() {
        document.getElementById('login-modal').classList.add('hidden');
        if (lockoutTimerInterval) {
            clearInterval(lockoutTimerInterval);
            lockoutTimerInterval = null;
        }
    };

    window.handleAdminLogin = async function(e) {
        e.preventDefault();
        const status = checkLockoutStatus();
        if (status.locked) {
            updateLockoutUI();
            return;
        }

        const userInp = document.getElementById('admin-username').value.trim();
        const passInp = document.getElementById('admin-password').value.trim();

        const inputUserHash = await hashText(userInp);
        const inputPassHash = await hashText(passInp);

        if (inputUserHash === adminCreds.usernameHash && inputPassHash === adminCreds.passwordHash) {
            clearFailedAttempts();
            isAdminLoggedIn = true;
            sessionStorage.setItem(STORAGE_KEY_ADMIN_SESSION, 'true');
            closeAdminModal();
            updateAdminViewUI();
            resetInactivityTimer();
            showToast("🛡️ Autentikasi Admin berhasil! Selamat datang, Terry.");
        } else {
            const failResult = recordFailedAttempt();
            const loginError = document.getElementById('login-error');

            if (failResult.locked) {
                updateLockoutUI();
                showToast("⛔ Sesi terblokir sementara karena kesalahan berturut-turut!");
            } else {
                loginError.textContent = `Username atau Password salah! Sisa percobaan: ${failResult.attemptsLeft}x`;
                loginError.classList.remove('hidden');
            }
        }
    };

    // Admin Credentials Modal Handlers
    window.openAdminCredModal = function() {
        if (!isAdminLoggedIn) return;
        document.getElementById('edit-admin-username').value = "";
        document.getElementById('edit-admin-password').value = "";
        document.getElementById('edit-admin-confirm-password').value = "";
        document.getElementById('cred-error').classList.add('hidden');
        checkPasswordStrength("");
        document.getElementById('admin-cred-modal').classList.remove('hidden');
    };

    window.closeAdminCredModal = function() {
        document.getElementById('admin-cred-modal').classList.add('hidden');
    };

    window.checkPasswordStrength = function(password) {
        const bar = document.getElementById('pwd-strength-bar');
        const text = document.getElementById('pwd-strength-text');

        if (!bar || !text) return;

        let score = 0;
        if (password.length >= 8) score++;
        if (/[A-Z]/.test(password) || /[a-z]/.test(password)) score++;
        if (/[0-9]/.test(password)) score++;
        if (/[^A-Za-z0-9]/.test(password)) score++;

        if (password.length < 8) {
            bar.style.width = '25%';
            bar.className = 'h-full bg-red-500 transition-all duration-300';
            text.textContent = 'Sangat Lemah (Min. 8 Karakter)';
            text.className = 'text-red-500 font-bold';
        } else if (score <= 2) {
            bar.style.width = '50%';
            bar.className = 'h-full bg-amber-500 transition-all duration-300';
            text.textContent = 'Sedang (Tambahkan Angka/Simbol)';
            text.className = 'text-amber-500 font-bold';
        } else if (score >= 3) {
            bar.style.width = '100%';
            bar.className = 'h-full bg-emerald-500 transition-all duration-300';
            text.textContent = 'Kuat & Aman ✨';
            text.className = 'text-emerald-500 font-bold';
        }
    };

    window.handleSaveAdminCreds = async function(e) {
        e.preventDefault();
        const newUsername = document.getElementById('edit-admin-username').value.trim();
        const newPassword = document.getElementById('edit-admin-password').value.trim();
        const confirmPassword = document.getElementById('edit-admin-confirm-password').value.trim();
        const credError = document.getElementById('cred-error');

        credError.classList.add('hidden');

        if (!newUsername || !newPassword) {
            credError.textContent = "Username dan Password tidak boleh kosong!";
            credError.classList.remove('hidden');
            return;
        }

        if (newPassword.length < 8) {
            credError.textContent = "Password baru harus memiliki minimal 8 karakter demi keamanan!";
            credError.classList.remove('hidden');
            return;
        }

        if (newPassword !== confirmPassword) {
            credError.textContent = "Konfirmasi password tidak cocok!";
            credError.classList.remove('hidden');
            return;
        }

        adminCreds = {
            usernameHash: await hashText(newUsername),
            passwordHash: await hashText(newPassword)
        };

        localStorage.setItem(STORAGE_KEY_CREDS, JSON.stringify(adminCreds));

        showToast("🔑 Kredensial Admin berhasil diperbarui dan disimpan di LocalStorage!");
        closeAdminCredModal();
    };

    window.logoutAdmin = function() {
        isAdminLoggedIn = false;
        sessionStorage.removeItem(STORAGE_KEY_ADMIN_SESSION);
        clearTimeout(inactivityTimer);
        updateAdminViewUI();
        showToast("🔒 Telah keluar dari Mode Admin.");
    };

    function updateAdminViewUI() {
        const adminBanner = document.getElementById('admin-banner');
        const adminIcon = document.getElementById('admin-icon');
        const adminBtnText = document.getElementById('admin-btn-text');
        const adminOnlyElements = document.querySelectorAll('.admin-only');

        if (isAdminLoggedIn) {
            adminBanner.classList.remove('hidden');
            adminIcon.textContent = "⚙️";
            adminBtnText.textContent = "Kelola";
            adminOnlyElements.forEach(el => el.classList.remove('hidden'));
        } else {
            adminBanner.classList.add('hidden');
            adminIcon.textContent = "🔒";
            adminBtnText.textContent = "Admin";
            adminOnlyElements.forEach(el => el.classList.add('hidden'));
        }
        renderProjectsUI();
    }

    // Manage Project Modal
    window.openAddProjectModal = function() {
        if (!isAdminLoggedIn) return;
        document.getElementById('project-modal-title').textContent = "➕ Tambah Proyek ICT Baru";
        document.getElementById('project-id').value = "";
        document.getElementById('project-title').value = "";
        document.getElementById('project-category').value = "Web Project";
        document.getElementById('project-url').value = "https://";
        document.getElementById('project-desc').value = "";
        document.getElementById('project-icon').value = "💻";
        document.getElementById('project-image-url').value = "";
        document.getElementById('project-image-file').value = "";
        clearProjectImage();
        document.getElementById('delete-project-btn').classList.add('hidden');
        document.getElementById('project-modal').classList.remove('hidden');
    };

    window.openEditProjectModal = function(id) {
        if (!isAdminLoggedIn) return;
        const proj = stateProjects.find(p => p.id === id);
        if (!proj) return;

        document.getElementById('project-modal-title').textContent = "✏️ Edit Card Proyek & Link";
        document.getElementById('project-id').value = proj.id;
        document.getElementById('project-title').value = proj.title || "";
        document.getElementById('project-category').value = proj.category || "";
        document.getElementById('project-url').value = proj.url || "";
        document.getElementById('project-desc').value = proj.desc || "";
        document.getElementById('project-icon').value = proj.icon || "💻";
        document.getElementById('project-image-file').value = "";

        if (proj.imageUrl) {
            window.currentProjectImageData = proj.imageUrl;
            document.getElementById('image-preview').src = proj.imageUrl;
            document.getElementById('image-preview-container').classList.remove('hidden');
            if (proj.imageUrl.startsWith('http')) {
                document.getElementById('project-image-url').value = proj.imageUrl;
            } else {
                document.getElementById('project-image-url').value = "";
            }
        } else {
            clearProjectImage();
        }

        document.getElementById('delete-project-btn').classList.remove('hidden');
        document.getElementById('project-modal').classList.remove('hidden');
    };

    window.handleImageFileSelect = function(e) {
        const file = e.target.files[0];
        if (!file) return;

        const reader = new FileReader();
        reader.onload = function(event) {
            const img = new Image();
            img.onload = function() {
                const canvas = document.createElement('canvas');
                let width = img.width;
                let height = img.height;
                const MAX_DIM = 600;
                
                if (width > height && width > MAX_DIM) {
                    height = Math.round((height * MAX_DIM) / width);
                    width = MAX_DIM;
                } else if (height > MAX_DIM) {
                    width = Math.round((width * MAX_DIM) / height);
                    height = MAX_DIM;
                }

                canvas.width = width;
                canvas.height = height;
                const ctx = canvas.getContext('2d');
                ctx.drawImage(img, 0, 0, width, height);

                const compressedUrl = canvas.toDataURL('image/jpeg', 0.85);
                window.currentProjectImageData = compressedUrl;
                document.getElementById('image-preview').src = compressedUrl;
                document.getElementById('image-preview-container').classList.remove('hidden');
                document.getElementById('project-image-url').value = "";
            };
            img.src = event.target.result;
        };
        reader.readAsDataURL(file);
    };

    window.handleImageUrlInput = function(e) {
        const url = e.target.value.trim();
        if (url) {
            window.currentProjectImageData = url;
            document.getElementById('image-preview').src = url;
            document.getElementById('image-preview-container').classList.remove('hidden');
        } else {
            clearProjectImage();
        }
    };

    window.clearProjectImage = function() {
        window.currentProjectImageData = "";
        document.getElementById('project-image-url').value = "";
        document.getElementById('project-image-file').value = "";
        document.getElementById('image-preview').src = "";
        document.getElementById('image-preview-container').classList.add('hidden');
    };

    window.closeProjectModal = function() {
        document.getElementById('project-modal').classList.add('hidden');
    };

    window.handleSaveProject = function(e) {
        e.preventDefault();
        const projId = document.getElementById('project-id').value;
        const projectData = {
            title: document.getElementById('project-title').value.trim(),
            category: document.getElementById('project-category').value.trim(),
            url: document.getElementById('project-url').value.trim(),
            desc: document.getElementById('project-desc').value.trim(),
            icon: document.getElementById('project-icon').value.trim() || "💻",
            imageUrl: window.currentProjectImageData || document.getElementById('project-image-url').value.trim() || ""
        };

        if (projId) {
            const idx = stateProjects.findIndex(p => p.id === projId);
            if (idx !== -1) stateProjects[idx] = { id: projId, ...projectData };
        } else {
            stateProjects.push({ id: 'proj_' + Date.now(), ...projectData });
        }

        // Save to LocalStorage
        localStorage.setItem(STORAGE_KEY_PROJECTS, JSON.stringify(stateProjects));
        renderProjectsUI();

        showToast("🎉 Data proyek & gambar berhasil disimpan ke LocalStorage!");
        closeProjectModal();
    };

    window.handleDeleteProject = function() {
        const projId = document.getElementById('project-id').value;
        if (!projId) return;

        stateProjects = stateProjects.filter(p => p.id !== projId);
        
        // Save to LocalStorage
        localStorage.setItem(STORAGE_KEY_PROJECTS, JSON.stringify(stateProjects));
        renderProjectsUI();

        showToast("🗑️ Proyek telah dihapus.");
        closeProjectModal();
    };

    // Profile Edit Modal
    window.openProfileEditModal = function() {
        if (!isAdminLoggedIn) return;
        document.getElementById('edit-profile-name').value = stateProfile.name || "";
        document.getElementById('edit-profile-status').value = stateProfile.statusBadge || "";
        document.getElementById('edit-profile-bio').value = stateProfile.bio || "";
        document.getElementById('edit-profile-avatar').value = stateProfile.avatarUrl || "";
        document.getElementById('edit-profile-skills').value = (stateProfile.skills || []).join(', ');

        const socials = { ...DEFAULT_PROFILE.socials, ...(stateProfile.socials || {}) };
        document.getElementById('edit-social-github').value = socials.github || "";
        document.getElementById('edit-social-instagram').value = socials.instagram || "";
        document.getElementById('edit-social-youtube').value = socials.youtube || "";
        document.getElementById('edit-social-tiktok').value = socials.tiktok || "";
        document.getElementById('edit-social-linkedin').value = socials.linkedin || "";

        document.getElementById('profile-modal').classList.remove('hidden');
    };

    window.closeProfileModal = function() {
        document.getElementById('profile-modal').classList.add('hidden');
    };

    window.handleSaveProfile = function(e) {
        e.preventDefault();
        const skillsRaw = document.getElementById('edit-profile-skills').value;
        const updatedProfile = {
            name: document.getElementById('edit-profile-name').value.trim(),
            statusBadge: document.getElementById('edit-profile-status').value.trim(),
            bio: document.getElementById('edit-profile-bio').value.trim(),
            avatarUrl: document.getElementById('edit-profile-avatar').value.trim(),
            skills: skillsRaw.split(',').map(s => s.trim()).filter(Boolean),
            socials: {
                github: document.getElementById('edit-social-github').value.trim() || DEFAULT_PROFILE.socials.github,
                instagram: document.getElementById('edit-social-instagram').value.trim() || DEFAULT_PROFILE.socials.instagram,
                youtube: document.getElementById('edit-social-youtube').value.trim() || DEFAULT_PROFILE.socials.youtube,
                tiktok: document.getElementById('edit-social-tiktok').value.trim() || DEFAULT_PROFILE.socials.tiktok,
                linkedin: document.getElementById('edit-social-linkedin').value.trim() || DEFAULT_PROFILE.socials.linkedin
            }
        };

        stateProfile = updatedProfile;
        
        // Save to LocalStorage
        localStorage.setItem(STORAGE_KEY_PROFILE, JSON.stringify(stateProfile));
        renderProfileUI();

        showToast("✨ Informasi profil & media sosial berhasil diperbarui dan disimpan!");
        closeProfileModal();
    };

    function showToast(message) {
        const toast = document.getElementById('toast-msg');
        toast.textContent = message;
        toast.classList.remove('opacity-0', 'translate-y-4');
        toast.classList.add('opacity-100', 'translate-y-0');
        setTimeout(() => {
            toast.classList.remove('opacity-100', 'translate-y-0');
            toast.classList.add('opacity-0', 'translate-y-4');
        }, 3000);
    }

    // Dark Mode Logic
    window.toggleDarkMode = function() {
        const html = document.documentElement;
        const themeIcon = document.getElementById('theme-icon');
        
        if (html.classList.contains('dark')) {
            html.classList.remove('dark');
            localStorage.setItem('theme', 'light');
            if (themeIcon) themeIcon.textContent = '🌙';
            showToast("☀️ Mode Terang diaktifkan");
        } else {
            html.classList.add('dark');
            localStorage.setItem('theme', 'dark');
            if (themeIcon) themeIcon.textContent = '☀️';
            showToast("🌙 Mode Gelap diaktifkan");
        }
    };

    function initTheme() {
        const savedTheme = localStorage.getItem('theme');
        const prefersDark = window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches;
        const themeIcon = document.getElementById('theme-icon');

        if (savedTheme === 'dark' || (!savedTheme && prefersDark)) {
            document.documentElement.classList.add('dark');
            if (themeIcon) themeIcon.textContent = '☀️';
        } else {
            document.documentElement.classList.remove('dark');
            if (themeIcon) themeIcon.textContent = '🌙';
        }
    }

    // Initialize App on DOM Load
    window.addEventListener('DOMContentLoaded', () => {
        initTheme();
        loadLocalStorageData();

        // Dynamic Sticky Header Scroll Effect
        window.addEventListener('scroll', () => {
            const header = document.getElementById('main-header');
            if (header) {
                if (window.scrollY > 15) {
                    header.classList.add('shadow-md');
                } else {
                    header.classList.remove('shadow-md');
                }
            }
        });
    });
</script>
