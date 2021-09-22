<template>
    <div>
        <p>Componente de mensagem</p>
        <div>
            <form id="form-burguer">
                <div class="input-container">
                    <label for="nome">Nome do cliente</label>
                    <input type="text" name="nome" id="nome" v-model="nome" placeholder="Digite o seu nome">
                </div>
                <div class="input-container">
                    <label for="pao">Escolha o pão</label>
                    <select name="pao" id="pao" v-model="pao">
                        <option value=""></option>
                        <option value="Integral">Integral</option>
                    </select>
                </div>
                <div class="input-container" id="opcional-container">
                    <label for="carne">Escolha a carne</label>
                    <select name="carne" id="carne" v-model="carne">
                        <option value=""></option>
                        <option value="Integral">Integral</option>
                    </select>
                </div>
                <div class="input-container">
                    <label for="opcional" id="opcional-title">Escolha a opcional</label>
                    <div class="checkbox-container">
                        <input type="checkbox" name="opcional" v-model="opcional" value="Salame">
                        <span>Salame</span>
                    </div>
                </div>
                <div class="input-container">
                    <input type="submit" class="submit-btn" value="Criar meu burger">
                </div>
            </form>
        </div>
    </div>
</template>

<script>
export default {
    name: 'BurguerForm',
}
</script>

<style scoped>
  #burger-form {
    max-width: 400px;
    margin: 0 auto;
  }
  .input-container {
    display: flex;
    flex-direction: column;
    margin-bottom: 20px;
  }
  label {
    font-weight: bold;
    margin-bottom: 15px;
    color: #222;;
    padding: 5px 10px;
    border-left: 4px solid #fcba03;
  }
  input, select {
    padding: 5px 10px;
    width: 300px;
  }
  #opcionais-container {
    flex-direction: row;
    flex-wrap: wrap;
  }
  #opcionais-title {
    width: 100%;
  }
  .checkbox-container {
    display: flex;
    align-items: flex-start;
    width: 50%;
    margin-bottom: 20px;
  }
  .checkbox-container span,
  .checkbox-container input {
    width: auto;
  }
  .checkbox-container span {
    margin-left: 6px;
    font-weight: bold;
  }
  .submit-btn {
    background-color: #222;
    color:#fcba03;
    font-weight: bold;
    border: 2px solid #222;
    padding: 10px;
    font-size: 16px;
    margin: 0 auto;
    cursor: pointer;
    transition: .5s;
  }
  .submit-btn:hover {
    background-color: transparent;
    color: #222;
  }
</style>
