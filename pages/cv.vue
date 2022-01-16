<template>
    <div class="cv h-screen overflow-auto bg-darkblue relative">
        <div class="flex flex-col max-w-5xl my-32 mx-5 lg:mx-auto rounded-xl">
            <div class="header relative flex flex-col justify-center items-center lg:items-start rounded-t-xl p-8 lg:p-12">
                <img class="profile-pic lg:absolute" src="/profile.jpg">
                <h1 class="text-white text-2xl lg:text-4xl font-bold mb-4">Matija Jeras</h1>
                <h2 class="text-white text-md lg:text-l">Software developer with a passion for frontend</h2>
                <!-- <button class="print absolute bg-white text-navyblue no-print" @click="print()"><font-awesome-icon :icon="['fas', 'print']"/></button> -->
            </div>
            <div class="section flex flex-col lg:flex-row p-6 lg:p-12 bg-white">
                <div class="flex flex-col flex-1 items-start pr-6">
                    <h3 class="text-2xl font-bold mb-6 lg:mb-12">About me</h3>
                    <p class="flex text-left text-sm">I am Matija Jeras, software developer focused on frontend code that enables me to program a clean and intuitive web based applications.</p>
                </div>
                <div class="flex flex-col justify-around flex-1 text-sm pt-6 lg:pl-6">
                    <div class="flex justify-between mb-2">
                        <span class="font-bold">Age</span>
                        <span>28</span>
                    </div>
                    <div class="flex justify-between mb-2">
                        <span class="font-bold">Email</span>
                        <span>matija.jeras64@gmail.com</span>
                    </div>
                    <div class="flex justify-between mb-2">
                        <span class="font-bold">Location</span>
                        <span>Ljubljana, Slovenia</span>
                    </div>
                </div>
            </div>
            <div class="section flex flex-col p-6 lg:p-12 bg-white">
                <h3 class="text-2xl font-bold text-left mb-6 lg:mb-12">Professional skills</h3>
                <div class="flex flex-col lg:flex-row">
                    <div class="flex flex-1 flex-col lg:pr-6">
                        <div class="flex flex-col mb-4">
                            <span class="text-left">Vue</span>
                            <div class="flex h-4 bg-offwhite rounded-md"><div class="w-10/12 h-full bg-darkgreen rounded-l-md"></div></div>
                        </div>
                        <div class="flex flex-col mb-4">
                            <span class="text-left">React</span>
                            <div class="flex h-4 bg-offwhite rounded-md"><div class="w-8/12 h-full bg-darkgreen rounded-l-md"></div></div>
                        </div>
                        <div class="flex flex-col mb-4">
                            <span class="text-left">Angular</span>
                            <div class="flex h-4 bg-offwhite rounded-md"><div class="w-9/12 h-full bg-darkgreen rounded-l-md"></div></div>
                        </div>
                    </div>
                    <div class="flex flex-1 flex-col pt-6 lg:pt-0 lg:pl-6">
                        <div class="flex flex-col mb-4">
                            <span class="text-left">CSS</span>
                            <div class="flex h-4 bg-offwhite rounded-md"><div class="w-11/12 h-full bg-teal rounded-l-md"></div></div>
                        </div>
                        <div class="flex flex-col mb-4">
                            <span class="text-left">Node</span>
                            <div class="flex h-4 bg-offwhite rounded-md"><div class="w-9/12 h-full bg-teal rounded-l-md"></div></div>
                        </div>
                        <div class="flex flex-col mb-4">
                            <span class="text-left">Go</span>
                            <div class="flex h-4 bg-offwhite rounded-md"><div class="w-5/12 h-full bg-teal rounded-l-md"></div></div>
                        </div>
                    </div>
                </div>
            </div>
            <div class="section work flex flex-col p-6 lg:p-12 bg-white">
                <h3 class="text-2xl font-bold text-left mb-6 lg:mb-12">Work experience</h3>
                <div class="timeline flex flex-col">
                    <div class="card relative flex flex-col items-start ml-10 mb-10 p-5 lg:p-10 rounded-md">
                        <div class="flex flex-col lg:flex-row mb-5">
                            <span class="text-md lg:text-xl text-left font-bold">Frontend Developer</span>
                            <span class="text-md lg:text-xl text-left text-dark lg:ml-2">at Oryx Gaming</span>
                        </div>
                        <span class="text-xs lg:text-sm mb-5">Apr 2017 - May 2019</span>
                        <p class="text-md text-left">Developing websites in vanilla HTML, CSS and Javascript, later with Vue.js. Leading a small CMS team to develop, maintain and upgrade custom CMS (PHP, Laravel).</p>
                    </div>
                    <div class="card relative flex flex-col items-start ml-10 mb-10 p-5 lg:p-10 rounded-md">
                        <div class="flex flex-col lg:flex-row mb-5">
                            <span class="text-md lg:text-xl text-left font-bold">Fullstack Developer</span>
                            <span class="text-md lg:text-xl text-left text-dark lg:ml-2">at 1Home</span>
                        </div>
                        <span class="text-xs lg:text-sm mb-5">May 2019 - Jan 2021</span>
                        <p class="text-md mb-2 text-left">Web application development with Vue.js, Node.js and MongoDB, writing Node.js and GoLang for IOT devices (Raspberry Pi 3&4), IOT devices fleet control & management (Balena + OpenBalena).</p>
                        <p class="text-md mb-2 text-left">Configuring and connecting to smart home servers (KNX, Loxone, GiraHS, GiraX1), writing javascript code for smart assistants APIs (Google Home, Amazon Alexa, Apple Homekit) and integrating them into our system.</p>
                        <p class="text-md text-left">Helping with customer support and solving issues directly with clients (Intercom).</p>
                    </div>
                    <div class="card relative flex flex-col items-start ml-10 mb-10 p-5 lg:p-10 rounded-md">
                        <div class="flex flex-col lg:flex-row mb-5">
                            <span class="text-md lg:text-xl text-left font-bold">Senior Developer</span>
                            <span class="text-md lg:text-xl text-left text-dark lg:ml-2">at Endava</span>
                        </div>
                        <span class="text-xs lg:text-sm mb-5">Jan 2021 - Present</span>
                        <p class="text-md mb-2 text-left">Extending an Angular web application that enables user to interact with a hardware device and displays data/statistics with graphs (Plotly).</p>
                        <p class="text-md mb-2 text-left">Rewriting components from Angular to React (Next.js - SSR) to help with SEO performance.</p>
                        <p class="text-md text-left">Improving performance of an Anuglar landing page using Lighthouse.</p>
                    </div>
                </div>
            </div>
            <div class="section education flex flex-col p-6 lg:p-12 bg-white">
                <h3 class="text-2xl font-bold text-left mb-6 lg:mb-12">Education</h3>
                <div class="timeline flex flex-col">
                    <div class="card relative flex flex-col items-start ml-10 mb-10 p-5 lg:p-10 rounded-md">
                        <div class="flex flex-col lg:flex-row mb-5">
                            <span class="text-md lg:text-xl text-left font-bold">Bachelor of Computer Science</span>
                            <span class="text-md lg:text-xl text-left text-dark lg:ml-2">at Faculty of Computer and Information Science</span>
                        </div>
                        <span class="text-xs lg:text-sm mb-5">2013 - 2017</span>
                        <p class="text-md text-left">Focusing on web technologies and making a diploma on visualizing music on HTML 5 canvas with WebGL.</p>
                    </div>
                </div>
            </div>
            <div class="section education flex flex-col p-6 lg:p-12 bg-white rounded-b-xl">
                <div class="flex flex-col lg:flex-row lg:items-center">
                    <form class="flex flex-col flex-1 lg:items-start" action="mailto:matija.jeras64@gmail.com" method="POST" enctype="multipart/form-data" name="EmailForm">
                        <h3 class="text-2xl font-bold text-left mb-12">Contact</h3>
                        <div class="flex flex-col lg:flex-row justify-between w-full mb-5">
                            <input class="input flex-1" type="text" size="19" name="name" placeholder="Your name">
                            <input class="input flex-1 mt-2 lg:mt-0 lg:ml-5" type="text" size="19" name="email" placeholder="Your email">
                        </div>
                        <textarea class="input w-full mb-5" name="message" rows="5" cols="20" placeholder="Your message"></textarea>
                        <input class="button" type="submit" value="Send">
                    </form>
                    <div class="flex flex-col flex-1 items-center mt-10 lg:mt-0">
                        <span class="text-xl font-bold text-grey mb-5">Matija Jeras</span>
                        <div class="flex text-grey">
                            <a class="icon px-3 text-xl hover:text-black" href="https://github.com/Quattro04" target="_blank"><font-awesome-icon :icon="['fab', 'github']"/></a>
                            <a class="icon px-3 text-xl hover:text-teal" href="https://www.linkedin.com/in/matija-jeras/" target="_blank"><font-awesome-icon :icon="['fab', 'linkedin-in']"/></a>
                            <a class="icon px-3 text-xl hover:text-lightblue" href="https://www.facebook.com/matija.jeras01" target="_blank"><font-awesome-icon :icon="['fab', 'facebook-f']"/></a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    transition: {
        name: 'fade',
        mode: 'out-in'
    },
    methods: {
        print() {
            window.print();
        }
    }
}
</script>

<style lang="scss">
    .cv {
        .header {
            background:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' height='100%25' width='100%25'%3E%3Cdefs%3E%3Cpattern id='doodad' width='15' height='15' viewBox='0 0 40 40' patternUnits='userSpaceOnUse' patternTransform=''%3E%3Crect width='100%25' height='100%25' fill='rgba(47, 133, 90,1)'/%3E%3Cpath d='M0 40h-10v-60h60L40 0L38 1h-36v38z' fill='rgba(56, 161, 105,1)'/%3E%3Cpath d='M40 0v10h60v60L0 40L2 39h36v-38z' fill='rgba(47, 133, 90,1)'/%3E%3Cpath d='M40 0v10h60v60L0 40L0 40h40v-40z' fill='rgba(56, 161, 105,1)'/%3E%3Cpath d='M0 40h-10v-60h60L40 0L40 0h-40v40z' fill='rgba(47, 133, 90,1)'/%3E%3C/pattern%3E%3C/defs%3E%3Crect fill='url(%23doodad)' height='200%25' width='200%25'/%3E%3C/svg%3E ");

            .profile-pic {
                width: 160px;
                height: 151px;
                left: 5%;
                bottom: -10%;
                border: 10px solid white;
                -webkit-box-shadow: 0px 0px 5px 0px #828282; 
                box-shadow: 0px 0px 5px 0px #828282;
                @media(max-width: 1023px) {
                    width: 120px;
                    height: 113px;
                    margin-bottom: 1rem;
                }
            }
            h1,
            h2 {
                margin-left: 30%;
                @media(max-width: 1023px) {
                    margin-left: 0;
                }
            }
            .print {
                width: 40px;
                height: 40px;
                top: 1rem;
                right: 1rem;
                border-radius: 50%;
                font-size: 20px;
            }
        }
        .section {
            border-bottom: 1px solid rgb(228, 228, 228);
            &:last-child {
                border: none;
            }
        }
        .timeline {
            border-left: 2px solid #E6E9ED;
            .card {
                border: 1px solid #E6E9ED;
                border-left: 2px solid #5faac7;
                &::before {
                    content: '';
                    display: inline-block;
                    position: absolute;
                    background-color: #fff;
                    border-radius: 10px;
                    width: 12px;
                    height: 12px;
                    top: 20px;
                    left: -49px;
                    z-index: 2;
                }
                &::after {
                    content: '';
                    display: inline-block;
                    position: absolute;
                    width: 37px;
                    height: 2px;
                    top: 25px;
                    left: -37px;
                    z-index: 1;
                }
            }
        }
        .work .timeline .card {
            border-left: 2px solid #5faac7;
            &::before {
                border: 2px solid #5faac7;
            }
            &::after {
                background-color: #5faac7;
            }
        }
        .education .timeline .card {
            border-left: 2px solid #00d37b;
            &::before {
                border: 2px solid #00d37b;
            }
            &::after {
                background-color: #00d37b;
            }
        }

        .education {
            .input {
                padding: 0.375rem 0.75rem;
                font-size: 1rem;
                font-weight: 400;
                line-height: 1.5;
                color: #434a54;
                background-color: #f8f9fa;
                background-clip: padding-box;
                border: 2px solid #dee2e6;
                -webkit-appearance: none;
                -moz-appearance: none;
                appearance: none;
                border-radius: 0.25rem;
                &:focus {
                    outline-color: #5faac7;
                }
            }
            .button {
                background-color: #5faac7;
                color: white;
                padding: 10px 20px;
                border-radius: 3rem;
                cursor: pointer;
            }
        }
    }

    @media print {    
        .no-print, .no-print * {
            display: none !important;
        }
    }

    .fade-enter-active, .fade-leave-active { transition: opacity .5s; }
    .fade-enter, .fade-leave-active { opacity: 0; }
</style>