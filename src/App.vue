<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const menu = ['Beranda', 'Tentang', 'Struktur Tim', 'Proker', 'Dokumentasi', 'Kontak']

const heroSlides = [
  '/slideshow/IMG_0743%20(3).jpg',
  '/slideshow/IMG_7102%20(1).jpg',
  '/slideshow/IMG_7320%20(2).jpg',
  '/slideshow/IMG_7637%20(1).jpg',
  '/slideshow/IMG_7638%20(1).jpg'
]
const currentSlide = ref(0)
const isPlaying = ref(false)
let audioEl = null

const toggleMusic = () => {
  if (!audioEl) {
    audioEl = new Audio('/MP3/ssstik.io_1790577652096.mp3')
    audioEl.loop = true
    audioEl.onended = () => { isPlaying.value = false }
  }
  if (isPlaying.value) {
    audioEl.pause()
    isPlaying.value = false
  } else {
    audioEl.play()
    isPlaying.value = true
  }
}
const isMobileMenuOpen = ref(false)
let slideInterval

onMounted(() => {
  slideInterval = setInterval(() => {
    currentSlide.value = (currentSlide.value + 1) % heroSlides.length
  }, 3000)
})

onUnmounted(() => {
  clearInterval(slideInterval)
})

const highlightStats = [
  { label: 'Lokasi Desa', value: 'Desa Boidu' },
  { label: 'Periode KKN', value: 'Agustus - September 2026' },
  { label: 'Jumlah Anggota', value: '16 Mahasiswa', subtext: '11 Perempuan, 5 Laki-laki' },
]

const prokerInti = [
  "Pelatihan budidaya tanaman pekarangan untuk ketahanan pangan keluarga",
  "Pembuatan KEPER bibit rica dan tomat (kebun percontohan) sebagai pemanfaatan lahan pekarangan",
  "Distribusi polybag bibit rica dan tomat sebagai pengganti pemanfaatan pekarangan rumah tangga"
]

const prokerTambahan = [
  "Raigma cup 3 (Rangkaian Kegiatan Mahasiswa) kolaborasi dengan Karang Taruna Mutiara Hijau Desa Boidu",
  "Sosialisasi ketahanan pangan melalui budidaya cabai dan tomat"
]

const pembina = [
  { name: 'Prof., Dr. Fahrudin Zain Olilingo, S.E., M.Si.', role: 'Ketua DPL', image: '/DPL/Prof., Dr. Fahrudin Zain Olilingo, S.E., M.Si..jpg' },
  { name: 'Dr. Sahmin Noholo, SE, MM', role: 'Anggota DPL', image: '/DPL/Dr. Sahmin Noholo, SE, MM.jpg' },
  { name: 'Dr. Irwan Bempah, S.P., M.P.', role: 'Anggota DPL', image: '/DPL/Dr. Irwan Bempah, S.P., M.P..jpg' },
  { name: 'Bpk. Masri Polihito', role: 'Kepala Desa Boidu', image: '/DPL/Bpk. Masri Polihito.jpeg' }
]

const pengurusInti = [
  { name: 'Mochamad Fachry Botutihe', role: 'Sekretaris', image: null, tagline: '"Disiplin administrasi adalah kunci kelancaran setiap program desa."' },
  { name: 'Tegar Purnama Hulopi', role: 'Koordinator Desa', image: '/KSB/Tegar Purnama Hulopi.jpeg', tagline: '"Pemimpin bukan sekadar memberi arah, tapi berjalan bersama mewujudkan cita."' },
  { name: 'Siti Rahmadani Mouko', role: 'Bendahara', image: '/KSB/Siti Rahmadani Mouko.jpeg', tagline: '"Transparansi dan kehati-hatian finansial demi hasil pengabdian maksimal."' }
]

const divisi = [
  {
    nama: 'HUMAS',
    anggota: [
      { name: 'Putri Adelia Nazwa Masiu', image: '/Humas/Putri Adelia Nazwa Masiu.jpeg', tagline: '"Menjadi jembatan aspirasi antara warga dan tim pengabdi."' },
      { name: "Nisrina Qurrotul'Ain", image: "/Humas/Nisrina Qurrotul Ain.jpeg", tagline: '"Komunikasi yang baik adalah awal dari kerjasama yang luar biasa."' },
      { name: 'Shinta Novia Erianty', image: '/Humas/Shinta Novia Erianty.jpeg', tagline: '"Menyapa desa dengan senyuman dan informasi akurat."' }
    ]
  },
  {
    nama: 'Acara',
    anggota: [
      { name: 'Nazwa Putri Mbuinga', image: '/Acara/Nazwa Putri Mbuinga.jpeg', tagline: '"Setiap kegiatan adalah momen berharga yang harus dirancang sempurna."' },
      { name: 'Awa Monopo', image: '/Acara/Awa Monopo.jpeg', tagline: '"Memastikan setiap rincian acara membawa dampak bagi desa."' },
      { name: 'Susilawati Igirisa', image: '/Acara/Susilawati Igirisa.jpeg', tagline: '"Kreativitas tiada henti untuk senyum warga Boidu."' },
      { name: 'Karmila Djafar', image: '/Acara/Karmila Djafar.jpeg', tagline: '"Semarak pengabdian hadir dari persiapan yang matang."' }
    ]
  },
  {
    nama: 'Perlengkapan',
    anggota: [
      { name: 'Ericksandi Datu Adam', image: null, tagline: '"Kami memastikan tidak ada satu pun alat yang menghambat jalannya misi."' },
      { name: 'Sugito Muhammad', image: null, tagline: '"Detail logistik adalah fondasi tersembunyi kesuksesan."' },
      { name: 'Mohamad Akbar Gintulangi', image: null, tagline: '"Sedia payung sebelum hujan, sedia perlengkapan sebelum acara jalan."' }
    ]
  },
  {
    nama: 'PDD',
    anggota: [
      { name: 'Sri Imelda Monda', image: '/PDD/Sri Imelda Monda.jpeg', tagline: '"Mengabadikan cerita, mendokumentasikan setiap senyum dan usaha."' },
      { name: 'Siti Fadhila Noholo', image: '/PDD/Siti Fadhila Noholo.jpeg', tagline: '"Lensa kami menangkap esensi pengabdian yang sebenarnya."' },
      { name: 'Mustika Yusuf', image: '/PDD/Mustika Yusuf.jpeg', tagline: '"Visual yang berbicara lebih lantang daripada sekadar kata."' }
    ]
  }
]

const selectedMember = ref(null)
const showArticleModal = ref(false)
const selectedArticle = ref(null)

const dokumentasi = [
  { title: 'Doa Bersama Maulid Nabi Muhammad SAW', date: '12 Jul 2026', category: 'Keagamaan', image: '/Galeri Dokumentasi/DOA BERSAMA DI MASJID, DALAM RANGKA PERAYAAN MAULID NABI MUHAMMAD .jpg' },
  { title: 'Kunjungan ke Bumi Perkemahan', date: '15 Jul 2026', category: 'Kegiatan', image: '/Galeri Dokumentasi/KUNJUNGAN KE BUMI PERKEMAHAAN.jpg' },
  { title: 'Kunjungan Perdana & Observasi Lahan Proker', date: '20 Jul 2026', category: 'Lingkungan', image: '/Galeri Dokumentasi/KUNJUNGAN PERDANA, DAN OBSERVASI AWAL CALON LAHAN PROKER.jpg' },
  { title: 'Pengukuran Bedengan Proker Inti', date: '5 Agu 2026', category: 'Pertanian', image: '/Galeri Dokumentasi/PENGUKURAN BEDENGAN PROKER INTI.jpg' },
  { title: 'Semarak HUT RI di Kantor Camat Bulango', date: '17 Agu 2026', category: 'Kemerdekaan', image: '/Galeri Dokumentasi/SEMARAK HUT RI KANTOR CAMAT BULANGO.jpg' },
]

const dokumentasiKarangTaruna = [
  { 
    title: 'Rapat Pembahasan Raigma Cup 3', 
    category: 'Kolaborasi Pemuda',
    date: '30 Jul 2026',
    description: 'Pertemuan rutin dan intensif dengan anggota Karang Taruna Mutiara Hijau untuk mematangkan konsep, jadwal, dan kepanitiaan acara perlombaan tahunan Raigma Cup 3. Kami berdiskusi mengenai pembagian tugas dan anggaran agar acara dapat berjalan dengan lancar dan meriah.',
    image: '/Kolaborasi Pemuda/Rapat Pembahasan Raigma Cup 3.jpg' 
  },
  { 
    title: 'Rapat Perdana', 
    category: 'Kolaborasi Pemuda',
    date: '10 Jul 2026',
    description: 'Rapat perdana perkenalan dan penyatuan visi antara mahasiswa KKN dan pengurus Karang Taruna Mutiara Hijau. Pada momen ini, kami saling bertukar ide dan menyepakati beberapa program kolaborasi yang akan dilaksanakan demi kemajuan pemuda dan masyarakat Desa Boidu.',
    image: '/Kolaborasi Pemuda/Rapat Perdana.jpg' 
  },
  { 
    title: 'Semarak HUT RI Ke-81', 
    category: 'Kolaborasi Pemuda',
    date: '17 Agu 2026',
    description: 'Puncak perayaan Hari Kemerdekaan Republik Indonesia ke-81 di Desa Boidu. Bersama Karang Taruna Mutiara Hijau, mahasiswa KKN menyelenggarakan berbagai perlombaan rakyat yang meriah dan menghibur, mempererat tali persaudaraan antarwarga.',
    image: '/Kolaborasi Pemuda/Semarak HUT RI Ke 81.jpg' 
  },
  { 
    title: 'KKN-T bersama KTMH Raigma Cup 3', 
    category: 'Kolaborasi Pemuda',
    date: '10 Agu 2026',
    description: 'Dokumentasi kebersamaan tim KKN Tematik bersama Karang Taruna Mutiara Hijau dalam rangkaian kegiatan Raigma Cup 3. Sinergi nyata antara mahasiswa dan pemuda desa dalam membangun semangat kebersamaan.',
    image: '/Kolaborasi Pemuda/KKN-T WITH KTMH RAIGMA CUP 3.jpg' 
  }
]

const sorotanKegiatan = [
  { 
    title: 'Pelatihan Budidaya Tanaman Pekarangan', 
    category: 'Ketahanan Pangan',
    date: '10 Jul 2026',
    description: 'Dapur yang sehat dimulai dari pekarangan rumah. Kami hadir menemani ibu-ibu dan keluarga di Desa Boidu untuk mengubah lahan kosong di sekitar rumah menjadi sumber pangan keluarga yang nyata, hemat, dan berkelanjutan.',
    sliderImage: '/Sorotan Kegiatan/Pelatihan budidaya tanaman pekarangan untuk ketahanan pangan keluarga FOTO 1.jpg',
    image: '/Sorotan Kegiatan/Pelatihan budidaya tanaman pekarangan untuk ketahanan pangan keluarga FOTO 2.jpg'
  },
  { 
    title: 'Pembuatan KEPER (Kebun Percontohan)', 
    category: 'Pertanian Desa',
    date: '18 Jul 2026',
    description: 'Membangun kebun percontohan sebagai wujud nyata pemanfaatan lahan pekarangan secara optimal dan produktif untuk menanam bibit rica (cabai) dan tomat.',
    image: '/Sorotan Kegiatan/Pembuatan KEPER (Kebun Percontohan).jpeg'
  },
  { 
    title: 'Distribusi Polybag Bibit Rica & Tomat', 
    category: 'Pemberdayaan Warga',
    date: '25 Jul 2026',
    description: 'Membagikan polybag berisi bibit rica dan tomat kepada rumah tangga sebagai langkah awal partisipasi aktif warga dalam program ketahanan pangan mandiri.',
    image: '/Sorotan Kegiatan/Distribusi Polybag Bibit Rica & Tomat.jpeg'
  },
  { 
    title: 'Raigma Cup 3', 
    category: 'Kolaborasi Pemuda',
    date: '10 Agu 2026',
    description: 'Rangkaian Kegiatan Mahasiswa yang berkolaborasi dengan Karang Taruna Mutiara Hijau Desa Boidu untuk mempererat tali silaturahmi dan semangat kepemudaan.',
    image: '/Sorotan Kegiatan/RAIGMA CUP 3.jpg'
  },
  {
    title: 'Sosialisasi Ketahanan Pangan Melalui Budidaya Cabai & Tomat',
    category: 'Proker Tambahan',
    date: '20 Agu 2026',
    description: 'Kegiatan sosialisasi mengenai pentingnya ketahanan pangan keluarga dan optimalisasi pemanfaatan pekarangan melalui budidaya tanaman cabai dan tomat.',
    image: '/Sorotan Kegiatan/sosialisasi ketahanan pangan melalui budidaya cabai dan tomat.jpg'
  }
]

const dokumentasiRandom = [
  '/MOMEN ACAK & CANDID/IMG-20260909-WA0116.jpg',
  '/MOMEN ACAK & CANDID/IMG-20260909-WA0192.jpg',
  '/MOMEN ACAK & CANDID/IMG_1169.jpg',
  '/MOMEN ACAK & CANDID/IMG_1189.jpg',
  '/MOMEN ACAK & CANDID/IMG_1262.jpg',
  '/MOMEN ACAK & CANDID/IMG_1317 (2).JPG',
  '/MOMEN ACAK & CANDID/IMG_1321 (1).jpg',
  '/MOMEN ACAK & CANDID/IMG_1607.jpg',
  '/MOMEN ACAK & CANDID/IMG_1613.jpg',
  '/MOMEN ACAK & CANDID/IMG_1729.jpg',
  '/MOMEN ACAK & CANDID/IMG_1941.jpg',
  '/MOMEN ACAK & CANDID/IMG_20260829_140054_210 (1).jpg',
  '/MOMEN ACAK & CANDID/IMG_20260830_141747_220 (1).jpg',
  '/MOMEN ACAK & CANDID/IMG_20260830_141754_659.jpg',
  '/MOMEN ACAK & CANDID/IMG_20260830_153721_551.jpg',
  '/MOMEN ACAK & CANDID/IMG_20260830_204951_825 (2).jpg',
  '/MOMEN ACAK & CANDID/IMG_20260908_165615_038.jpg',
  '/MOMEN ACAK & CANDID/IMG_20260913_022905_435.jpg',
  '/MOMEN ACAK & CANDID/IMG_2791.jpg',
  '/MOMEN ACAK & CANDID/IMG_2867.jpg',
  '/MOMEN ACAK & CANDID/IMG_7927.jpg',
  '/MOMEN ACAK & CANDID/IMG_7934.jpg',
  '/MOMEN ACAK & CANDID/IMG_7937.jpg',
  '/MOMEN ACAK & CANDID/IMG_7952.jpg',
  '/MOMEN ACAK & CANDID/IMG_7957.jpg',
  '/MOMEN ACAK & CANDID/IMG_7961.jpg',
  '/MOMEN ACAK & CANDID/IMG_7990.jpg',
  '/MOMEN ACAK & CANDID/IMG_7991.jpg',
  '/MOMEN ACAK & CANDID/IMG_7992.jpg'
]
</script>

<template>
  <div class="font-sans text-gray-800 bg-white relative overflow-hidden">
    <!-- Navbar -->
    <nav class="fixed top-0 left-0 w-full z-50 bg-primary-pink shadow-md transition-all duration-300">
      <div class="max-w-7xl mx-auto px-6 py-3 md:py-4 flex justify-between items-center gap-8 md:gap-16">
        
        <!-- Logo Section -->
        <a href="#beranda" class="flex items-center gap-3 group shrink-0">
          <div class="w-10 h-10 md:w-12 md:h-12 rounded-full bg-white flex items-center justify-center shadow-sm group-hover:scale-105 transition-transform overflow-hidden border-2 border-white">
            <img src="/logo%20kkn/7.png" alt="Logo KKN" class="w-full h-full object-cover" />
          </div>
          <div class="flex flex-col justify-center">
            <span class="text-white font-extrabold text-sm md:text-base tracking-widest whitespace-nowrap leading-tight">KKN TEMATIK II</span>
            <span class="text-white/90 font-medium text-[10px] md:text-xs tracking-wider whitespace-nowrap leading-tight">UNIVERSITAS NEGERI GORONTALO</span>
          </div>
        </a>
        
        <!-- Navigation Links (Desktop) -->
        <div class="hidden lg:flex items-center gap-8">
          <a v-for="item in menu" :key="item" :href="'#' + item.toLowerCase().replace(' ', '-')" class="text-sm font-medium text-white/80 hover:text-white hover:scale-105 transition-all duration-300">
            {{ item }}
          </a>
        </div>
        
        <!-- Right Tag (Desktop) -->
        <div class="hidden lg:flex bg-white px-6 py-2.5 md:py-3 rounded-full items-center justify-center hover:bg-gray-100 transition-colors cursor-pointer shadow-sm">
          <span class="font-bold text-sm text-gray-900 tracking-tight">Desa Boidu</span>
        </div>

        <!-- Hamburger Button (Mobile) -->
        <button @click="isMobileMenuOpen = !isMobileMenuOpen" class="lg:hidden text-white focus:outline-none p-2">
          <svg class="w-7 h-7" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path v-if="!isMobileMenuOpen" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path>
            <path v-else stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
          </svg>
        </button>
        
      </div>
      
      <!-- Mobile Menu Dropdown -->
      <transition 
        enter-active-class="transition duration-200 ease-out"
        enter-from-class="transform -translate-y-4 opacity-0"
        enter-to-class="transform translate-y-0 opacity-100"
        leave-active-class="transition duration-150 ease-in"
        leave-from-class="transform translate-y-0 opacity-100"
        leave-to-class="transform -translate-y-4 opacity-0"
      >
        <div v-show="isMobileMenuOpen" class="lg:hidden bg-white shadow-xl absolute top-full left-0 w-full flex flex-col border-t border-gray-100">
          <a v-for="item in menu" :key="item" :href="'#' + item.toLowerCase().replace(' ', '-')" @click="isMobileMenuOpen = false" class="px-6 py-4 text-gray-800 font-medium border-b border-gray-50 hover:bg-pink-50 hover:text-primary-pink-dark transition-colors">
            {{ item }}
          </a>
        </div>
      </transition>
    </nav>

    <!-- Hero Section -->
    <section id="beranda" class="pt-32 pb-20 px-6 md:px-12 flex flex-col md:flex-row items-center gap-12 max-w-7xl mx-auto min-h-[90vh] relative z-10">
      <!-- Background Silhouette 1 (Left City/Monuments) -->
      <svg class="absolute top-20 -left-32 w-[600px] h-[600px] text-gray-100 opacity-60 z-[-1] pointer-events-none" viewBox="0 0 500 500" fill="currentColor">
        <!-- Generic monument shapes -->
        <path d="M100 450 L120 150 L140 450 Z" />
        <path d="M110 300 L130 300 M115 200 L125 200" stroke="currentColor" stroke-width="4"/>
        <path d="M200 450 L200 300 C200 250 250 200 250 200 C250 200 300 250 300 300 L300 450 Z" />
        <rect x="220" y="350" width="20" height="100"/>
        <rect x="260" y="350" width="20" height="100"/>
        <path d="M50 450 L70 350 L90 450 Z" />
      </svg>
      <!-- Background Dashed Path 1 -->
      <svg class="absolute top-40 left-0 w-full h-[500px] text-gray-200 z-[-1] pointer-events-none" viewBox="0 0 1000 500" fill="none" stroke="currentColor" stroke-width="3" stroke-dasharray="10 10">
        <path d="M -100 400 Q 200 100 500 250 T 1100 100" />
        <!-- Airplane silhouette -->
        <path d="M 480 230 L 510 215 L 505 255 Z" fill="currentColor" stroke="none" />
        <path d="M 495 235 L 485 260 L 500 250 Z" fill="currentColor" stroke="none" />
      </svg>

      <div class="flex-1 space-y-6 relative z-10">
        <h1 class="text-5xl md:text-6xl font-extrabold leading-tight text-gray-900">
          Mengabdi dengan <span class="text-primary-pink-dark">Hati</span>,<br/>Membangun <span class="text-primary-green-dark">Desa</span>.
        </h1>
        <p class="text-lg text-gray-600 max-w-lg">
          Selamat datang di portal dokumentasi KKN Desa Boidu. Bersama masyarakat, kami wujudkan potensi desa menuju masa depan yang lebih cerah.
        </p>
        <div class="flex flex-col sm:flex-row gap-4 pt-4">
          <a href="#tentang" class="bg-primary-pink-dark hover:bg-pink-700 text-white px-8 py-3 rounded-full font-bold shadow-lg shadow-pink-200 transition-transform transform hover:-translate-y-1 text-center">
            Mulai Eksplorasi
          </a>
          <button @click="toggleMusic" class="bg-white border-2 border-gray-200 hover:border-primary-pink-dark hover:text-primary-pink-dark text-gray-700 px-8 py-3 rounded-full font-bold transition-all flex items-center justify-center gap-2">
            <!-- Play icon -->
            <svg v-if="!isPlaying" xmlns="http://www.w3.org/2000/svg" class="w-5 h-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 19V6l12 7-12 7z" />
            </svg>
            <!-- Pause / equalizer icon -->
            <svg v-else xmlns="http://www.w3.org/2000/svg" class="w-5 h-5 text-primary-pink-dark" fill="currentColor" viewBox="0 0 24 24">
              <rect x="5" y="4" width="4" height="16" rx="1"/>
              <rect x="15" y="4" width="4" height="16" rx="1"/>
            </svg>
            <span>{{ isPlaying ? 'Sedang Putar ♪' : 'Putar Musik' }}</span>
          </button>
        </div>
      </div>
      <div class="flex-1 relative pl-0 md:pl-10 mt-12 md:mt-0 flex justify-center w-full">
        <div class="absolute inset-0 bg-primary-green rounded-full blur-3xl opacity-30 animate-pulse"></div>
        <div class="relative w-full max-w-[300px] md:max-w-[380px] h-[380px] md:h-[480px] rounded-t-full rounded-b-[3rem] border-2 border-dashed border-primary-pink p-3 group mx-auto">
          <div class="relative w-full h-full rounded-t-full rounded-b-[2.2rem] overflow-hidden shadow-2xl bg-gray-100 transform group-hover:scale-[1.03] transition-transform duration-700">
            <img 
              v-for="(img, index) in heroSlides" 
              :key="index"
              :src="img" 
              alt="Hero Slideshow" 
              class="absolute inset-0 w-full h-full object-cover transition-all duration-1000 ease-in-out"
              :style="{ opacity: currentSlide === index ? 1 : 0, zIndex: currentSlide === index ? 10 : 0 }"
            />
          </div>
          
          <!-- Decorative elements with SVGs -->
          <div class="absolute -top-4 -right-4 w-16 h-16 bg-primary-pink rounded-full flex items-center justify-center text-white shadow-lg">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <path d="M12 2v4M12 18v4M4.93 4.93l2.83 2.83M16.24 16.24l2.83 2.83M2 12h4M18 12h4M4.93 19.07l2.83-2.83M16.24 7.76l2.83-2.83"/>
            </svg>
          </div>
          <div class="absolute bottom-10 -left-8 w-14 h-14 bg-primary-green-dark rounded-full flex items-center justify-center text-white shadow-lg">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-7 w-7" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <path d="M12 22c4-4 4-10 0-14-4 4-4 10 0 14z" fill="currentColor" fill-opacity="0.3"/>
              <path d="M12 22V8"/>
              <path d="M12 14c-4-2-4-8 0-10"/>
              <path d="M12 14c4-2 4-8 0-10"/>
            </svg>
          </div>
        </div>
      </div>
    </section>

    <!-- Pengenalan Desa & Lokasi Posko -->
    <section id="pengenalan-desa" class="pt-16 pb-36 bg-slate-50 relative z-10 border-t border-gray-100">
      <div class="max-w-7xl mx-auto px-6 md:px-12">
        <div class="flex flex-col lg:flex-row gap-12 items-center">
          
          <!-- Teks Pengenalan -->
          <div class="lg:w-1/2 space-y-6">

            <h2 class="text-4xl md:text-5xl font-extrabold text-gray-900 leading-tight">
              Selamat Datang di <br/><span class="text-transparent bg-clip-text bg-gradient-to-r from-primary-green-dark to-primary-green">Desa Boidu</span>
            </h2>
            <p class="text-lg text-gray-600 leading-relaxed">
              Desa Boidu adalah desa yang kaya akan potensi alam dan kearifan lokal. Masyarakatnya yang ramah dan semangat gotong royong yang tinggi menjadi fondasi utama dalam setiap langkah pembangunan desa menuju masa depan yang lebih baik.
            </p>
            <div class="pt-6 flex flex-col gap-2">
              <div class="flex items-center gap-4 text-gray-800 font-semibold text-lg">
                <div class="w-12 h-12 rounded-full bg-primary-pink/10 flex items-center justify-center text-primary-pink-dark shadow-inner">
                  <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"></path><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"></path></svg>
                </div>
                Lokasi Posko KKN Kami
              </div>
              <p class="text-sm text-gray-500 ml-16 max-w-md">
                Desa Boidu, Kecamatan Bulango Utara, Kabupaten Bone Bolango, Gorontalo.
              </p>
            </div>
          </div>

          <!-- Maps Frame -->
          <div class="lg:w-1/2 w-full h-[400px] md:h-[450px] rounded-[2.5rem] overflow-hidden shadow-2xl border-[6px] border-white bg-gray-200 relative group">
            <!-- Loading skeleton for map -->
            <div class="absolute inset-0 flex items-center justify-center text-gray-400 bg-gray-100">
               Memuat Peta...
            </div>
            <iframe 
              src="https://maps.google.com/maps?q=0.633215,123.079720&t=&z=15&ie=UTF8&iwloc=&output=embed" 
              class="absolute inset-0 w-full h-full border-0 grayscale hover:grayscale-0 transition-all duration-700" 
              allowfullscreen="" 
              loading="lazy" 
              referrerpolicy="no-referrer-when-downgrade">
            </iframe>
          </div>

        </div>
      </div>
    </section>

    <!-- Info/Highlight Card -->
    <section id="tentang" class="py-16 bg-transparent relative z-20">
      <div class="max-w-6xl mx-auto px-6">
        <div class="bg-white rounded-[2rem] shadow-xl p-8 md:p-12 flex flex-col md:flex-row gap-10 items-center transform -translate-y-24 relative z-20 border border-gray-50">
          <!-- Background Dashed Path inside card area -->
          <svg class="absolute -top-10 -right-20 w-64 h-64 text-primary-pink opacity-20 z-[-1] pointer-events-none" viewBox="0 0 200 200" fill="none" stroke="currentColor" stroke-width="2" stroke-dasharray="6 6">
            <circle cx="100" cy="100" r="80" />
            <circle cx="100" cy="100" r="60" />
          </svg>

          <div class="w-full md:w-2/5 flex items-center justify-center">
            <img src="/logo%20kkn/7.png" alt="Logo KKN" class="w-64 h-64 object-contain drop-shadow-xl" />
          </div>
          <div class="w-full md:w-3/5 space-y-6">
            <h2 class="text-3xl font-bold">Tentang Pengabdian Kami</h2>
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
              <div v-for="stat in highlightStats" :key="stat.label" class="p-4 rounded-xl bg-gray-50 border border-gray-100">
                <div class="text-sm text-gray-500 mb-1">{{ stat.label }}</div>
                <div class="font-bold text-lg text-primary-pink-dark">{{ stat.value }}</div>
                <div v-if="stat.subtext" class="text-[11px] text-gray-500 mt-1.5 font-medium leading-tight">{{ stat.subtext }}</div>
              </div>
            </div>
            <div class="flex gap-4 pt-2">
              <a href="#struktur-tim" class="bg-gray-900 text-white px-6 py-2 rounded-full font-medium hover:bg-gray-800 transition-colors">Lihat Struktur Tim</a>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Kategori Program Kerja -->
    <!-- Kategori Program Kerja -->
    <section id="proker" class="pt-8 pb-20 px-6 max-w-7xl mx-auto relative z-10">
      <div class="text-center mb-16">
        <h2 class="text-4xl font-bold mb-4">Program Kerja Unggulan</h2>
        <p class="text-gray-600 max-w-2xl mx-auto">Berbagai inisiatif yang kami jalankan untuk memberdayakan dan meningkatkan kualitas hidup masyarakat Desa Boidu.</p>
      </div>
      
      <div class="grid grid-cols-1 md:grid-cols-2 gap-12">
        <!-- Proker Inti -->
        <div class="bg-gradient-to-br from-primary-pink/10 to-white rounded-3xl p-8 md:p-12 shadow-xl border border-pink-100 relative overflow-hidden">
          <div class="absolute -right-10 -top-10 text-primary-pink/20">
            <svg class="w-48 h-48" fill="currentColor" viewBox="0 0 24 24"><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/></svg>
          </div>
          <h3 class="text-3xl font-extrabold text-gray-900 mb-8 relative z-10 flex items-center gap-3">
            <span class="w-3 h-10 bg-primary-pink rounded-full inline-block"></span>
            Proker Inti
          </h3>
          <ul class="space-y-6 relative z-10">
            <li v-for="(item, index) in prokerInti" :key="index" class="flex gap-4">
              <div class="flex-shrink-0 w-10 h-10 rounded-full bg-primary-pink text-white flex items-center justify-center font-bold shadow-md">{{ index + 1 }}</div>
              <p class="text-gray-800 text-lg leading-relaxed font-medium">{{ item }}</p>
            </li>
          </ul>
        </div>
        
        <!-- Proker Tambahan -->
        <div class="bg-gradient-to-bl from-primary-green/10 to-white rounded-3xl p-8 md:p-12 shadow-xl border border-green-100 relative overflow-hidden">
          <div class="absolute -left-10 -bottom-10 text-primary-green/20">
            <svg class="w-48 h-48" fill="currentColor" viewBox="0 0 24 24"><path d="M13 10V3L4 14h7v7l9-11h-7z"/></svg>
          </div>
          <h3 class="text-3xl font-extrabold text-gray-900 mb-8 relative z-10 flex items-center gap-3">
            <span class="w-3 h-10 bg-primary-green rounded-full inline-block"></span>
            Proker Tambahan
          </h3>
          <ul class="space-y-6 relative z-10">
            <li v-for="(item, index) in prokerTambahan" :key="index" class="flex gap-4">
              <div class="flex-shrink-0 w-10 h-10 rounded-full bg-primary-green text-white flex items-center justify-center font-bold shadow-md">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" viewBox="0 0 20 20" fill="currentColor"><path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd" /></svg>
              </div>
              <p class="text-gray-800 text-lg leading-relaxed font-medium">{{ item }}</p>
            </li>
          </ul>
        </div>
      </div>
    </section>

    <!-- Struktur Organisasi -->
    <section id="struktur-tim" class="py-20 relative px-6 z-10">
      <!-- Faint background color layer so it feels distinct but shows some watermark through -->
      <div class="absolute inset-0 bg-gray-50/80 z-[-1]"></div>
      
      <div class="max-w-6xl mx-auto">
        <div class="text-center mb-16">
          <h2 class="text-4xl font-bold mb-4">Struktur Organisasi</h2>
          <p class="text-gray-600">Jajaran pembimbing dan pelaksana KKN Desa Boidu.</p>
        </div>
        
        <!-- DPL dan Kepala Desa -->
        <div class="flex flex-wrap justify-center gap-8 mb-16 relative">
          <!-- Hubungan Garis -->
          <div class="hidden md:block absolute top-full left-1/2 w-0.5 h-16 bg-gray-300 -translate-x-1/2"></div>
          
          <div v-for="person in pembina" :key="person.name" class="bg-white p-4 rounded-2xl shadow-lg border-2 border-primary-green flex flex-col items-center w-64 hover:shadow-xl transition-shadow z-10">
            <div class="w-full aspect-[4/5] overflow-hidden rounded-xl mb-4 bg-gradient-to-br from-primary-green/10 to-green-50 flex items-center justify-center">
              <img v-if="person.image" :src="person.image" :alt="person.name" class="w-full h-full object-cover hover:scale-105 transition-transform duration-500" />
              <svg v-else class="w-20 h-20 text-primary-green/40" fill="currentColor" viewBox="0 0 24 24"><path d="M12 12c2.7 0 4.8-2.1 4.8-4.8S14.7 2.4 12 2.4 7.2 4.5 7.2 7.2 9.3 12 12 12zm0 2.4c-3.2 0-9.6 1.6-9.6 4.8v2.4h19.2v-2.4c0-3.2-6.4-4.8-9.6-4.8z"/></svg>
            </div>
            <h4 class="font-bold text-lg text-gray-900 text-center">{{ person.name }}</h4>
            <span class="text-sm text-primary-green-dark font-bold text-center mt-1">{{ person.role }}</span>
          </div>
        </div>
        
        <!-- Pengurus Inti -->
        <div class="relative pt-8 border-t-2 border-gray-300 mb-16">
          <div class="absolute -top-1 left-1/2 w-2 h-2 rounded-full bg-gray-300 -translate-x-1/2"></div>
          <div class="hidden md:block absolute top-full left-1/2 w-0.5 h-12 bg-gray-300 -translate-x-1/2"></div>
          
          <h3 class="text-center font-bold text-xl text-gray-800 mb-8">KSB</h3>
          <div class="flex flex-wrap justify-center gap-6">
            <div v-for="member in pengurusInti" :key="member.name" @click="selectedMember = member" class="bg-white p-3.5 rounded-2xl shadow-md border border-gray-100 flex flex-col items-center w-48 hover:shadow-xl hover:border-primary-pink-dark transition-all group z-10 cursor-pointer">
              <div class="w-full aspect-square overflow-hidden rounded-xl mb-4 relative bg-gradient-to-br from-pink-50 to-pink-100 flex items-center justify-center">
                <!-- Highlight badge for coordinator -->
                <div v-if="member.role === 'Koordinator Desa'" class="absolute top-2 right-2 z-10 bg-primary-pink-dark text-white text-[10px] font-bold px-2 py-1 rounded shadow-sm">
                  LEADER
                </div>
                <img v-if="member.image" :src="member.image" :alt="member.name" class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500" />
                <svg v-else class="w-16 h-16 text-primary-pink/40" fill="currentColor" viewBox="0 0 24 24"><path d="M12 12c2.7 0 4.8-2.1 4.8-4.8S14.7 2.4 12 2.4 7.2 4.5 7.2 7.2 9.3 12 12 12zm0 2.4c-3.2 0-9.6 1.6-9.6 4.8v2.4h19.2v-2.4c0-3.2-6.4-4.8-9.6-4.8z"/></svg>
              </div>
              <h4 class="font-bold text-base text-gray-900 text-center">{{ member.name }}</h4>
              <span class="text-sm text-primary-pink-dark font-medium text-center mt-1">{{ member.role }}</span>
            </div>
          </div>
        </div>

        <!-- Divisi-Divisi -->
        <div class="relative pt-8 border-t-2 border-gray-300">
          <div class="absolute -top-1 left-1/2 w-2 h-2 rounded-full bg-gray-300 -translate-x-1/2"></div>
          
          <h3 class="text-center font-bold text-xl text-gray-800 mb-10">Divisi Kerja</h3>
          <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
            <div v-for="div in divisi" :key="div.nama" class="flex flex-col items-center">
              <h4 class="font-bold text-lg text-primary-green-dark mb-5 border-b-2 border-primary-green pb-2">{{ div.nama }}</h4>
              <div class="flex flex-col gap-4">
                <div v-for="anggota in div.anggota" :key="anggota.name" @click="selectedMember = { ...anggota, role: 'Divisi ' + div.nama }" class="bg-white p-3 rounded-xl shadow-sm border border-gray-100 flex items-center gap-3 w-56 hover:shadow-md transition-shadow cursor-pointer">
                  <div class="w-12 h-12 rounded-full bg-gradient-to-br from-primary-pink/20 to-pink-50 flex items-center justify-center shrink-0 overflow-hidden">
                    <img v-if="anggota.image" :src="anggota.image" :alt="anggota.name" class="w-full h-full object-cover" />
                    <svg v-else class="w-7 h-7 text-primary-pink/50" fill="currentColor" viewBox="0 0 24 24"><path d="M12 12c2.7 0 4.8-2.1 4.8-4.8S14.7 2.4 12 2.4 7.2 4.5 7.2 7.2 9.3 12 12 12zm0 2.4c-3.2 0-9.6 1.6-9.6 4.8v2.4h19.2v-2.4c0-3.2-6.4-4.8-9.6-4.8z"/></svg>
                  </div>
                  <div>
                    <h5 class="font-bold text-sm text-gray-900">{{ anggota.name }}</h5>
                    <span class="text-[10px] text-gray-500 uppercase tracking-wider">Anggota</span>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Sorotan Kegiatan / Blog -->
    <section id="sorotan" class="py-24 px-6 max-w-7xl mx-auto relative z-10">
      <div class="text-center mb-16">
        <h2 class="text-4xl font-bold mb-4">Sorotan Kegiatan</h2>
        <p class="text-gray-600">Jejak langkah nyata dari program kerja kami di Desa Boidu.</p>
      </div>

      <div class="flex overflow-x-auto snap-x snap-mandatory gap-16 pb-12 pt-4 hide-scrollbar px-2">
        <div v-for="(sorotan, index) in sorotanKegiatan" :key="sorotan.title" class="flex flex-col md:flex-row gap-8 lg:gap-16 items-center snap-center shrink-0 w-full" :class="index % 2 === 0 ? '' : 'md:flex-row-reverse'">
          
          <!-- Image Section (Kotak / Modern) -->
          <div class="w-full md:w-1/2 relative group">
            <!-- Modern Decorative Elements -->
            <div class="absolute -bottom-6 -right-6 md:-bottom-10 md:-right-10 w-32 h-32 md:w-56 md:h-56 rounded-full border border-dashed opacity-40 z-0 transition-transform duration-700 group-hover:rotate-45" :class="index % 2 === 0 ? 'border-primary-pink' : 'border-primary-green'"></div>
            <div class="absolute -top-4 -left-4 md:-top-6 md:-left-6 w-20 h-20 md:w-32 md:h-32 bg-gradient-to-br opacity-20 rounded-3xl z-0" :class="index % 2 === 0 ? 'from-primary-pink to-pink-100' : 'from-primary-green to-green-100'"></div>
            
            <div class="overflow-hidden rounded-3xl shadow-2xl relative w-full h-[350px] md:h-[500px] z-10 border-4 border-white">
              <div class="absolute inset-0 bg-black/5 group-hover:bg-transparent transition-colors duration-500 z-10 pointer-events-none"></div>
              <img v-if="sorotan.sliderImage || sorotan.image" :src="sorotan.sliderImage || sorotan.image" :alt="sorotan.title" class="w-full h-full object-cover transform group-hover:scale-105 transition-transform duration-700 ease-out" />
              <div v-else class="w-full h-full bg-gradient-to-br from-gray-100 to-gray-200 flex flex-col items-center justify-center gap-4">
                <svg class="w-16 h-16 text-gray-300" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M4 16l4.586-4.586a2 2 0 012.828 0L16 16m-2-2l1.586-1.586a2 2 0 012.828 0L20 14m-6-6h.01M6 20h12a2 2 0 002-2V6a2 2 0 00-2-2H6a2 2 0 00-2 2v12a2 2 0 002 2z" /></svg>
                <span class="text-gray-400 font-medium text-sm tracking-widest uppercase">Segera Hadir</span>
              </div>
            </div>
          </div>
          
          <!-- Content Section (Modern Article Style) -->
          <div class="w-full md:w-1/2 space-y-6 p-2 md:p-0 z-10">
            <div class="flex items-center gap-4 flex-wrap">
              <span class="font-bold tracking-widest uppercase text-xs md:text-sm px-4 py-1.5 rounded-full shadow-sm bg-white border border-gray-100" :class="index % 2 === 0 ? 'text-primary-green-dark' : 'text-primary-pink-dark'">
                {{ sorotan.category }}
              </span>
              <span class="text-gray-500 text-sm font-medium flex items-center gap-1.5">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z" /></svg>
                {{ sorotan.date }}
              </span>
            </div>
            
            <h2 class="text-4xl md:text-5xl lg:text-6xl font-extrabold text-gray-900 leading-[1.1] tracking-tight">{{ sorotan.title }}</h2>
            
            <div class="w-20 h-1.5 rounded-full" :class="index % 2 === 0 ? 'bg-primary-pink' : 'bg-primary-green'"></div>
            
            <p class="text-gray-600 text-lg md:text-xl leading-relaxed font-serif text-justify md:text-left">
              {{ sorotan.description }}
            </p>
            
            <div class="pt-6">
              <button @click="selectedArticle = sorotan; showArticleModal = true" class="group/btn flex items-center gap-3 font-bold transition-all px-8 py-3.5 rounded-xl border-2 shadow-sm hover:shadow-xl w-full sm:w-auto justify-center" :class="index % 2 === 0 ? 'border-primary-pink-dark text-primary-pink-dark hover:bg-primary-pink-dark hover:text-white' : 'border-primary-green-dark text-primary-green-dark hover:bg-primary-green-dark hover:text-white'">
                Baca Artikel Penuh
                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 transform group-hover/btn:translate-x-1.5 transition-transform" viewBox="0 0 20 20" fill="currentColor">
                  <path fill-rule="evenodd" d="M12.293 5.293a1 1 0 011.414 0l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414-1.414L14.586 11H3a1 1 0 110-2h11.586l-2.293-2.293a1 1 0 010-1.414z" clip-rule="evenodd" />
                </svg>
              </button>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Dokumentasi Kegiatan -->
    <section id="dokumentasi" class="py-20 relative px-6 z-10">
      <div class="absolute inset-0 bg-gray-50/80 z-[-1]"></div>
      <div class="max-w-7xl mx-auto">
        <div class="flex justify-between items-end mb-12">
          <div>
            <h2 class="text-4xl font-bold mb-4">Galeri Dokumentasi</h2>
            <p class="text-gray-600">Rekam jejak langkah kami di Desa Boidu.</p>
          </div>
          <a href="#" class="hidden md:inline-block text-primary-green-dark font-medium hover:underline">Lihat Semua →</a>
        </div>
        
        <div class="flex overflow-x-auto snap-x snap-mandatory pb-8 pt-2 hide-scrollbar">
          <div v-for="doc in dokumentasi" :key="doc.title" class="snap-center shrink-0 w-full px-2 md:px-4">
            <div class="bg-white rounded-[2rem] overflow-hidden shadow-2xl group relative h-[400px] md:h-[500px] lg:h-[600px] w-full">
              <!-- Label Kategori -->
              <div class="absolute top-6 right-6 z-20 bg-white/90 backdrop-blur text-sm font-extrabold px-4 py-2 rounded-full shadow-lg tracking-wider uppercase"
                   :class="doc.category === 'Lingkungan' || doc.category === 'Pendidikan' ? 'text-primary-green-dark' : 'text-primary-pink-dark'">
                {{ doc.category }}
              </div>
              
              <!-- Gambar atau Icon -->
              <img v-if="doc.image" :src="doc.image" :alt="doc.title" class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-1000" />
              <div v-else class="w-full h-full bg-gradient-to-br from-gray-100 to-gray-200 flex flex-col items-center justify-center gap-4">
                <svg class="w-24 h-24 text-gray-300" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1" d="M4 16l4.586-4.586a2 2 0 012.828 0L16 16m-2-2l1.586-1.586a2 2 0 012.828 0L20 14m-6-6h.01M6 20h12a2 2 0 002-2V6a2 2 0 00-2-2H6a2 2 0 00-2 2v12a2 2 0 002 2z" /></svg>
                <span class="text-gray-400 font-semibold text-sm uppercase tracking-wider">Foto Segera Hadir</span>
              </div>
              
              <!-- Overlay Gradien untuk Teks -->
              <div class="absolute inset-0 bg-gradient-to-t from-black/90 via-black/30 to-transparent z-10 pointer-events-none"></div>
              
              <!-- Informasi Teks di Atas Gambar -->
              <div class="absolute bottom-8 left-8 md:bottom-12 md:left-12 text-white z-20 max-w-2xl">
                <div class="text-sm md:text-base text-gray-300 mb-3 font-semibold tracking-widest uppercase flex items-center gap-2">
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-primary-pink" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z" /></svg>
                  {{ doc.date }}
                </div>
                <h3 class="font-extrabold text-3xl md:text-5xl lg:text-6xl drop-shadow-lg leading-tight">{{ doc.title }}</h3>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Dokumentasi Random -->
    <section id="momen-acak" class="py-20 relative px-6 z-10 bg-pink-50/50">
      <div class="max-w-7xl mx-auto">
        <div class="text-center mb-16">
          <span class="text-primary-pink-dark font-bold tracking-wider uppercase text-sm mb-2 block">Di Balik Layar</span>
          <h2 class="text-4xl font-bold mb-4">Momen Acak & Candid</h2>
          <p class="text-gray-600 max-w-2xl mx-auto">Potret keseharian, kebersamaan, dan keseruan tim KKN kami selama mengabdi di Desa Boidu.</p>
        </div>
        
        <div class="columns-2 md:columns-3 lg:columns-4 gap-4 md:gap-6 space-y-4 md:space-y-6">
          <div v-for="(img, idx) in dokumentasiRandom" :key="idx" class="break-inside-avoid relative group overflow-hidden rounded-2xl shadow-sm hover:shadow-xl transition-all duration-300">
            <img v-if="img" :src="img" class="w-full h-auto object-cover transform group-hover:scale-105 transition-transform duration-700" alt="Momen KKN" loading="lazy" />
            <div v-else class="w-full bg-gradient-to-br from-pink-50 to-gray-100 flex flex-col items-center justify-center" :class="idx % 3 === 0 ? 'aspect-[3/4]' : (idx % 2 === 0 ? 'aspect-square' : 'aspect-[4/3]')">
              <svg class="w-10 h-10 mb-2 text-pink-200" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M4 16l4.586-4.586a2 2 0 012.828 0L16 16m-2-2l1.586-1.586a2 2 0 012.828 0L20 14m-6-6h.01M6 20h12a2 2 0 002-2V6a2 2 0 00-2-2H6a2 2 0 00-2 2v12a2 2 0 002 2z" /></svg>
              <span class="text-[10px] uppercase font-bold tracking-widest text-pink-300">Foto {{ idx + 1 }}</span>
            </div>
            <div class="absolute inset-0 bg-black/40 opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-center justify-center pointer-events-none">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-10 w-10 text-white/80" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z" />
              </svg>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Karang Taruna -->
    <section id="karang-taruna" class="py-20 relative px-6 z-10 bg-white">
      <div class="max-w-7xl mx-auto">
        <div class="text-center mb-16">
          <span class="text-primary-pink-dark font-bold tracking-wider uppercase text-sm mb-2 block">Kolaborasi Pemuda</span>
          <h2 class="text-4xl font-bold mb-4">Bersama Karang Taruna Mutiara Hijau Desa Boidu</h2>
          <p class="text-gray-600 max-w-2xl mx-auto">Sinergi antara mahasiswa KKN dan Karang Taruna Mutiara Hijau dalam membangun program kerja yang bermakna bagi warga Desa Boidu.</p>
        </div>
        
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          <div v-for="doc in dokumentasiKarangTaruna" :key="doc.title" @click="selectedArticle = doc; showArticleModal = true" class="group relative overflow-hidden rounded-[2rem] shadow-md hover:shadow-2xl transition-all duration-300 cursor-pointer">
            <div class="aspect-[4/3] overflow-hidden bg-gradient-to-br from-gray-100 to-gray-50 flex items-center justify-center">
              <img v-if="doc.image" :src="doc.image" :alt="doc.title" class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-700" />
              <div v-else class="flex flex-col items-center gap-3 p-6 text-center">
                <svg class="w-16 h-16 text-gray-300" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1" d="M4 16l4.586-4.586a2 2 0 012.828 0L16 16m-2-2l1.586-1.586a2 2 0 012.828 0L20 14m-6-6h.01M6 20h12a2 2 0 002-2V6a2 2 0 00-2-2H6a2 2 0 00-2 2v12a2 2 0 002 2z" /></svg>
                <span class="text-gray-400 font-semibold text-xs uppercase tracking-wider">Foto Segera Hadir</span>
              </div>
            </div>
            <div class="absolute inset-0 bg-gradient-to-t from-black/80 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
            <div class="absolute bottom-0 left-0 right-0 p-6 translate-y-6 group-hover:translate-y-0 opacity-0 group-hover:opacity-100 transition-all duration-300">
              <h3 class="text-white font-bold text-xl">{{ doc.title }}</h3>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- CTA Penutup -->
    <section class="py-24 px-6 relative z-10">
      <!-- Airplane path trailing into CTA -->
      <svg class="absolute top-0 left-0 w-full h-full text-gray-200 z-[-1] pointer-events-none" viewBox="0 0 1000 400" fill="none" stroke="currentColor" stroke-width="4" stroke-dasharray="15 15">
        <path d="M 0 100 Q 500 300 1000 100" />
      </svg>
      
      <div class="max-w-5xl mx-auto flex flex-col md:flex-row bg-gradient-to-br from-primary-pink/10 to-pink-50 rounded-[3rem] overflow-hidden shadow-xl border border-pink-100">
        <div class="w-full md:w-1/2 p-12 md:p-16 flex flex-col justify-center">
          <h2 class="text-4xl md:text-5xl font-bold text-gray-900 mb-6">Kenali Tim Kami Lebih Dekat</h2>
          <p class="text-gray-600 text-lg mb-10">
            Membangun desa tanpa batas. Bersama kami, perubahan kecil menjadi langkah awal untuk kemajuan yang besar. Mari berkolaborasi!
          </p>
          <div>
            <a href="#kontak" class="inline-block bg-primary-pink-dark hover:bg-pink-700 text-white px-8 py-4 rounded-full font-bold text-lg shadow-lg shadow-pink-200 transition-colors">
              Hubungi Tim Kami
            </a>
          </div>
        </div>
        <div class="w-full md:w-1/2 relative min-h-[300px] bg-gradient-to-br from-pink-100 to-rose-50 flex items-center justify-center">
          <svg class="w-32 h-32 text-pink-200" fill="currentColor" viewBox="0 0 24 24"><path d="M17 20h5v-2a3 3 0 00-5.356-1.857M17 20H7m10 0v-2c0-.656-.126-1.283-.356-1.857M7 20H2v-2a3 3 0 015.356-1.857M7 20v-2c0-.656.126-1.283.356-1.857m0 0a5.002 5.002 0 019.288 0M15 7a3 3 0 11-6 0 3 3 0 016 0z"/></svg>
          <div class="absolute inset-0 bg-gradient-to-r from-pink-50 to-transparent"></div>
        </div>
      </div>
    </section>    <!-- Footer -->
    <footer id="kontak" class="bg-[#1e1e1e] text-gray-400 py-16 px-6 relative z-20">
      <div class="max-w-7xl mx-auto grid grid-cols-1 md:grid-cols-2 gap-12">
        <!-- Col 1: Powered By -->
        <div>
          <h4 class="font-bold text-white mb-6 text-sm uppercase tracking-wider">Powered By</h4>
          <div class="flex items-center gap-3">
            <div class="w-8 h-8 rounded-full bg-white flex items-center justify-center font-bold text-[#1e1e1e] text-xs">KKN</div>
            <span class="font-bold text-lg text-white">Tim Desa Boidu</span>
          </div>
        </div>
        
        <!-- Col 2: Call Center -->
        <div>
          <h4 class="font-bold text-white mb-6 text-sm uppercase tracking-wider">Call center</h4>
          <ul class="space-y-3 text-sm">
            <li>Informasi & Layanan Desa</li>
            <li class="text-white">+62 812 3456 7890</li>
          </ul>
        </div>
      </div>
      
      <!-- Bottom Bar -->
      <div class="max-w-7xl mx-auto border-t border-[#333] mt-16 pt-8 flex flex-col md:flex-row justify-between items-center text-xs text-gray-500 gap-6">
        <div class="flex gap-6">
          <a href="#" class="hover:text-white transition-colors">Privacy Policy</a>
          <a href="#" class="hover:text-white transition-colors">Cookies</a>
        </div>
        
        <div>
          &copy; 2026 All Rights Reserved.
        </div>
        
        <div class="flex items-center gap-4">
          <span class="mr-2">Connect with us</span>
          <!-- Twitter/X -->
          <a href="#" class="text-gray-400 hover:text-white transition-colors">
            <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24"><path d="M23.953 4.57a10 10 0 01-2.825.775 4.958 4.958 0 002.163-2.723c-.951.555-2.005.959-3.127 1.184a4.92 4.92 0 00-8.384 4.482C7.69 8.095 4.067 6.13 1.64 3.162a4.822 4.822 0 00-.666 2.475c0 1.71.87 3.213 2.188 4.096a4.904 4.904 0 01-2.228-.616v.06a4.923 4.923 0 003.946 4.827 4.996 4.996 0 01-2.212.085 4.936 4.936 0 004.604 3.417 9.867 9.867 0 01-6.102 2.105c-.39 0-.779-.023-1.17-.067a13.995 13.995 0 007.557 2.209c9.053 0 13.998-7.496 13.998-13.985 0-.21 0-.42-.015-.63A9.935 9.935 0 0024 4.59z"/></svg>
          </a>
          <!-- Instagram -->
          <a href="#" class="text-gray-400 hover:text-white transition-colors">
            <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24"><path fill-rule="evenodd" d="M12.315 2c2.43 0 2.784.013 3.808.06 1.064.049 1.791.218 2.427.465a4.902 4.902 0 011.772 1.153 4.902 4.902 0 011.153 1.772c.247.636.416 1.363.465 2.427.048 1.067.06 1.407.06 4.123v.08c0 2.643-.012 2.987-.06 4.043-.049 1.064-.218 1.791-.465 2.427a4.902 4.902 0 01-1.153 1.772 4.902 4.902 0 01-1.772 1.153c-.636.247-1.363.416-2.427.465-1.067.048-1.407.06-4.123.06h-.08c-2.643 0-2.987-.012-4.043-.06-1.064-.049-1.791-.218-2.427-.465a4.902 4.902 0 01-1.772-1.153 4.902 4.902 0 01-1.153-1.772c-.247-.636-.416-1.363-.465-2.427-.047-1.024-.06-1.379-.06-3.808v-.63c0-2.43.013-2.784.06-3.808.049-1.064.218-1.791.465-2.427a4.902 4.902 0 011.153-1.772A4.902 4.902 0 015.45 2.525c.636-.247 1.363-.416 2.427-.465C8.901 2.013 9.256 2 11.685 2h.63zm-.081 1.802h-.468c-2.456 0-2.784.011-3.807.058-.975.045-1.504.207-1.857.344-.467.182-.8.398-1.15.748-.35.35-.566.683-.748 1.15-.137.353-.3.882-.344 1.857-.047 1.023-.058 1.351-.058 3.807v.468c0 2.456.011 2.784.058 3.807.045.975.207 1.504.344 1.857.182.466.399.8.748 1.15.35.35.683.566 1.15.748.353.137.882.3 1.857.344 1.054.048 1.37.058 4.041.058h.08c2.597 0 2.917-.01 3.96-.058.976-.045 1.505-.207 1.858-.344.466-.182.8-.398 1.15-.748.35-.35.566-.683.748-1.15.137-.353.3-.882.344-1.857.048-1.055.058-1.37.058-4.041v-.08c0-2.597-.01-2.917-.058-3.96-.045-.976-.207-1.505-.344-1.858a3.097 3.097 0 00-.748-1.15 3.098 3.098 0 00-1.15-.748c-.353-.137-.882-.3-1.857-.344-1.023-.047-1.351-.058-3.807-.058zM12 6.865a5.135 5.135 0 110 10.27 5.135 5.135 0 010-10.27zm0 1.802a3.333 3.333 0 100 6.666 3.333 3.333 0 000-6.666zm5.338-3.205a1.2 1.2 0 110 2.4 1.2 1.2 0 010-2.4z" clip-rule="evenodd" /></svg>
          </a>
          <!-- Facebook -->
          <a href="#" class="text-gray-400 hover:text-white transition-colors">
            <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24"><path d="M22.675 0h-21.35C.597 0 0 .597 0 1.325v21.351C0 23.403.597 24 1.325 24H12.82v-9.294H9.692v-3.622h3.128V8.413c0-3.1 1.893-4.788 4.659-4.788 1.325 0 2.463.099 2.795.143v3.24l-1.918.001c-1.504 0-1.795.715-1.795 1.763v2.313h3.587l-.467 3.622h-3.12V24h6.116c.73 0 1.323-.597 1.323-1.325V1.325C24 .597 23.403 0 22.675 0z"/></svg>
          </a>
        </div>
      </div>
    </footer>
    
    <!-- Modal Anggota (Modern & Elegant) -->
    <transition
      enter-active-class="transition duration-300 ease-out"
      enter-from-class="opacity-0 scale-95"
      enter-to-class="opacity-100 scale-100"
      leave-active-class="transition duration-200 ease-in"
      leave-from-class="opacity-100 scale-100"
      leave-to-class="opacity-0 scale-95"
    >
      <div v-if="selectedMember" class="fixed inset-0 z-[100] flex items-center justify-center p-4 sm:p-6">
        <!-- Backdrop -->
        <div class="absolute inset-0 bg-gray-900/40 backdrop-blur-md" @click="selectedMember = null"></div>
        
        <!-- Modal Content -->
        <div class="bg-white rounded-[2.5rem] w-full max-w-4xl relative z-10 overflow-hidden shadow-2xl flex flex-col md:flex-row border border-white/50">
          
          <!-- Close Button -->
          <button @click="selectedMember = null" class="absolute top-4 right-4 md:top-6 md:right-6 w-10 h-10 bg-white/50 backdrop-blur-md hover:bg-white text-gray-800 rounded-full flex items-center justify-center transition-all z-30 shadow-sm hover:scale-110">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
              <path fill-rule="evenodd" d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z" clip-rule="evenodd" />
            </svg>
          </button>
          
          <!-- Image Section (Left on Desktop, Top on Mobile) -->
          <div class="w-full md:w-5/12 h-64 md:h-[450px] relative">
            <div class="absolute inset-0 bg-gradient-to-t from-black/60 to-transparent md:hidden z-10"></div>
            <img :src="selectedMember.image" :alt="selectedMember.name" class="w-full h-full object-cover" />
            <!-- Mobile Badge -->
            <div class="absolute bottom-4 left-4 z-20 md:hidden">
              <h3 class="font-bold text-2xl text-white drop-shadow-md">{{ selectedMember.name }}</h3>
              <p class="text-sm font-medium text-pink-200">{{ selectedMember.role }}</p>
            </div>
          </div>
          
          <!-- Content Section (Right on Desktop, Bottom on Mobile) -->
          <div class="w-full md:w-7/12 p-8 md:p-12 flex flex-col justify-center relative bg-gradient-to-br from-white to-pink-50/50">
            <!-- Large Quote Watermark -->
            <svg class="absolute top-8 right-8 w-32 h-32 text-pink-200/40 -rotate-12 pointer-events-none" fill="currentColor" viewBox="0 0 32 32">
              <path d="M10 8c-3.3 0-6 2.7-6 6v10h10V14H8c0-2.2 1.8-4 4-4V8zm16 0c-3.3 0-6 2.7-6 6v10h10V14h-6c0-2.2 1.8-4 4-4V8z"/>
            </svg>
            
            <div class="relative z-10 hidden md:block mb-8">
              <div class="inline-block px-4 py-1.5 rounded-full bg-primary-green/10 text-primary-green-dark font-bold text-xs mb-4 tracking-widest uppercase">
                {{ selectedMember.role }}
              </div>
              <h3 class="text-4xl md:text-5xl font-extrabold text-gray-900 mb-4 tracking-tight">{{ selectedMember.name }}</h3>
              <div class="w-16 h-1.5 bg-primary-pink rounded-full"></div>
            </div>
            
            <div class="relative z-10 flex-grow flex flex-col justify-center py-4 md:py-0">
              <p class="text-gray-700 text-lg md:text-2xl leading-relaxed font-serif italic relative z-10">
                <span class="text-primary-pink font-sans text-4xl leading-none absolute -top-4 -left-5">"</span>
                {{ selectedMember.tagline }}
                <span class="text-primary-pink font-sans text-4xl leading-none align-bottom -mb-4">"</span>
              </p>
            </div>
            
            <div class="relative z-10 mt-8 pt-6 border-t border-gray-200 flex items-center justify-between">
              <div class="flex gap-3">
                <!-- Social media icons -->
                <a href="#" class="w-10 h-10 rounded-full bg-white border border-gray-200 flex items-center justify-center text-gray-400 hover:border-pink-300 hover:text-primary-pink transition-all shadow-sm hover:shadow">
                  <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24"><path fill-rule="evenodd" d="M12.315 2c2.43 0 2.784.013 3.808.06 1.064.049 1.791.218 2.427.465a4.902 4.902 0 011.772 1.153 4.902 4.902 0 011.153 1.772c.247.636.416 1.363.465 2.427.048 1.067.06 1.407.06 4.123v.08c0 2.643-.012 2.987-.06 4.043-.049 1.064-.218 1.791-.465 2.427a4.902 4.902 0 01-1.153 1.772 4.902 4.902 0 01-1.772 1.153c-.636.247-1.363.416-2.427.465-1.067.048-1.407.06-4.123.06h-.08c-2.643 0-2.987-.012-4.043-.06-1.064-.049-1.791-.218-2.427-.465a4.902 4.902 0 01-1.772-1.153 4.902 4.902 0 01-1.153-1.772c-.247-.636-.416-1.363-.465-2.427-.047-1.024-.06-1.379-.06-3.808v-.63c0-2.43.013-2.784.06-3.808.049-1.064.218-1.791.465-2.427a4.902 4.902 0 011.153-1.772A4.902 4.902 0 015.45 2.525c.636-.247 1.363-.416 2.427-.465C8.901 2.013 9.256 2 11.685 2h.63zm-.081 1.802h-.468c-2.456 0-2.784.011-3.807.058-.975.045-1.504.207-1.857.344-.467.182-.8.398-1.15.748-.35.35-.566.683-.748 1.15-.137.353-.3.882-.344 1.857-.047 1.023-.058 1.351-.058 3.807v.468c0 2.456.011 2.784.058 3.807.045.975.207 1.504.344 1.857.182.466.399.8.748 1.15.35.35.683.566 1.15.748.353.137.882.3 1.857.344 1.054.048 1.37.058 4.041.058h.08c2.597 0 2.917-.01 3.96-.058.976-.045 1.505-.207 1.858-.344.466-.182.8-.398 1.15-.748.35-.35.566-.683.748-1.15.137-.353.3-.882.344-1.857.048-1.055.058-1.37.058-4.041v-.08c0-2.597-.01-2.917-.058-3.96-.045-.976-.207-1.505-.344-1.858a3.097 3.097 0 00-.748-1.15 3.098 3.098 0 00-1.15-.748c-.353-.137-.882-.3-1.857-.344-1.023-.047-1.351-.058-3.807-.058zM12 6.865a5.135 5.135 0 110 10.27 5.135 5.135 0 010-10.27zm0 1.802a3.333 3.333 0 100 6.666 3.333 3.333 0 000-6.666zm5.338-3.205a1.2 1.2 0 110 2.4 1.2 1.2 0 010-2.4z" clip-rule="evenodd" /></svg>
                </a>
                <a href="#" class="w-10 h-10 rounded-full bg-white border border-gray-200 flex items-center justify-center text-gray-400 hover:border-blue-300 hover:text-blue-600 transition-all shadow-sm hover:shadow">
                  <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24"><path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"/></svg>
                </a>
              </div>
              <span class="text-[10px] font-bold text-gray-400 uppercase tracking-[0.2em]">KKN Desa Boidu 2026</span>
            </div>
            
          </div>
        </div>
      </div>
    </transition>

    <!-- Modal Artikel Cerita Unggulan -->
    <transition
      enter-active-class="transition duration-400 ease-out"
      enter-from-class="opacity-0 translate-y-12"
      enter-to-class="opacity-100 translate-y-0"
      leave-active-class="transition duration-300 ease-in"
      leave-from-class="opacity-100 translate-y-0"
      leave-to-class="opacity-0 translate-y-12"
    >
      <div v-if="showArticleModal && selectedArticle" class="fixed inset-0 z-[110] flex items-center justify-center p-4 sm:p-6 md:p-12 overflow-y-auto pt-24 pb-12">
        <!-- Backdrop -->
        <div class="fixed inset-0 bg-gray-900/60 backdrop-blur-sm" @click="showArticleModal = false; selectedArticle = null"></div>
        
        <!-- Modal Content (Article) -->
        <div class="bg-white rounded-3xl w-full max-w-3xl relative z-10 shadow-2xl flex flex-col overflow-hidden my-auto">
          
          <!-- Close Button -->
          <button @click="showArticleModal = false; selectedArticle = null" class="absolute top-4 right-4 md:top-6 md:right-6 w-12 h-12 bg-black/40 hover:bg-black/60 backdrop-blur-md text-white rounded-full flex items-center justify-center transition-all z-30 shadow-md">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
            </svg>
          </button>
          
          <!-- Article Header Image -->
          <div class="w-full h-64 md:h-80 relative">
            <img v-if="selectedArticle.image" :src="selectedArticle.image" :alt="selectedArticle.title" class="w-full h-full object-cover" />
            <div v-else class="w-full h-full bg-gradient-to-br from-gray-100 to-gray-200 flex flex-col items-center justify-center gap-4">
              <svg class="w-20 h-20 text-gray-300" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1" d="M4 16l4.586-4.586a2 2 0 012.828 0L16 16m-2-2l1.586-1.586a2 2 0 012.828 0L20 14m-6-6h.01M6 20h12a2 2 0 002-2V6a2 2 0 00-2-2H6a2 2 0 00-2 2v12a2 2 0 002 2z" /></svg>
              <span class="text-gray-400 font-medium text-sm uppercase tracking-wider">Foto Segera Hadir</span>
            </div>
            <div class="absolute inset-0 bg-gradient-to-t from-black/80 via-black/20 to-transparent"></div>
            <div class="absolute bottom-6 left-6 right-6 md:bottom-8 md:left-10 md:right-10 text-white">
              <span class="bg-primary-green text-white text-xs font-bold px-3 py-1 rounded-full uppercase tracking-widest mb-3 inline-block">{{ selectedArticle.category }}</span>
              <h2 class="text-3xl md:text-4xl font-extrabold leading-tight">{{ selectedArticle.title }}</h2>
              <div class="flex items-center gap-2 mt-4 text-sm text-gray-300">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z" /></svg>
                {{ selectedArticle.date }}
              </div>
            </div>
          </div>
          
          <!-- Article Body -->
          <div class="p-6 md:p-10 text-gray-700 space-y-6 md:text-lg leading-relaxed bg-slate-50">
            <p>
              <span class="font-bold text-4xl float-left mr-2 mt-1 text-primary-pink-dark">{{ selectedArticle.description.charAt(0) }}</span>{{ selectedArticle.description.substring(1) }}
            </p>
            <p>
              Kegiatan ini dirancang bukan sekadar pelatihan biasa melainkan sebuah solusi nyata bagi setiap keluarga di Desa Boidu. Para ibu rumah tangga dan kepala keluarga diajak langsung untuk belajar cara menanam, merawat, dan memanen tanaman di lahan pekarangan sendiri, tanpa harus mengeluarkan biaya besar. Materi disampaikan secara praktis, ringan, dan mudah dipraktikkan di rumah.
            </p>
            
            <blockquote class="border-l-4 border-primary-green bg-white p-6 rounded-r-xl shadow-sm italic text-gray-800 my-8">
              "Kegiatan seperti ini bukan sekadar menjalankan program kerja. Ini menyentuh langsung kehidupan keluarga kami ketika pekarangan sendiri bisa menghasilkan kebutuhan dapur sehari-hari, itulah kemandirian yang sesungguhnya."
              <br/>
              <span class="block mt-3 text-sm font-bold text-gray-500 not-italic">Bpk. Masri Polihito (Kepala Desa Boidu)</span>
            </blockquote>
            
            <p>
              Harapan kami, setelah program <strong>{{ selectedArticle.title }}</strong> ini berjalan, setiap rumah tangga di Desa Boidu tidak lagi memandang pekarangan sebagai lahan tidur. Sebaliknya, ia menjadi aset produktif yang nyata tempat tumbuhnya kemandirian pangan keluarga, satu tanaman demi satu tanaman.
            </p>
            <p>
              Kami percaya, perubahan besar selalu dimulai dari langkah kecil di rumah. Dan bagi kami, bisa hadir mendampingi keluarga-keluarga Desa Boidu dalam langkah pertama itu adalah kehormatan yang tak ternilai.
            </p>
          </div>
          
        </div>
      </div>
    </transition>

  </div>
</template>

<style>
/* Smooth scrolling */
html {
  scroll-behavior: smooth;
}

/* Hide scrollbar for swiper containers */
.hide-scrollbar::-webkit-scrollbar {
  display: none;
}
.hide-scrollbar {
  -ms-overflow-style: none; /* IE and Edge */
  scrollbar-width: none; /* Firefox */
}
</style>
