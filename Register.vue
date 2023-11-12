<template>
    <!-- Main modal -->
    <div @wheel.prevent @touchmove.prevent @scroll.prevent 
        id="modal2" tabindex="-1" aria-hidden="true" class="fixed top-0 left-0 right-0 z-50 hidden w-full p-4 overflow-x-hidden overflow-y-auto md:inset-0 h-[calc(100%-1rem)] max-h-full">
        <div class="relative w-full max-w-md max-h-full">
            <!-- Modal content -->
            <div class="relative bg-white rounded-xl shadow dark:bg-gray-800 border-4 border-transparent">
                <button id='closeButton2' type="button" class="absolute top-3 right-2.5 text-gray-400 duration-300 bg-gray-900 hover:bg-gray-200 hover:text-gray-900 rounded-lg text-sm p-1.5 ml-auto inline-flex items-center dark:hover:bg-white dark:hover:text-indigo-500" data-modal-hide="authentication-modal">
                    <svg aria-hidden="true" class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z" clip-rule="evenodd"></path></svg>
                    <span class="sr-only">Close modal</span>
                </button>
                <div class="px-6 py-6 lg:px-8">
                    <h3 class="mb-4 text-xl font-medium text-gray-900 dark:text-white">Register to our platform ⚡</h3>
                    <form class="space-y-6" action="#">
                        <div>
                            <label for="username" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Your username</label>
                            <input type="username" name="username" id="username" placeholder="BuffyBunny80" class="bg-gray-50  text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-900 dark:placeholder-gray-400 dark:text-white" required>
                        </div>
                        <div>
                            <label for="email" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Your email</label>
                            <input type="email" name="email" id="email" class="bg-gray-50 dark:border-2 text-gray-900 text-sm rounded-lg dark:focus:border-blue-500 block w-full p-2.5 dark:bg-gray-900 dark:border-gray-800 dark:placeholder-gray-400 dark:text-white" placeholder="name@company.com" required>
                        </div>
                        <div>
                            <label for="password" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Your password</label>
                            <input type="password" name="password" id="password" placeholder="••••••••" class="bg-gray-50  text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-900 dark:placeholder-gray-400 dark:text-white" required>
                        </div>
                        <button type="submit" class="w-full text-white bg-indigo-700 hover:bg-indigo-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-semibold rounded-lg text-sm px-5 py-2.5 text-center dark:bg-indigo-600 dark:hover:bg-indigo-700 dark:focus:ring-indigo-800">Register your account 👋</button>
                    </form>
                </div>
            </div>
        </div>
    </div> 

</template>

<script setup>
    
    import { onMounted } from 'vue'
    import { Modal } from 'flowbite'
    
    onMounted(() => {
        const $buttonElement = document.querySelector('#register');
        const $modalElement = document.querySelector('#modal2');
        const $closeButton = document.querySelector('#closeButton2');
    
        const modalOptions = {
            backdrop: 'dynamic',
            backdropClasses: 'bg-gray-900 bg-opacity-50 dark:bg-opacity-80 fixed inset-0 z-40',
        }
    
        if ($modalElement) {
            const modal = new Modal($modalElement, modalOptions);
            $buttonElement.addEventListener('click', () => {
                modal.toggle()
                $modalElement.classList.add('scaling-animation')
            });
            $closeButton.addEventListener('click', () => modal.hide());

            $modalElement.addEventListener('transitionend', () => {
                $modalElement.classList.remove('scaling-animation')
            })
        }
    })
    
</script>

<style>
.scaling-animation {
  animation-name: scaling;
  animation-duration: 0.3s;
  animation-timing-function: ease-in-out;
  transform-origin: center;
}

@keyframes scaling {
  0% {
    transform: scale(0);
  }
  100% {
    transform: scale(1);
  }
}
</style>