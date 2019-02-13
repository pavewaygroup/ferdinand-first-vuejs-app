<template>
	<v-container>
    	<v-layout row align-center>
      		<v-flex xs12 sm5 offset-sm4>
        		<v-card>
          			<v-toolbar color="teal" dark>

            			<v-toolbar-title class="text-xs-center">Calculator App</v-toolbar-title>
          			</v-toolbar>

					<div class="display-pad">
						<p class="display-result" v-text="display"></p>
						<v-btn color="grey lighten-2" @click="removeDisplay" class="acbutton">ac</v-btn>
					</div>
					<div class="Key-pad">
						<v-layout column wrap align-center>
							<v-flex xs2>
								<v-layout row wrap>
								  <v-flex xs3>
								   <v-btn @click="addToDisplay(1,'num')" color="primary" id="number1" class="   elevation-0">1</v-btn>
								  </v-flex>
								  <v-flex xs3>
								    <v-btn @click="addToDisplay(2,'num')" color="primary" id="number2" class="elevation-0">2</v-btn>
								  </v-flex>
								  <v-flex xs2 md3>
								    <v-btn @click="addToDisplay(3,'num')" color="primary" id="number3" class="elevation-0">3</v-btn>
								  </v-flex>
								  <v-flex xs2 md3>
								    <v-btn @click="addToDisplay('*','op')" color="indigo" id="operrator" class="elevation-0">*</v-btn>
								  </v-flex>
								</v-layout>
							</v-flex>
							<v-flex xs1>
								<v-layout row wrap>
								  <v-flex xs3>
								    <v-btn @click="addToDisplay(4,'num')" color="primary" id="number4" class="elevation-0">4</v-btn>
								  </v-flex>
								  <v-flex xs3>
								    <v-btn @click="addToDisplay(5,'num')" color="primary" id="number5" class="elevation-0">5</v-btn>
								  </v-flex>
								  <v-flex xs2 md3>
								    <v-btn @click="addToDisplay(6,'num')" color="primary" id="number6" class="elevation-0">6</v-btn>
								  </v-flex>
								  <v-flex xs2 md3>
								    <v-btn @click="addToDisplay('\\','op')" color="indigo" id="operrator" class="elevation-0">\</v-btn>
								  </v-flex>
								</v-layout>
							</v-flex>
							<v-flex xs1>
								<v-layout row wrap>
								  <v-flex xs3>
								    <v-btn @click="addToDisplay(7,'num')" color="primary" id="number7" class="elevation-0">7</v-btn>
								  </v-flex>
								  <v-flex xs3>
								    <v-btn @click="addToDisplay(8,'num')" color="primary" id="number8" class="elevation-0">8</v-btn>
								  </v-flex>
								  <v-flex xs2 md3>
								    <v-btn @click="addToDisplay(9,'num')" color="primary" id="number9" class="elevation-0">9</v-btn>
								  </v-flex>
								  <v-flex xs2 md3>
								    <v-btn @click="addToDisplay('.','op')" color="indigo" id="operrator" class="elevation-0">.</v-btn>
								  </v-flex>
								</v-layout>
							</v-flex>
							<v-flex xs1>
								<v-layout row wrap>
								  <v-flex xs3>
								    <v-btn @click="addToDisplay('+','op')" color="indigo" id="operrator" class="elevation-0">+</v-btn>
								  </v-flex>
								  <v-flex xs3>
								    <v-btn @click="addToDisplay(0,'num')" color="primary" id="number0" class="elevation-0">0</v-btn>
								  </v-flex>
								  <v-flex xs2 md3>
								    <v-btn @click="addToDisplay('-','op')" color="indigo" id="operrator" class="elevation-0">-</v-btn>
								  </v-flex>
								  <v-flex xs2 md3>
								    <v-btn @click="addToDisplay('=','op')" color="indigo" id="operrator" class="elevation-0">=</v-btn>
								  </v-flex>
								</v-layout>
							</v-flex>
						</v-layout>
					</div>
	 			</v-card>
   			</v-flex>
		</v-layout>
	</v-container>
</template>
<script>
	export default{
		data () {
			return{
				display: '',
				operran1:'',
				operran2:'',
				operrator:null,
				equalto:null,
				answeris:null,
				anoperator:false,
			}
		},
		methods:{
			removeDisplay(){
				this.display=''
				this.operran1=''
				this.operran2=''
				this.operrator=null
				this.equalto=null
				this.answeris=null
				this.anoperator=false
			},
			addToDisplay(operrand,thetype){
				this.display = this.display + operrand
				if (thetype=='num') {
					if (this.anoperator==false) {
						this.operran1=this.operran1 + parseInt(operrand)
						this.operrand=this.display
					}else{
						if (this.anoperator==true) {
							this.operran2=this.operran2 + parseInt(operrand)
						    this.operrand=this.display
						}else{
							this.operran1=parseInt(operrand)
						    this.operrand==operran1
						    this.operrand=this.display
						}
					}
				}else{
					this.anoperator=true
					if (operrand=='=') {
						this.anoperator=false
						this.equalto=parseInt(this.operran1) + this.operrator + parseInt(this.operran2)
						this.answeris=parseInt(this.equalto)
						this.display=this.answeris
					}else{
						if (thetype=='op') {
							this.operrator=String(operrand)
						}else{
							this.display='Infinit'
						}
					}
				}
			}
		}
	};
</script>
<style lang="scss">
	.display-pad {
		height:50px;
		width: 100%;
		color:black;
		background-color:pink;
		display: table;
		margin-top: 10px;
		margin-bottom: 10px; 
		p.display-result {
			display: table-cell;
			vertical-align: middle;
			padding: 10px;
		}
		.acbutton {
		float:right;

	}

	}
</style>