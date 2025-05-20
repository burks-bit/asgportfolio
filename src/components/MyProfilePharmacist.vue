<template>
    <header class="fixed top-0 w-full z-50 bg-white dark:bg-gray-900 shadow">
        <nav class="container mx-auto flex items-center justify-between p-4">
        <h1 class="text-xl font-bold">My Portfolio</h1>
        
        <!-- Hamburger Menu Button -->
        <button class="md:hidden" @click="toggleMobileMenu">
            <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-6 w-6"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
            >
            <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M4 6h16M4 12h16M4 18h16"
            />
            </svg>
        </button>

            <!-- Desktop Nav -->
            <ul class="hidden md:flex space-x-6">
                <li v-for="link in links" :key="link">
                <a
                    :href="'#' + link.toLowerCase()"
                    class="text-gray-700 hover:text-blue-500"
                    @click="scrollToSection(link)"
                >
                    {{ link }}
                </a>
                </li>
            </ul>
        </nav>

        <!-- Mobile Nav -->
        <ul
            v-if="showMobileMenu"
            class="md:hidden bg-white dark:bg-gray-900 px-4 pb-4 space-y-2"
        >
            <li v-for="link in links" :key="link">
                <a
                    :href="'#' + link.toLowerCase()"
                    class="block text-gray-700 hover:text-blue-500"
                    @click="handleMobileLinkClick(link)"
                >
                {{ link }}
                </a>
            </li>
        </ul>
    </header>

    <!-- Hero Section -->
    <section class="hero-gradient text-white py-20 md:py-32 bg-gradient-to-r from-indigo-600 to-indigo-800 relative overflow-hidden">
        <!-- Animated Background Gradient -->
        <div class="absolute inset-0 bg-gradient-to-r from-indigo-600 to-indigo-800 opacity-50 animate-gradient-pulse"></div>

        <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
            <div class="flex flex-col md:flex-row items-center">
                <!-- Text Content -->
                <div class="md:w-1/2 mb-10 md:mb-0 text-center md:text-left">
                    <h1 class="text-4xl font-bold mb-2 animate-fade-in-down text-shadow-lg">Daine Macalintal, RPh</h1>
                    <p class="text-lg text-white/80 animate-fade-in text-shadow-md">Pharmacovigilance & Safety Science Professional</p>
                    <!-- Button Section -->
                    <div class="flex justify-center md:justify-start space-x-4 mt-6">
                        <a href="#contact" class="bg-white text-indigo-600 px-6 py-3 rounded-full font-medium hover:bg-indigo-100 hover:scale-105 transition-all">Get In Touch</a>
                        <a href="#projects" class="border-2 border-white text-white px-6 py-3 rounded-full font-medium hover:bg-white hover:bg-opacity-10 hover:scale-105 transition-all">View Projects</a>
                    </div>
                    <!-- Scroll Indicator -->
                    <div class="mt-8 text-white text-2xl animate-bounce">
                        <a href="#projects">
                            <svg xmlns="http://www.w3.org/2000/svg" class="w-8 h-8 mx-auto" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"></path>
                            </svg>
                        </a>
                    </div>
                </div>

                <!-- Profile Image -->
                <div class="md:w-1/2 flex justify-center">
                    <div class="w-64 h-64 md:w-80 md:h-80 rounded-full bg-white/20 flex items-center justify-center">
                        <div class="w-56 h-56 md:w-72 md:h-72 rounded-full bg-white/30 flex items-center justify-center">
                            <div class="w-48 h-48 md:w-64 md:h-64 rounded-full bg-white/40 flex items-center justify-center overflow-hidden">
                                <img src="/daine.jpg" alt="Daine Macalintal" class="w-full h-full object-cover rounded-full border-4 border-white shadow-2xl">
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>




    <!-- About Section -->
    <section id="about" class="py-16 bg-white">
        <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
            <h2 class="text-3xl font-bold text-center mb-12">Who I Am</h2>
            <p class="text-lg mb-6">
                I am a licensed pharmacist committed to providing top-quality pharmaceutical care and promoting patient safety. With a background in community and clinical settings, I bring hands-on experience in dispensing, counseling, and medication therapy management.
            </p>
            <p class="text-lg mb-6">
                A graduate of Bicol University Polangui Campus, I am constantly driven to expand my knowledge in pharmaceutical sciences and the evolving role of technology in healthcare.
            </p>
        </div>
    </section>
    <!-- Skills Section -->
    <section id="skills" class="py-16 bg-gray-50">
        <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
            <h2 class="text-3xl font-bold text-center mb-12">Skills & Expertise</h2>
            
            <div v-for="skillGroup in skills" :key="skillGroup.title" class="mb-12">
                <h3 class="text-xl font-semibold mb-6 text-gray-800">{{ skillGroup.title }}</h3>
                <div class="flex flex-wrap gap-4">
                    <div v-for="skill in skillGroup.items" :key="skill.name" class="skill-badge bg-white px-6 py-3 rounded-full shadow-md flex items-center transition duration-300">
                        <i :class="skill.icon" class="text-2xl mr-2"></i>
                        <span>{{ skill.name }}</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Experience Section -->
    <section id="experience" class="py-16 bg-white">
        <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
            <h2 class="text-3xl font-bold text-center mb-12">Work Experience</h2>
            <div class="relative">
                <div
                    v-for="(exp, index) in experiences"
                    :key="index"
                    class="timeline-company pb-12"
                >
                    <div
                        v-for="(role, idx) in exp.roles"
                        :key="idx"
                        class="timeline-item relative pl-16 pb-8"
                    >
                        <div
                            class="absolute left-0 top-0 w-8 h-8 rounded-full bg-indigo-500 flex items-center justify-center text-white"
                        >
                            <i class="fas fa-briefcase"></i>
                        </div>
                        <div class="bg-gray-50 p-6 rounded-lg shadow-sm">
                            <div
                                class="flex flex-col md:flex-row md:justify-between md:items-center mb-2"
                            >
                                <h3 class="text-xl font-semibold">{{ role.title }}</h3>
                                <span class="text-indigo-600 font-medium">{{ role.date }}</span>
                            </div>
                            <h4 class="text-lg text-gray-600 mb-4">{{ exp.company }}</h4>
                            <ul class="list-disc pl-5 space-y-2 text-gray-700">
                                <li v-for="(responsibility, i) in role.description" :key="i">
                                    {{ responsibility }}
                                </li>
                            </ul>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Projects Section -->
    <section id="projects" class="py-16 bg-gray-50">
        <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
            <h2 class="text-3xl font-bold text-center mb-12">Featured Projects</h2>
            
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-2 gap-8">
                <div v-for="project in projects" :key="project.title" class="project-card bg-white rounded-lg overflow-hidden shadow-md transition duration-300">
                    <div :class="`h-48 ${project.colorClass} flex items-center justify-center`">
                        <i :class="`${project.icon} text-6xl ${project.textColor}`"></i>
                    </div>
                    <div class="p-6">
                        <h3 class="text-xl font-bold mb-2">{{ project.title }}</h3>
                        <p class="text-gray-600 mb-4">{{ project.description }}</p>
                        <div class="flex flex-wrap gap-2">
                            <span v-for="tech in project.technologies" :key="tech" :class="`px-3 py-1 ${project.badgeColor} rounded-full text-sm`">{{ tech }}</span>
                        </div>
                        <div class="pt-3">
                            <button
                                class="text-xs font-medium border border-gray-300 focus:outline-none text-dark px-4 py-2 rounded-full hover:bg-blue-600 hover:text-white transition flex items-center gap-2"
                                @click="viewProjectSlide"
                            >
                                <i class="fa fa-eye"></i>
                                View Slide
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="py-16 bg-white">
        <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
            <h2 class="text-3xl font-bold text-center mb-12">Get In Touch</h2>
            <p class="text-center text-lg mb-12 max-w-2xl mx-auto">
                Feel free to reach out if you're looking for a developer, have a question, or just want to connect.
            </p>
            
            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <div v-for="contact in contacts" :key="contact.type" class="contact-card bg-gray-50 p-8 rounded-lg shadow-lg text-center hover:shadow-md transition duration-300">
                    <div :class="`contact-icon ${contact.iconBgClass} w-16 h-16 rounded-full flex items-center justify-center mx-auto mb-6`">
                        <i :class="`${contact.icon} ${contact.iconTextColor} text-2xl`"></i>
                    </div>
                    <h3 class="text-xl font-semibold mb-2">{{ contact.type }}</h3>
                    <p class="text-gray-600 mb-4">{{ contact.value }}</p>
                    <a :href="contact.link" :class="`${contact.linkColor} hover:${contact.linkHoverColor} font-medium`">{{ contact.actionText }}</a>
                </div>
            </div>
        </div>
    </section>

     <!-- Dialog Overlay and Box -->
    <transition name="fade-zoom">
        <div
            v-if="showDialog"
            class="fixed inset-0 z-50 flex items-center justify-center bg-black bg-opacity-50"
        >
            <div
                class="bg-white p-6 rounded-lg shadow-xl w-full max-w-md relative transform transition-all duration-500 ease-out scale-95 opacity-0"
                :class="{ 'scale-100 opacity-100': showDialog }"
            >
            <!-- Close Button -->
            <button
                class="absolute top-2 right-2 text-gray-500 hover:text-gray-800"
                @click="closeDialog"
            >
                &times;
            </button>
            <h2 class="text-lg font-semibold mb-4">Project Slide</h2>
            <p>This is your slide content or preview.</p>
            </div>
        </div>
    </transition>
</template>
<script setup>
    import { ref, onMounted, onBeforeUnmount } from 'vue'

    const showMobileMenu = ref(false)
    const links = ['Home', 'About', 'Skills', 'Experience', 'Projects', 'Contact']
    const showDialog = ref(false)

    const toggleMobileMenu = () => {
        showMobileMenu.value = !showMobileMenu.value
    }

    const scrollToSection = (sectionId) => {
        const section = document.getElementById(sectionId.toLowerCase())
        if (section) {
            section.scrollIntoView({ behavior: 'smooth' })
        }
    }

    const handleMobileLinkClick = (sectionId) => {
        scrollToSection(sectionId)
        showMobileMenu.value = false
    }

    const navLinks = [
        { href: '#about', text: 'About' },
        { href: '#skills', text: 'Skills' },
        { href: '#experience', text: 'Experience' },
        { href: '#projects', text: 'Projects' },
        { href: '#contact', text: 'Contact' }
    ]

    const skills = [
        {
            title: 'Pharmaceutical Knowledge',
            items: [
                { name: 'Drug Dispensing', icon: 'fas fa-pills text-blue-500' },
                { name: 'Medication Counseling', icon: 'fas fa-user-md text-green-500' },
                { name: 'Pharmacovigilance', icon: 'fas fa-eye text-red-500' },
                { name: 'Inventory Management', icon: 'fas fa-boxes text-yellow-500' }
            ]
        },
        {
            title: 'Healthcare Systems & Tools',
            items: [
                { name: 'Pharmacy Information Systems', icon: 'fas fa-desktop text-purple-500' },
                { name: 'Electronic Prescriptions (eRx)', icon: 'fas fa-file-prescription text-indigo-600' },
                { name: 'HL7 & EMR Integration', icon: 'fas fa-notes-medical text-teal-600' }
            ]
        },
        {
            title: 'Soft Skills',
            items: [
                { name: 'Patient Communication', icon: 'fas fa-comments text-blue-400' },
                { name: 'Attention to Detail', icon: 'fas fa-search text-pink-500' },
                { name: 'Ethical Practice', icon: 'fas fa-balance-scale text-gray-600' }
            ]
        }
    ]


    function calculateDuration(start, end = new Date()) {
    const startDate = new Date(start);
    const endDate = new Date(end);

    let years = endDate.getFullYear() - startDate.getFullYear();
    let months = endDate.getMonth() - startDate.getMonth();
    let days = endDate.getDate() - startDate.getDate();

    if (days < 0) {
        months--;
        const previousMonthDays = new Date(endDate.getFullYear(), endDate.getMonth(), 0).getDate();
        days += previousMonthDays;
    }

    if (months < 0) {
        years--;
        months += 12;
    }

    const yearStr = years > 0 ? `${years} year${years > 1 ? 's' : ''}` : '';
    const monthStr = months > 0 ? `${months} month${months > 1 ? 's' : ''}` : '';

    return [yearStr, monthStr].filter(Boolean).join(', ') || 'Less than a month';
}

const experiences = [
    {
        company: "Fortrea",
        roles: [
            {
                title: "Safety Science Analyst II",
                date: `Apr 2025 - Present (${calculateDuration('2025-04-01')})`,
                description: [
                    "Handles case processing with a focus on adverse event reporting, product quality complaints, and medical information inquiries.",
                    "Ensures regulatory compliance and patient safety through comprehensive documentation.",
                    "Contributes to continuous process improvement within pharmacovigilance operations."
                ]
            },
            {
                title: "Safety Science Analyst I",
                date: `Aug 2022 - Apr 2025 (${calculateDuration('2022-08-01', '2025-04-01')})`,
                description: [
                    "Managed general and medical inquiries for pharmaceutical products.",
                    "Worked with global pharmaceutical clients in a Contract Research Organization (CRO) setting.",
                    "Specialized in case intake, data entry, triage, and follow-up communication."
                ]
            }
        ]
    },
    {
        company: "WATSONS PERSONAL CARE STORES (PHILIPPINES), INC.",
        roles: [
            {
                title: "Store Pharmacist",
                date: `May 2022 - Aug 2022 (${calculateDuration('2022-05-01', '2022-08-01')})`,
                description: [
                    "Provided medication counseling and ensured proper dispensing practices.",
                    "Maintained inventory and compliance with pharmacy regulations."
                ]
            }
        ]
    },
    {
        company: "Celltrion Inc.",
        roles: [
            {
                title: "Pharmacovigilance Associate",
                date: `Feb 2022 - Apr 2022 (${calculateDuration('2022-02-01', '2022-04-30')})`,
                description: [
                    "Performed data entry in Argus Safety for adverse event reports.",
                    "Assisted in processing and documentation of pharmacovigilance cases."
                ]
            }
        ]
    },
    {
        company: "Metrocare Pharmacy",
        roles: [
            {
                title: "Pharmacy Assistant",
                date: `Jun 2021 - Aug 2021 (${calculateDuration('2021-06-01', '2021-08-30')})`,
                description: [
                    "Assisted in dispensing medications and patient counseling.",
                    "Maintained cleanliness and organization of pharmacy shelves."
                ]
            }
        ]
    },
    {
        company: "Planet Drugstore Corporation",
        roles: [
            {
                title: "Community Pharmacy Intern",
                date: "Internship",
                description: [
                    "Gained hands-on experience in retail pharmacy operations."
                ]
            }
        ]
    }
];



    const projects = [
        {
            title: 'Medication Reminder App',
            description: 'A mobile app helping patients manage medication schedules and dosages.',
            technologies: ['Vue.js', 'Firebase', 'Push Notifications'],
            icon: 'fas fa-capsules',
            colorClass: 'bg-blue-200',
            textColor: 'text-blue-700',
            badgeColor: 'bg-blue-100 text-blue-600',
        },
        {
            title: 'Pharmacy Inventory Tracker',
            description: 'A web-based tool for monitoring drug stock levels and expiry dates.',
            technologies: ['Laravel', 'MySQL', 'Tailwind CSS'],
            icon: 'fas fa-warehouse',
            colorClass: 'bg-green-200',
            textColor: 'text-green-700',
            badgeColor: 'bg-green-100 text-green-600',
        }
    ]

    const contacts = [
        {
            type: 'Email',
            value: 'bertnet08@gmail.com',
            icon: 'fas fa-envelope',
            iconBgClass: 'bg-indigo-100',
            iconTextColor: 'text-indigo-500',
            link: 'mailto:albert@example.com',
            linkColor: 'text-indigo-600',
            linkHoverColor: 'text-indigo-800',
            actionText: 'Send a Message'
        },
        {
            type: 'Phone',
            value: '+63 965 284 5007',
            icon: 'fas fa-phone-alt',
            iconBgClass: 'bg-green-100',
            iconTextColor: 'text-green-500',
            link: 'tel:+639123456789',
            linkColor: 'text-green-600',
            linkHoverColor: 'text-green-800',
            actionText: 'Call Now'
        },
        {
            type: 'LinkedIn',
            value: 'linkedin.com/in/asgdev',
            icon: 'fab fa-linkedin',
            iconBgClass: 'bg-blue-100',
            iconTextColor: 'text-blue-500',
            link: 'https://www.linkedin.com/in/asgdev',
            linkColor: 'text-blue-600',
            linkHoverColor: 'text-blue-800',
            actionText: 'Connect'
        }
    ]

    const socialLinks = [
        { icon: 'facebook-f' },
        { icon: 'twitter' },
        { icon: 'linkedin-in' },
        { icon: 'github' }
    ]

    function viewProjectSlide() {
        showDialog.value = true
    }

    function closeDialog() {
        showDialog.value = false
    }

</script>

<style>
    html {
        scroll-behavior: smooth;
    }
    .hero-gradient {
        background: linear-gradient(135deg, #1e0144 0%, #764ba2 100%);
    }
    .skill-badge:hover {
        transform: translateY(-3px);
        box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
    }
    .timeline-item:not(:last-child)::after {
        content: '';
        position: absolute;
        left: 1.5rem;
        top: 3.5rem;
        height: calc(100% - 3.5rem);
        width: 2px;
        background: #e5e7eb;
    }
    .project-card:hover {
        transform: translateY(-5px);
        box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1);
    }
    .contact-icon {
        transition: all 0.3s ease;
    }
    .contact-card:hover .contact-icon {
        transform: scale(1.2);
    }
    .fade-zoom-enter-active, .fade-zoom-leave-active {
        transition: all 0.5s ease;
    }
    .fade-zoom-enter-from, .fade-zoom-leave-to {
        opacity: 0;
        transform: scale(0.95);
    }
    .fade-zoom-enter-to, .fade-zoom-leave-from {
        opacity: 1;
        transform: scale(1);
    }
</style>