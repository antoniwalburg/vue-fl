<template>
    <div class="px-4 mx-auto max-w-8xl lg:px-4 lg:text-center pt-28 pb-8 ">
            <h3 class="mb-4 text-4xl tracking-tight text-gray-900 lg:text-3xl lg:leading-none dark:text-white lg:text-center xl:px-36 lg:mb-7">Frequently Asked Questions</h3>
    </div>
    <div v-for="(accordion, index) in accordions" :key="index" class="px-4 mx-auto max-w-screen-xl lg:px-6 pt-2">
        <h2 id="accordion-collapse-heading-1">
            <button type="button" @click="toggleAccordion(index)" :class="{ 'bg-blue-600': accordion.isOpen, 'bg-gray-800': !accordion.isOpen}" 
              class="flex items-center justify-between w-full p-5 text-center text-white dark:text-white hover:bg-blue-600 rounded-2xl duration-150">
                <span> {{ accordion.name }} </span> 
                <svg :class="{'w-6 h-6 rotate-180 shrink-0 duration-200' : !accordion.isOpen, 'w-6 h-6 shrink-0 duration-200' : accordion.isOpen }" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z" clip-rule="evenodd"></path></svg>
            </button>
        </h2>
        <div :class="{ 'hidden-height-acordion': !accordion.isOpen, 'visible-height-acordion': accordion.isOpen}" class="duration-300">
            <div class="p-5 border-gray-200 dark:border-gray-700 dark:bg-gray-900">
                <p class="mt-1 text-gray-500 dark:text-gray-400">{{ accordion.desc }}</p>
                <p class="text-gray-500 dark:text-gray-400"> {{ accordion.additional }} <a :href= accordion.link 
                    class="text-blue-600 dark:text-blue-500 hover:text-white duration-200">{{ accordion.pref }} </a> {{ accordion.additional2 }} </p>
            </div>
        </div>
      </div>
</template>
  
<script> 
  export default {
    data() {
      return {
        accordions: [
          { isOpen: true, name: 'What is Flowbite?', desc: 'Flowbite is an open-source library of interactive components built on top of Tailwind CSS including buttons, dropdowns, modals, navbars, and more.',
            additional: 'Check out this guide to learn how to', additional2: 'and start developing websites even faster with components on top of Tailwind CSS.', 
            pref: 'get started', link: '/#'},
          { isOpen: false , name: 'Is there a Figma file available?', desc: 'Flowbite is first conceptualized and designed using the Figma software so everything you see in the library has a design equivalent in our Figma file.'
          , additional: 'Check out the', additional2: 'based on the utility classes from Tailwind CSS and components from Flowbite.',
            pref: 'Figma design system', link: '/#'},
          { isOpen: false , name: 'What are the differences between Flowbite and Tailwind UI?', desc: 'Flowbite are open source under the MIT license.'
          ,additional: 'The main difference is that the core components from Flowbite are open source under the MIT license, whereas Tailwind UI is a paid product. Another difference is that Flowbite relies on smaller and standalone components, whereas Tailwind UI offers sections of pages.', additional2: 'However, we actually recommend using both Flowbite, Flowbite Pro, and even Tailwind UI as there is no technical reason stopping you from using the best of two worlds.',
            pref: 'Learn more about these technologies.', link: '/#'}
        ]
      };
    },
    methods: {
      toggleAccordion(index) {
        this.accordions[index].isOpen = !this.accordions[index].isOpen;
      }
    },
  };
  </script>
  




