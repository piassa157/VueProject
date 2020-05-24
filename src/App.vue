/* eslint-disable indent */
<template>
  <div>
    <div id="title" class="text-center">
      <h1>Name generator</h1>

      <h6 class="text-secondary">Name generator using vueJs, GraphQL and Node</h6>
    </div>
    <br>
  

    <div id="main">
      <div class="container">
          <div class="row"> 
            <div class="col-md">
              <ListemDomains v-bind:items="prefixes"></ListemDomains>
            </div>
            <ListemDomains v-bind:items="sufixes"></ListemDomains>
            <div class="col-md">
              <h5>Sufixes <span class="badge badge-info">{{sufixes.length}}</span></h5>
              <div class="card">
                <div class="card-body">
                  <ul class="list-group">
                    <li class="list-group-item" v-for="sufix in sufixes" :key="sufix">
                      <div class="row">
                          <div class="col-md">
                              {{sufix}}
                          </div>

                          <div class="col-md text-right">
                              <button class="btn btn-info" @click="deleteSufix(sufix)"><span class="fa fa-trash"></span></button>
                          </div>
                      </div>
                    </li>
                  </ul>
                  <br>
                   <div class="input-group">
                    <input class="form-control" type="text" placeholder="Write sufix!" v-model="sufix" @keyup.enter="addSufix(sufix)"/>
                    <div class="input-group-append">
                      <button class="btn btn-info" @click="addSufix(sufix)"><span class="fa fa-plus"></span></button>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
      </div>
      <br>

      <h5>Domains <span class="badge badge-info">{{domains.length}}</span></h5>
      <div class="card">
        <div class="card-body">
          <ul class="list-group">
            <li class="list-group-item" v-for="domain in domains" :key="domain.name">
              <div class="row">
                <div class="col-md">
                  {{domain.name}}
                </div>
                <div class="col-md text-right"> 
                  <a class="btn btn-info" 
                  v-bind:href="domain.check"
                  target="_blank">
                    <span class="fa fa-shopping-cart"></span>
                  </a>
                </div>
              </div>

            </li>
          </ul>
        </div>
      </div>
  
    </div>
  </div>
</template>

<script>

import "bootstrap/dist/css/bootstrap.css";
import "font-awesome/css/font-awesome.css";
import ListemDomains from "./components/ListemDomains";
export default {
	name: "App",
	components: {
		ListemDomains
	},
	data: function() {
		return {
			sufix: "",
			prefix: "",
			prefixes: ["Air", "Jet", "Flight"],
			sufixes: ["Hub", "Station", "Mart"]
		};
	},
	methods: {
		addPrefix(){
			this.prefixes.push(this.prefix);
			this.prefix = "";
		},
		addSufix(){
			this.sufixes.push(this.sufix);
			this.sufix = "";
		},
		deletePrefix(prefix){
			this.prefixes.splice(this.prefixes.indexOf(prefix), 1);      
		},
		deleteSufix(sufix){
			this.sufixes.splice(this.sufixes.indexOf(sufix), 1);
		}
		
	},
	computed: {
		domains() {
			const domains = []; 
			for (const prefix of this.prefixes){
				for(const sufix of this.sufixes){
					const name = prefix + sufix;
					const url = name.toLowerCase();
					const check = `https://checkout.hostgator.com.br/?a=add&sld=${url}&tld=.com`;
					domains.push({
						name,
						check
					});
				}
			}
			return domains;
		}
	},
};
</script>

<style>
  #title {
    margin-top: 30px;
    margin-bottom: 30px; 
  }

  #main {
    background-color: aquamarine;
    padding-top: 30px;
    padding-bottom: 30px;
  }
</style>
