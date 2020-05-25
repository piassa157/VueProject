/* eslint-disable indent */
<template>
  <div>
    <div id="title" class="text-center">
      <h1>Name generator</h1>
      <h6 class="text-secondary">Name generator using vueJs, GraphQL and Node</h6>
    </div>
    <br>
  

    <div id="main">
			<getDomains></getDomains>
		</div>
	</div>
</template>

<script>
import "bootstrap/dist/css/bootstrap.css";
import "font-awesome/css/font-awesome.css";
import getDomains from "./components/getDomains";
export default {
	name: "app",
	components: {
		getDomains
	}
};
</script>

<style>
#slogan {
	margin-top: 30px;
	margin-bottom: 30px;
}
#main {
	background-image: linear-gradient(aquamarine, purple);;
	padding-top: 30px;
	padding-bottom: 30px;
}
</style>