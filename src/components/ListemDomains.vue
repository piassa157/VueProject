<template>
  <div>
       <h5>items <span class="badge badge-info">{{item.length}}</span></h5>
              <div class="card">
                <div class="card-body">
                  <ul class="list-group">
                    <li class="list-group-item" v-for="item in items" :key="item">
                      <div class="row">
                          <div class="col-md">
                              {{item}}
                          </div>

                          <div class="col-md text-right">
                              <button class="btn btn-info" @click="deleteItems(item)"><span class="fa fa-trash"></span></button>
                          </div>
                      </div>
                    </li>
                  </ul>
                  <br>
                  <div class="input-group">
                    <input class="form-control" type="text" placeholder="Write item!" v-model="item" @keyup.enter="addItems(item)"/>
                    <div class="input-group-append">
                      <button class="btn btn-info" @click="addItems(item)"><span class="fa fa-plus"></span></button>
                    </div>
                  </div>
                </div>
              </div>
  </div>
</template>

<script>
export default {
	name: "ListemDomains",
	props: ["items"],
	data() {
		return {
			item: ""
		};
	},
	methods: {
		addItems(item){
			this.$emit("addItem", item);
			this.item = "";
		}
	}

};
</script>


<style scoped>

</style>
 