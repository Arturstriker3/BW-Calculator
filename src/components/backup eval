<template>
  <div class="main">
    <div :class="{ 'transitioning': transitioning }">
    <div class="calculadora" :data-theme="darkTheme ? 'dark' : ''">
      <div class="header">
        <div class="switchContainer">
          <label class="switchBox">
            <input type="checkbox" v-model="darkTheme" @change="toggleTheme">
            <div class="box"></div>
          </label>
          <span class="label-text">Darkmode</span>
        </div>
      </div>
      <div class="input">
        <input type="text" name="" id="display" :value="displayValue" disabled>
        <input type="button" value="C" class="cancelar_btn" @click="clearDisplay">
      </div>
      <div class="row">
        <input type="button" value="7" @click="buttonClick('7')">
        <input type="button" value="8" @click="buttonClick('8')">
        <input type="button" value="9" @click="buttonClick('9')">
        <input type="button" value="+" @click="buttonClick('+')">
      </div>
      <div class="row">
        <input type="button" value="4" @click="buttonClick('4')">
        <input type="button" value="5" @click="buttonClick('5')">
        <input type="button" value="6" @click="buttonClick('6')">
        <input type="button" value="-" @click="buttonClick('-')">
      </div>
      <div class="row">
        <input type="button" value="3" @click="buttonClick('3')">
        <input type="button" value="2" @click="buttonClick('2')">
        <input type="button" value="1" @click="buttonClick('1')">
        <input type="button" value="*" @click="buttonClick('*')">
      </div>
      <div class="row">
        <input style="border-radius: 0 0 0 10px;" type="button" value="." @click="buttonClick('.')">
        <input type="button" value="0" @click="buttonClick('0')">
        <input style="background: #542e71; color: white;" type="button" value="=" @click="buttonClick('=')">
        <input style="border-radius: 0 0 10px 0;" type="button" value="/" @click="buttonClick('/')">
      </div>
    </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      darkTheme: false,
      displayValue: "",
      transitioning: false // Adicione essa variável para controlar a transição
    };
  },
  methods: {
    toggleTheme() {
      this.transitioning = true; // Inicia a transição

      if (this.darkTheme) {
        document.body.setAttribute("data-theme", "dark");
      } else {
        document.body.setAttribute("data-theme", "");
      }

      if (this.darkTheme) {
        document.body.classList.add("black-theme");
      } else {
        document.body.classList.remove("black-theme");
      }

      this.$refs.calculadora.classList.add("ativo");
      setTimeout(() => {
        this.$refs.calculadora.classList.remove("ativo");
        this.transitioning = false; // Finaliza a transição após um tempo
      }, 800);
    },
    clearDisplay() {
      this.displayValue = "";
    },
    buttonClick(value) {
    if (value === "=") {
      // Lógica para calcular o resultado
      try {
        this.displayValue = eval(this.displayValue);
      } catch (error) {
        this.displayValue = "Erro";
      }
    } else {
      if (value === '.' && this.displayValue.includes('.')) {
        // Evita adicionar múltiplos pontos decimais
        return;
      }

      if (value === '.' && this.displayValue === "") {
        // Se o valor atual do display for vazio, adiciona "0." para começar um número decimal
        this.displayValue = "0.";
      } else {
        // Verifica se o último caractere é um operador e se o valor atual já contém um ponto decimal
        if (/[-+*/]$/.test(this.displayValue) && value === '.') {
          this.displayValue += '0' + value;
        } else {
          this.displayValue += value;
        }
      }
    }
  }
}
};
</script>

<style scoped>
  @import url('https://fonts.googleapis.com/css2?family=Zen+Dots&display=swap');
  *{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Zen Dots', cursive;
  }
  html{
    --bg: #f1f1f1;
    --sec_bg: #fff;
    --color: #000:
    --hover_color: #e7e7e7;
  }
  body[data-theme="dark"]{
    --bg: #0e0e0e;
    --sec_bg: #222222;
    --color: #fff;
    --hover_color: #424242
  }
  body{
    background: var(--bg);
  }
  .main{
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .calculadora{
    width: 300px;
  }
  .header{
    width: 100%;
    height: 60px;
    background: #1b1a17;
    border-radius: 10px 10px 0 0;
    display: flex;
    align-items: center;
  }
  
  .switchContainer {
  display: flex;
  align-items: center;
  margin-left: 12px; /* Ajuste este valor conforme necessário */
}

.switchBox {
  position: relative;
  display: inline-block;
  margin-right: 10px;
}

.switchBox input {
  display: none;
}

.switchBox .box {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  left: 2px;
  width: 30px;
  height: 18px;
  background: #6d6d6d;
  border-radius: 15px;
  transition: background 0.4s; /* Apenas a transição de cor */
}

.switchBox input:checked ~ .box {
  background: #ff8303; /* Mudança de cor quando o switch está ligado */
}

.label-text {
  color: var(--color);
  margin-left: 25px; /* Ajuste este valor conforme necessário */
}

  .input{
    width: 100%;
    height: 60px;
    background: #fff;
  }
  input{
    cursor: pointer;
  }
  .input #display{
    width: 74%;
    height: 60px;
    border: none;
    outline: none;
    font-size: 1.5rem;
    padding-left: 10px;
  }
  .cancelar_btn{
    width: 24%;
    height: 60px;
    border: none;
    background: #ff8303;
    font-size: 1.5rem;
    color: white;
  }
  .row{
    width: 100%;
    margin: 10px 0;
  }
  .row input{
    width: 23.6%;
    height: 60px;
    background: var(--sec_bg);
    color: var(--color);
    border: 1px solid rgba(0, 0, 0, 0.137);
  }

  body.transitioning {
  transition: background-color 0.8s, color 0.8s; /* Aumente a duração da transição */
}

.calculadora {
  width: 300px;
  border: 1px solid #ccc; /* Adicione esta linha para a borda */
}

  .calculadora[data-theme="dark"] {
  background-color: #222222; /* Altere para a cor de fundo desejada */
}

.calculadora[data-theme="dark"] input[type="text"] {
  background-color: #333333; /* Altere para a cor de fundo do input */
  color: white; /* Altere para a cor do texto desejada */
}
  .ativo {
  animation: anim 0.4s;
  }
  @keyframes anim {
    0%, 100% {
      transform: scale(1);
    }
    50% {
      transform: scale(1.1);
      background: var(--hover_color);
    }
  }
  
</style>