<template>
    <div id="burguer-table">
        <div>
            <div id="burguer-table-heading">
                <div class="order-id">
                    #
                </div>
                <div>Cliente</div>
                <div>Pão</div>
                <div>Carne</div>
                <div>Opcionais</div>
                <div>Ações</div>
            </div>
        </div>
        <div id="burguer-table-rows">
            <div class="burguer-table-row" v-for="burguer in this.burguers" :key="burguer.id">
                <div class="order-number">
                    {{ burguer.id}}
                </div>
                <div>{{burguer.nome}}</div>
                <div>{{burguer.pao}}</div>
                <div>{{burguer.carne}}</div>
                <div>
                    <ul>
                        <li v-for="(opcional, index) in burguer.opcionais" :key="index">
                            {{opcional}}
                        </li>
                    </ul>
                </div>
                <div>
                    <select name="status" class="status">
                        <option value="">Selecione...</option>
                        <option v-for="s in this.status" :key="s.id" :value="s.id"
                            :selected="s.tipo == burguer.status"
                        >
                            {{s.tipo}}
                        </option>
                    </select>
                    <button class="delete-btn">Cancelar</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Dashboard',
    data() {
        return {
            burguers: null,
            burguer_id: null,
            status: [],
            baseUrl: 'http://localhost:3000/',
        }
    },
  methods: {
     async getPedidos() {
      const req = await fetch(this.baseUrl + 'burgers', {
        headers: {
          'Content-Type': 'application/json',
          'Accept': 'application/json',
        },
      })

      this.burguers = await req.json()
    },
    async getStatus() {
      const req = await fetch(`${this.baseUrl}status`, {
        method: 'get',
        headers: {
          'Content-Type': 'application/json',
          'Accept': 'application/json',
        },
      })

      this.status = await req.json()
      console.log(this.status)
    }
  },
  mounted() {
      this.getPedidos()
      this.getStatus()
  },
}
</script>

<style scoped>
    #burguer-table {
        max-width: 1200px;
        margin: 0 auto;
    }
    #burguer-table-heading,
    #burguer-table-rows,
    .burguer-table-row {
        display: flex;
        flex-wrap: wrap;
    }
    #burguer-table-heading {
        font-weight: bold;
        padding: 12px;
        border-bottom: 3px solid #333;
    }
    #burguer-table-heading div,
    .burguer-table-row div {
        width: 19%;
    }

    .burguer-table-row {
        width: 100%;
        padding: 12px;
        border-bottom: 1px solid #ccc;
    }
    #burguer-table-heading .order-id,
    .burguer-table-row .order-number {
        width: 5%;
    }
    select {
        padding: 12px 6px;
        margin-right: 12px;
    }
    .delete-btn {
        background-color: #222;
        color: #fcba03;
        font-weight: bold;
        border: 2px solid #222;
        padding: 10px;
        font-size: 16px;
        margin: 0 auto;
        cursor: pointer;
        transition: .5s;
    }
    .delete-btn:hover {
        background-color: transparent;
        color: #222;
    }
</style>