<template>
    <div class="w-full h-full min-h-screen p-12">
        <div class="container p-10 w-1/2 m-12 mx-auto bg-gray-200 shadow-lg">
            <div class="space-y-6">
                <ul>
                    <form class="space-y-2"> 
                        <li class="font-bold">Otázka 1: Až zemřu, chci aby si mě lidé pamatovali jako:</li>
                        <li>
                            <input v-model="first" type="radio" id="one" value="one" />
                            <label @click="mrzimor++" for="one" class="px-2">Dobrého člověka </label>
                        </li>

                        <li>
                            <input v-model="first" type="radio" id="two" value="two" />
                            <label @click="zmijozel++" for="two">Skvělého člověka</label>
                        </li>

                        <li>
                            <input v-model="first" type="radio" id="three" value="three" />
                            <label @click="havraspar++" for="three">Moudrého člověka</label>
                        </li>

                        <li>
                            <input v-model="first" type="radio" id="four" value="four" />
                            <label @click="nebelvir++" for="four">Statečného člověka</label>
                        </li>
                    </form>
                </ul>

                <ul>
                    <form class="space-y-2">
                        <li class="font-bold">Otázka 2: Preferuješ úsvit nebo soumrak?</li>
                        <li>
                            <input v-model="second" type="radio" id="secOne" value="secOne" />
                            <label @click="nebelvir++ || havraspar++" for="secOne">Úsvit</label>
                        </li>
                        <li>
                            <input v-model="second" type="radio" id="secTwo" value="secTwo" />
                            <label @click="zmijozel++ || mrzimor++" for="secTwo">Soumrak</label>
                        </li>
                    </form>
                </ul>

                <ul>
                    <form class="space-y-2">
                        <li class="font-bold">Otázka 3: Který hudební nástroj nejvíce potěší tvůj sluch?</li>
                         <li>
                            <input v-model="third" type="radio" id="rdOne" value="rdOne" />
                            <label @click="zmijozel++" for="rdOne">Housle</label>
                        </li>

                         <li>
                            <input v-model="third" type="radio" id="rdTwo" value="rdTwo" />
                            <label @click="mrzimor++" for="rdTwo">Trumpeta</label>
                        </li>

                         <li>
                            <input v-model="third" type="radio" id="rdThree" value="rdThree" />
                            <label @click="havraspar++" for="rdThree">Piáno</label>
                        </li>

                         <li>
                            <input v-model="third" type="radio" id="rdFour" value="rdFour" />
                            <label @click="nebelvir++" for="rdFour">Buben</label>
                        </li>
                    </form>
                </ul>

                <ul>
                    <form class="space-y-2">
                        <li class="font-bold">Otázka 4: Stojíš-li na rozcestí, jakou stezku si zvolíš?</li>
                        <li>
                            <input v-model="fourth" type="radio" id="foOne" value="foOne" />
                            <label @click="mrzimor++" for="foOne">Široká, prosluněná a obklopená trávou</label>
                        </li>

                        <li>
                            <input v-model="fourth" type="radio" id="foTwo" value="foTwo" />
                            <label @click="zmijozel++" for="foTwo">Úzká, tmavá, osvětlená pouze lucernou</label>
                        </li>

                        <li>
                            <input v-model="fourth" type="radio" id="foThree" value="foThree" />
                            <label @click="nebelvir++" for="foThree">Klikatá, posetá listím skrz les</label>
                        </li>

                        <li>
                            <input v-model="fourth" type="radio" id="foFour" value="foFour" />
                            <label @click="havraspar++" for="foFour">Dlážděná cesta skrz starobylé město</label>
                        </li>
                        <li v-show="show" class="pt-4 font-bold">Tvoje kolej je {{ choice }}</li>
                    </form>
                </ul>
            </div>
        </div>
    </div>
</template>


<script setup>
import { ref, computed } from "vue";

const first = ref("");
const second = ref("");
const third = ref("");
const fourth = ref("");

const highest = ref(0);

// kolejicky
const nebelvir = ref(0);
const mrzimor = ref(0);
const havraspar = ref(0);
const zmijozel = ref(0);


const choice = computed(() => {
    // Find highest of the four
    highest.value = Math.max(nebelvir.value, mrzimor.value, havraspar.value, zmijozel.value);

    // Return the house
    if (highest.value === nebelvir.value) {
        return "Nebelvir";
    } else if (highest.value === mrzimor.value) {
        return "Mrzimor";
    } else if (highest.value === havraspar.value) {
        return "Havraspár";
    } else if (highest.value === zmijozel.value) {
        return "Zmijozel";
    }
});

const show = computed(() => {
    if (first.value !="" && second.value != "" && third.value != "" && fourth.value != "") {
        return choice.value;
    }
});



</script>










