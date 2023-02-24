<template>
    <div class="generator">
        <div class="generator-field">
            <p>{{ pw }}</p>
        </div>
        <div class="generator-panel">
            <div class="checkbox-line">
                <label><input type="checkbox" id="upp-cb" v-model="uppFlag"><span>uppercase</span></label>
                <label><input type="checkbox" id="num-cb" v-model="numFlag"><span>number</span></label>
                <label><input type="checkbox" id="sym-cb" v-model="symFlag"><span>symbols</span></label>
            </div>
            <input type="text" placeholder="length" class="input-length" v-model="pwLength">
            <button @click="generatePw">Generate</button>
            <button @click="copy">Copy</button>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            letters: "abcdefghijklmnopqrstuvwxyz",
            uppLetters: "ABCDEFGHIJKLMNOPQRSTUVWXYZ",
            numbers: "0123456789",
            symbols: "!@#$%^&*+<>/",
            pwArr: [],
            uppFlag: false,
            numFlag: false,
            symFlag: false,
            pwLength: "",
            pw: "generate a password",
        }
    },
    methods: {
        getRandomInt(min, max) {
            return Math.round(min - 0.5 + Math.random() * (max - min + 1));
        },
        concatArr() {
            this.pwArr = this.letters.split("");
            const uppLettArr = this.uppLetters.split("");
            const numArr = this.numbers.split("");
            const symArr = this.symbols.split("");
            if(this.uppFlag == true) {
                this.pwArr = this.pwArr.concat(uppLettArr);
                if(this.numFlag == true) {
                    this.pwArr = this.pwArr.concat(numArr);
                    if(this.symFlag == true) {
                        this.pwArr = this.pwArr.concat(symArr);
                    }
                } else if (this.symFlag == true) {
                    this.pwArr = this.pwArr.concat(symArr);
                }
            } else if (this.numFlag == true){
                this.pwArr = this.pwArr.concat(numArr);
                if(this.symFlag == true) {
                    this.pwArr = this.pwArr.concat(symArr);
                }
            } else if (this.symFlag == true) {
                this.pwArr = this.pwArr.concat(symArr);
            }
        },
        generatePw() {
            this.concatArr();
            this.pw = "";
            if(parseInt(this.pwLength)) {
                for(let i = 0; i <= this.pwLength; i++) {
                    this.pw += this.pwArr[this.getRandomInt(0, this.pwArr.length - 1)];
                }
            } else this.pw = "invalid length"
        },
        copy() {
            navigator.clipboard.writeText(this.pw);
            alert("Text copied");
        }
    }
}
</script>