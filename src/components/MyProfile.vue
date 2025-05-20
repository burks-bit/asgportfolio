<template>
    <header class="fixed top-0 w-full z-50 bg-white dark:bg-gray-900 shadow">
        <nav class="container mx-auto flex items-center justify-between p-4">
        <a href="/">
            <h1 class="text-xl font-bold">My Portfolio</h1>
        </a>
        
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
        <section id="home" class="hero-gradient text-white py-20 md:py-32">
            <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="flex flex-col md:flex-row items-center">
                    <div class="md:w-1/2 mb-10 md:mb-0">
                        <h1 class="text-4xl md:text-5xl font-bold mb-4">Albert Garcia</h1>
                        <h2 class="text-2xl md:text-3xl font-semibold mb-6">Web Developer</h2>
                        <p class="text-lg opacity-90 mb-8">Creating elegant solutions to complex problems with clean, efficient code.</p>
                        <div class="flex space-x-4">
                            <a href="#contact" class="bg-white text-indigo-600 px-6 py-3 rounded-full font-medium hover:bg-gray-100 transition">Get In Touch</a>
                            <a href="#projects" class="border-2 border-white text-white px-6 py-3 rounded-full font-medium hover:bg-white hover:bg-opacity-10 transition">View Projects</a>
                        </div>
                    </div>
                    <div class="md:w-1/2 flex justify-center">
                        <div class="w-64 h-64 md:w-80 md:h-80 rounded-full bg-white/20 flex items-center justify-center">
                            <div class="w-56 h-56 md:w-72 md:h-72 rounded-full bg-white/30 flex items-center justify-center">
                                <div class="w-48 h-48 md:w-64 md:h-64 rounded-full bg-white/40 flex items-center justify-center overflow-hidden">
                                    <img src="/myphoto1.jpg" alt="Albert Garcia" class="w-full h-full object-cover rounded-full border-4 border-white shadow-2xl">
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
                <div class="flex flex-col md:flex-row">
                    <div class="md:w-1/2 mb-8 md:mb-0 md:pr-8">
                        <p class="text-lg mb-6">
                            Currently thriving as a Junior Technical Engineer at I.T. Easy Software Solutions Inc., my role leverages a solid foundation in Computer Science, complemented by adeptness in Web Development, to deliver robust technical solutions.
                        </p>
                        <p class="text-lg mb-6">
                            The education at Bicol University Polangui Campus has been instrumental in shaping a mindset geared towards innovation and quality in the tech landscape.
                        </p>
                    </div>
                    <div class="md:w-1/2">
                        <p class="text-lg mb-6">
                            Driven by a commitment to excellence and a continuous improvement ethos, our team consistently aims to enhance user experiences and streamline operations.
                        </p>
                        <p class="text-lg">
                            Collaborating closely with colleagues, we navigate the complexities of modern software environments to solve pressing challenges and propel our organization forward.
                        </p>
                    </div>
                </div>
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
                    <div v-for="(exp, index) in experiences" :key="exp.title" class="timeline-item relative pl-16 pb-12">
                        <div class="absolute left-0 top-0 w-8 h-8 rounded-full bg-indigo-500 flex items-center justify-center text-white">
                            <i class="fas fa-briefcase"></i>
                        </div>
                        <div class="bg-gray-50 p-6 rounded-lg shadow-sm">
                            <div class="flex flex-col md:flex-row md:justify-between md:items-center mb-4">
                                <h3 class="text-xl font-semibold">{{ exp.title }}</h3>
                                <span class="text-indigo-600 font-medium">{{ exp.duration }}</span>
                            </div>
                            <h4 class="text-lg text-gray-600 mb-4">{{ exp.company }}</h4>
                            <ul class="list-disc pl-5 space-y-2 text-gray-700">
                                <li v-for="responsibility in exp.responsibilities">{{ responsibility }}</li>
                            </ul>
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
        { href: '#home', text: 'Home' },
        { href: '#about', text: 'About' },
        { href: '#skills', text: 'Skills' },
        { href: '#experience', text: 'Experience' },
        { href: '#projects', text: 'Projects' },
        { href: '#contact', text: 'Contact' }
    ]

    const skills = [
        {
            title: 'Frontend Development',
            items: [
                { name: 'HTML5', icon: 'fab fa-html5 text-orange-500' },
                { name: 'CSS3', icon: 'fab fa-css3-alt text-blue-500' },
                { name: 'JavaScript', icon: 'fab fa-js-square text-yellow-500' },
                { name: 'React.js', icon: 'fab fa-react text-blue-400' },
                { name: 'Vue.js', icon: 'fab fa-vuejs text-green-500' },
                { name: 'jQuery', icon: 'fas fa-code text-purple-500' },
                { name: 'Bootstrap', icon: 'fa-brands fa-bootstrap text-purple-500' },
            ]
        },
        {
            title: 'Backend Development',
            items: [
                { name: 'PHP', icon: 'fab fa-php text-purple-700' },
                { name: 'MySQL', icon: 'fas fa-database text-blue-600' },
                { name: 'Laravel', icon: 'fab fa-laravel text-red-500' },
                { name: 'CakePHP', icon: 'fas fa-birthday-cake text-pink-500' },
                { name: 'Node.js', icon: 'fab fa-node-js text-green-600' },
                // { name: 'Postman', icon: 'fab fa-postman text-orange-600' },
            ]
        },
        {
            title: 'Other Technologies',
            items: [
                { name: 'Git', icon: 'fab fa-git-alt text-orange-600' },
                { name: 'Apache', icon: 'fas fa-server text-gray-600' },
                { name: 'Linux', icon: 'fas fa-terminal text-gray-800' },
                { name: 'RESTful APIs', icon: 'fas fa-cloud text-blue-400' },
                { name: 'TCP/IP', icon: 'fas fa-network-wired text-blue-800' },
                { name: 'RS232/Ethernet', icon: 'fas fa-plug text-green-600' }
            ]
        },
        {
            title: 'Soft Skills',
            items: [
                { name: 'Communication', icon: 'fas fa-comments text-blue-500' },
                { name: 'Teamwork', icon: 'fas fa-users text-green-500' },
                { name: 'Problem Solving', icon: 'fas fa-brain text-purple-500' },
                { name: 'Multitasking', icon: 'fas fa-tasks text-yellow-500' },
                { name: 'Detail-Oriented', icon: 'fas fa-search text-indigo-500' }
            ]
        }
    ]

    function calculateDuration(start, end = new Date()) {
        const startDate = new Date(start);
        const endDate = new Date(end);

        let years = endDate.getFullYear() - startDate.getFullYear();
        let months = endDate.getMonth() - startDate.getMonth();

        if (months < 0) {
            years--;
            months += 12;
        }

        const yearStr = years > 0 ? `${years} year${years > 1 ? 's' : ''}` : '';
        const monthStr = months > 0 ? `${months} month${months > 1 ? 's' : ''}` : '';

        return [yearStr, monthStr].filter(Boolean).join(', ');
    }

    const experiences = [
        {
            title: 'Junior Technical Engineer',
            duration: `September 2022 - Present (${calculateDuration('2022-09-12')})`,
            company: 'I.T. Easy Software Solutions Inc.',
            responsibilities: [
                'Develop and maintain web applications using Laravel and CakePHP frameworks',
                'Design and optimize MySQL databases for performance and scalability',
                'Implement front-end interfaces with React.js and Vue.js',
                'Collaborate with cross-functional teams to deliver high-quality software solutions',
                'Configure and maintain Linux servers and web hosting environments'
            ]
        },
        {
            title: 'I.T. Officer',
            duration: `February 2019 - August 2022 (${calculateDuration('2019-02-01', '2022-08-31')})`,
            company: 'Zone Medical and Intervention Hospital, Inc.',
            responsibilities: [
                "Manage and maintain the hospital's information technology infrastructure",
                "Ensure the smooth functioning of the hospital's computer network",
                "Train staff on the efficient and secure use of EMR systems",
                "Provide technical support for computer hardware and software used in the hospital",
                "Troubleshoot and resolve network issues promptly",
                "Conduct training programs to enhance hospital staff's IT skills and awareness",
                "Maintain comprehensive documentation for all IT systems and procedures"
            ]
        },
    ]

    const projects = [
        {
            title: 'Clinical Management System',
            description: 'A clinical management system built to streamline consultations, prescriptions, and medical records using modern web technologies.',
            colorClass: 'bg-indigo-100',
            textColor: 'text-indigo-500',
            icon: 'fas fa-hospital',
            technologies: ['Vue.js', 'Laravel', 'MySQL'],
            badgeColor: 'bg-indigo-200'
        },
        {
            title: 'Clinical Management System',
            description: 'A clinical management system built to streamline consultations, prescriptions, and medical records using modern web technologies.',
            colorClass: 'bg-indigo-100',
            textColor: 'text-indigo-500',
            icon: 'fas fa-hospital',
            technologies: ['Vue.js', 'Laravel', 'MySQL'],
            badgeColor: 'bg-indigo-200'
        },
        // Add more project entries if needed
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