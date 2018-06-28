<template>
	<div id="app">
		<div class="map-content">
			<div class="map-head-title">
				Mapas de Processos
			</div>
			<div class="map-title">
				Mapa de processo -
				<span>{{app.process_name}}</span>
			</div>
			<div class="process-info">
				<div class="process-hook">
					<div class="process-start">
						Início do processo -
						<span>{{app.process_start}}</span>
					</div>
					<div class="process-end">
						Término do processo -
						<span>{{app.process_end}}</span>
					</div>
				</div>
				<div class="sector-mission">
					Missão do setor:
					<span>{{app.sector_mission}}</span>
				</div>
			</div>
			<div class="map">
				<div class="map-header">
					<div class="header-margin br">
						Fornecedores
					</div>
					<div class="header-margin">
						Entradas
					</div>
					<div class="header-center">
						Processo
					</div>
					<div class="header-margin">
						Saída
					</div>
					<div class="header-margin bl">
						Clientes
					</div>
				</div>
				<div class="map-body">
					<div class="item-process"  v-for="processo in processos" :key="processo.id">
						<div class="item-margin">
							<div class="item-margin-top">
								<div class="item-half br" v-on:click="pimba();processo.pr_fornecedores = !processo.pr_fornecedores">
									{{processo.fornecedores}}
								</div>
								<div class="item-half br" v-on:click="pimba();processo.pr_entradas = !processo.pr_entradas">
									{{processo.entradas}}
								</div>
							</div>
							<div class="item-margin-bottom">
								<div class="item-all br" v-on:click="pimba();processo.pr_requisitos_entrada = !processo.pr_requisitos_entrada">
									<div class="requisites">
										Requisitos:
									</div>
									{{processo.requisitos_entrada}}
								</div>
							</div>
						</div>
						<div class="item-center">
							<div class="item-process-name" v-on:click="pimba();processo.pr_processo_nome = !processo.pr_processo_nome">
								{{processo.processo_nome}}
							</div>
						</div>
						<div class="item-margin">
							<div class="item-margin-top">
								<div class="item-half bl" v-on:click="pimba();processo.pr_saida = !processo.pr_saida">
									<span>{{processo.saida}}</span>
								</div>
								<div class="item-half bl" v-on:click="pimba();processo.pr_clientes = !processo.pr_clientes">
									{{processo.clientes}}
								</div>
							</div>
							<div class="item-margin-bottom">
								<div class="item-all bl" v-on:click="pimba();processo.pr_requisitos_saida = !processo.pr_requisitos_saida">
									<div class="requisites">
										Requisitos:
									</div>
									{{processo.requisitos_saida}}
								</div>
							</div>
						</div>

						<!-- processo fornecedores -->
						<div v-if="processo.pr_fornecedores" class="config">
							<div class="alt-text">
								<div class="label">
									Digite o conteúdo abaixo:
								</div>
								<textarea  v-model="processo.fornecedores">
									
								</textarea>
							</div>
						</div>
						<!-- processo entradas -->
						<div v-if="processo.pr_entradas" class="config">
							<div class="alt-text">
								<div class="label">
									Digite o conteúdo abaixo:
								</div>
								<textarea  v-model="processo.entradas">
									
								</textarea>
							</div>
						</div>
						<!-- processo nome -->
						<div v-if="processo.pr_processo_nome" class="config">
							<div class="alt-text">
								<div class="label">
									Digite o conteúdo abaixo:
								</div>
								<textarea  v-model="processo.processo_nome">
									
								</textarea>
							</div>
						</div>
						<!-- processo saida -->
						<div v-if="processo.pr_saida" class="config">
							<div class="alt-text">
								<div class="label">
									Digite o conteúdo abaixo:
								</div>
								<textarea  v-model="processo.saida">
									
								</textarea>
							</div>
						</div>
						<!-- processo clientes -->
						<div v-if="processo.pr_clientes" class="config">
							<div class="alt-text">
								<div class="label">
									Digite o conteúdo abaixo:
								</div>
								<textarea  v-model="processo.clientes">
									
								</textarea>
							</div>
						</div>
						<!-- processo requisitos_entrada -->
						<div v-if="processo.pr_requisitos_entrada" class="config">
							<div class="alt-text">
								<div class="label">
									Digite o conteúdo abaixo:
								</div>
								<textarea  v-model="processo.requisitos_entrada">
									
								</textarea>
							</div>
						</div>
						<!-- processo requisitos_saida -->
						<div v-if="processo.pr_requisitos_saida" class="config">
							<div class="alt-text">
								<div class="label">
									Digite o conteúdo abaixo:
								</div>
								<textarea  v-model="processo.requisitos_saida">
									
								</textarea>
							</div>
						</div>
					</div>
				</div>
			</div>
		</div>
		
	</div>
</template>

<script>
	export default {
		name: "app",
		data() {
			return {
				app: {
					process_name: "Nome do processo",
					process_start: "ooa",
					process_end: "",
					sector_mission: ""
				},
				processos: [
					{
						id:'',
						fornecedores: "",
						entradas: "",
						processo_nome: "",
						saida: "",
						clientes: "",
						requisitos_entrada:"",
						requisitos_saida:"",

						pr_saida:false,
						pr_entradas:false,
						pr_fornecedores:false,
						pr_processo_nome:false,
						pr_clientes:false,
						pr_requisitos_entrada:false,
						pr_requisitos_saida:false
						
					}
				]
			};
		},
		methods:{
			pimba:function(variableu){
				this.processos.forEach(function(element, index, array){
					element.pr_saida = false;
					element.pr_entradas = false;
					element.pr_fornecedores = false;
					element.pr_processo_nome = false;
					element.pr_clientes = false;
					element.pr_requisitos_entrada = false;
					element.pr_requisitos_saida = false;
				});
			}
		}
	};
</script>

<style lang="scss">
	$default_border: solid 1px #333;
	#app {
		padding-left: 15px;
		padding-right: 15px;
	}

	body {
		font-family: 'Open Sans', sans-serif;
		
	}

	.map-content {
		width: 100%;
		float: left;
		display: block;
		border: $default_border;
		border-bottom: 0px;
		margin-bottom:200px;
		.map-head-title {
			width: 100%;
			padding-top: 5px;
			padding-bottom: 5px;
			background-color: #333;
			color: white;
			display: flex;
			align-items: center;
			justify-content: center;
			font-size: 20px;
			font-weight: bold;
			text-transform: uppercase;
		}
		.map-title {
			display: flex;
			padding: 10px;
			margin-top: 5px;
			font-size: 12px;
			background-color: #989898;
			color: white;
			font-weight: bold;
			text-transform: uppercase;

			span {
				font-weight: 400;
			}
		}
		.process-info {
			.process-hook {
				display: flex;
				padding: 10px;
				font-size: 12px;
				text-transform: uppercase;
				font-weight: bold;
				color: #333;
				span {
					font-weight: 400;
				}
				.process-start {
					width: 50%;
				}
				.process-end {
					width: 50%;
				}
			}
			.sector-mission {
				font-size: 12px;
				font-weight: bold;
				text-transform: uppercase;
				display: flex;
				padding: 10px;
				color: #989898;
				span {
					font-weight: 400;
				}
			}
		}
		.map {
			.map-header {
				display: flex;
				width: 100%;
				align-items: center;
				font-size: 12px;
				text-transform: uppercase;
				font-weight: bold;
				background-color: #aaa;
				color: #333;
				border-top: $default_border;
				border-bottom: $default_border;
				.header-margin {
					width: 19%;
					padding: 10px;
					text-align: center;
					&.br {
						border-right: $default_border;
					}
					&.bl {
						border-left: $default_border;
					}
				}
				.header-center {
					padding: 10px;
					width: 24%;
					text-align: center;
					border-left: $default_border;
					border-right: $default_border;

				}
			}
			.map-body {
				.item-process {
					display: flex;
					align-items: center;
					width: 100%;
					height: auto;
					border-bottom: $default_border;
					position:relative;
					cursor: pointer;
					
					.item-margin {
						width: 38.5%;
						.item-margin-top {
							display: flex;
							align-items: center;
							.item-half {
								width: 50%;
								min-height: 50px;
								&.br {
									border-right: $default_border;
								}
								&.bl {
									border-left: $default_border;
								}
							}
						}
						.item-margin-bottom {
							width: 100%;
							display: flex;
							align-items: center;
							.item-all {
								position: relative;
								display: flex;
								min-height: 55px;
								border-top:$default_border;
								width:100%;
								padding: 0px 5px;
								padding-top:15px;
								&.br {
									border-right: $default_border;
								}
								&.bl {
									border-left: $default_border;
								}
								.requisites{
									position:absolute;
									font-size: 12px;	
									text-transform: uppercase;
									top:0;
									left:5px;
								}
							}
						}
					}

					.item-center {
						width: 23.8%;
						height: 100%;
						display: flex;
						justify-content: center;
						.item-process-name{
							width:80%;
							min-height:50px;
							border-radius: 10px;
							border: $default_border;
						}

					}
				}
			}
		}
	}
	.config{
		position:fixed;
		bottom:0;
		left: 0;
		height:100px;
		width:100%;
		background-color:#4db883;
		padding: 15px;
		.alt-text{
			width:80%;
			.label{
				width:100%;
				color:white;
				font-size: 20px;
				font-weight: bold;
				text-transform:uppercase;
			}
			textarea{
				width: 100%;
				height: 60px;
				border: solid 0px #2ba568;
				border-radius: 10px;
				background-color: #6ff5b2;
				outline: none;
				padding: 5px;
			}
		}
	}
</style>