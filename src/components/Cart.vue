<template>
	<div>
		<ul class="list-group">
			<li class="list-group-item" v-for="item in items" :key="item.id">
				{{ item.title }} - eur {{ item.price }}
				<button @click="$emit('remove-from-cart', item)" class="btn badge badge-danger float-right">
					Remove from cart
				</button>
			</li>
		</ul>
		<div class="card p-3 my-5">
			<h4 class="text-center">
				EUR {{ total }}
			</h4>
		</div>
	</div>
</template>
<script>
	export default{
	    props:['items'],
		computed:{
	        total(){
	            return this.items.reduce((acc, item) => acc + Number(item.price),0)
	        }
		}
	}
</script>