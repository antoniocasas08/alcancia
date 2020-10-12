<template>
    <b-container class="bv-example-row">
        <b-nav tabs align="center">
            <b-nav-item active>Alcancía</b-nav-item>            
        </b-nav>
        <br>
        
        <b-row>
            <b-col  md="4" lg="4" xl="4">
                <b-card bg-variant="light" text-variant="black" title="Cincuenta">
                    <b-card-text>
                        Cantidad: {{cantidadCincuenta}}
                    </b-card-text>
                    <b-card-text>
                        Total Dinero: {{totalCincuenta}} Pesos
                    </b-card-text>
                    <b-button @click="agregarCincuenta" variant="success">Agregar</b-button>
                </b-card>
            </b-col>
            <b-col  md="4" lg="4" xl="4">
                <b-card bg-variant="light" text-variant="black" title="Cien">
                    <b-card-text>
                        Cantidad: {{cantidadCien}}
                    </b-card-text>
                    <b-card-text>
                        Total Dinero: {{totalCien}} Pesos
                    </b-card-text>
                    <b-button @click="agregarCien" variant="success">Agregar</b-button>
                </b-card>
            </b-col>
            <b-col  md="4" lg="4" xl="4">
                <b-card bg-variant="light" text-variant="black" title="Doscientos">
                    <b-card-text>
                        Cantidad: {{cantidadDoscientos}}
                    </b-card-text>
                    <b-card-text>
                        Total Dinero: {{totalDoscientos}} Pesos
                    </b-card-text>
                    <b-button @click="agregarDoscientos" variant="success">Agregar</b-button>
                </b-card>
            </b-col>
        </b-row>
        <br>
        <b-row>
            <b-col  md="4" lg="4" xl="4">
                <b-card bg-variant="light" text-variant="black" title="Quinientos">
                    <b-card-text>
                        Cantidad: {{cantidadQuinientos}}
                    </b-card-text>
                    <b-card-text>
                        Total Dinero: {{totalQuinientos}} Pesos
                    </b-card-text>
                    <b-button @click="agregarQuinientos" variant="success">Agregar</b-button>
                </b-card>
            </b-col>
            <b-col  md="4" lg="4" xl="4">
                <b-card bg-variant="light" text-variant="black" title="Mil">
                    <b-card-text>
                        Cantidad: {{cantidadMil}}
                    </b-card-text>
                    <b-card-text>
                        Total Dinero: {{totalMil}} Pesos
                    </b-card-text>
                    <b-button @click="agregarMil" variant="success">Agregar</b-button>
                </b-card>
            </b-col>
            <b-col  md="4" lg="4" xl="4">
                <b-card bg-variant="light" text-variant="black" title="Totales">
                    <b-card-text>
                        Total de Monedas: {{totalMonedas}}
                    </b-card-text>
                    <b-card-text>
                        Total Ahorrado: {{totalDinero}} Pesos
                    </b-card-text>
                    <b-button @click="vaciarAlcancia" variant="secondary">Vaciar</b-button>
                </b-card>
            </b-col>
        </b-row>
        
        <b-modal ref="my-modal" hide-footer centered title="Confirmar">
            <div class="d-block text-center">
                <h3>¿Esta seguro de querer vaciar la alcancía?</h3>
            </div>
            <b-button class="mt-2" variant="outline-info" block @click="limpiarDatos">Sí</b-button>
            <b-button class="mt-3" variant="outline-danger" block @click="cerrarModal">No</b-button>            
        </b-modal>
        <b-modal ref="vacía" hide-footer centered title="Información">
            <div class="d-block text-center">
                <h3>La alcancía se encuentra vacía.</h3>
            </div>
        </b-modal>
        

    </b-container>
</template>

<script>
export default {
    name: 'Alcancia',
    data(){
        return {
            cantidadCincuenta: 0,
            cantidadCien: 0,
            cantidadDoscientos: 0,
            cantidadQuinientos: 0,
            cantidadMil: 0,
            totalCincuenta: 0,
            totalCien: 0,
            totalDoscientos: 0,
            totalQuinientos: 0,
            totalMil: 0
        }
    },
    computed: {
        totalMonedas () {
            return  this.cantidadCincuenta + this.cantidadCien + this.cantidadDoscientos + this.cantidadQuinientos + this.cantidadMil
        },
        totalDinero () {
            return this.totalCincuenta + this.totalCien + this.totalDoscientos + this.totalQuinientos + this.totalMil
        }
    },
    methods: {
        agregarCincuenta(){
            this.cantidadCincuenta += 1;
            this.totalCincuenta = this.cantidadCincuenta * 50;
        },
        agregarCien(){
            this.cantidadCien += 1;
            this.totalCien = this.cantidadCien * 100;
        },
        agregarDoscientos(){
            this.cantidadDoscientos += 1;
            this.totalDoscientos = this.cantidadDoscientos * 200;
        },
        agregarQuinientos(){
            this.cantidadQuinientos += 1;
            this.totalQuinientos = this.cantidadQuinientos * 500;
        },
        agregarMil(){
            this.cantidadMil += 1;
            this.totalMil = this.cantidadMil * 1000;
        },
        vaciarAlcancia(){
            if (this.totalDinero !== 0) {
                this.$refs['my-modal'].show()
            }else{
                this.$refs['vacía'].show()
            }
        },
        cerrarModal(){
            this.$refs['my-modal'].hide()
        }, 
        limpiarDatos(){
            this.cantidadCincuenta= 0,
            this.cantidadCien= 0,
            this.cantidadDoscientos= 0,
            this.cantidadQuinientos= 0,
            this.cantidadMil= 0,
            this.totalCincuenta= 0,
            this.totalCien= 0,
            this.totalDoscientos= 0,
            this.totalQuinientos= 0,
            this.totalMil= 0
            this.$refs['my-modal'].hide()
        }
    }
}
</script>

<style scoped>

</style>