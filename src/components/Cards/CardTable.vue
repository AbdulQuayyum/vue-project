<template>

	<!-- detailss Table Card -->
	<a-card :bordered="false" class="header-solid h-full" :bodyStyle="{padding: 0,}">
		<template #title>
			<a-row type="flex" align="middle">
				<a-col :span="24" :md="12">
					<h5 class="font-semibold m-0">My Recordings</h5>
				</a-col>
				<a-col :span="24" :md="12" style="display: flex; align-items: center; justify-content:space-between" class="header-control">

					<!-- Header Control Buttons -->
				<router-link to="/sign-in" class="btn-filter btn-red
                " @click="e => e.preventDefault()">
						<svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
							<path fill-rule="evenodd" clip-rule="evenodd" d="M18 10C18 14.4183 14.4183 18 10 18C5.58172 18 2 14.4183 2 10C2 5.58172 5.58172 2 10 2C14.4183 2 18 5.58172 18 10ZM12 7C12 8.10457 11.1046 9 10 9C8.89543 9 8 8.10457 8 7C8 5.89543 8.89543 5 10 5C11.1046 5 12 5.89543 12 7ZM9.99993 11C7.98239 11 6.24394 12.195 5.45374 13.9157C6.55403 15.192 8.18265 16 9.99998 16C11.8173 16 13.4459 15.1921 14.5462 13.9158C13.756 12.195 12.0175 11 9.99993 11Z" fill="#111827"/>
						</svg>
						<span>Start Recording</span>
					</router-link>
			      	<router-link to="/sign-in" class="btn-filter btn-blue
                      " @click="e => e.preventDefault()">
						<svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
							<path fill-rule="evenodd" clip-rule="evenodd" d="M18 10C18 14.4183 14.4183 18 10 18C5.58172 18 2 14.4183 2 10C2 5.58172 5.58172 2 10 2C14.4183 2 18 5.58172 18 10ZM12 7C12 8.10457 11.1046 9 10 9C8.89543 9 8 8.10457 8 7C8 5.89543 8.89543 5 10 5C11.1046 5 12 5.89543 12 7ZM9.99993 11C7.98239 11 6.24394 12.195 5.45374 13.9157C6.55403 15.192 8.18265 16 9.99998 16C11.8173 16 13.4459 15.1921 14.5462 13.9158C13.756 12.195 12.0175 11 9.99993 11Z" fill="#111827"/>
						</svg>
						<span>New Request</span>
					</router-link>
					<router-link to="/sign-in" class="btn-filter
                    " @click="e => e.preventDefault()">
						<svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
							<path fill-rule="evenodd" clip-rule="evenodd" d="M18 10C18 14.4183 14.4183 18 10 18C5.58172 18 2 14.4183 2 10C2 5.58172 5.58172 2 10 2C14.4183 2 18 5.58172 18 10ZM12 7C12 8.10457 11.1046 9 10 9C8.89543 9 8 8.10457 8 7C8 5.89543 8.89543 5 10 5C11.1046 5 12 5.89543 12 7ZM9.99993 11C7.98239 11 6.24394 12.195 5.45374 13.9157C6.55403 15.192 8.18265 16 9.99998 16C11.8173 16 13.4459 15.1921 14.5462 13.9158C13.756 12.195 12.0175 11 9.99993 11Z" fill="#111827"/>
						</svg>
						<span>Add Filter</span>
					</router-link>
				    <router-link to="/sign-in" class="btn-filter
                    " @click="e => e.preventDefault()">
						<svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
							<path fill-rule="evenodd" clip-rule="evenodd" d="M18 10C18 14.4183 14.4183 18 10 18C5.58172 18 2 14.4183 2 10C2 5.58172 5.58172 2 10 2C14.4183 2 18 5.58172 18 10ZM12 7C12 8.10457 11.1046 9 10 9C8.89543 9 8 8.10457 8 7C8 5.89543 8.89543 5 10 5C11.1046 5 12 5.89543 12 7ZM9.99993 11C7.98239 11 6.24394 12.195 5.45374 13.9157C6.55403 15.192 8.18265 16 9.99998 16C11.8173 16 13.4459 15.1921 14.5462 13.9158C13.756 12.195 12.0175 11 9.99993 11Z" fill="#111827"/>
						</svg>
						<span>By Date</span>
					</router-link>
					<!-- / Header Search Input -->

				</a-col>
			</a-row>
		</template>
		<a-table :columns="columns" :data-source="data" :pagination="false">

			<template slot="details" slot-scope="details">
				<div class="table-avatar-info">
					<a-avatar shape="square" :src="details.avatar" />
					<div class="avatar-info">
						<h6>{{ details.header }}</h6>
						<p>{{ details.info }}</p>
					</div>
				</div>
			</template>

			<template slot="func" slot-scope="func">
				<div class="details-info">
					<h6 class="m-0">{{ func.views }}</h6>
					<p class="m-0 font-regular text-muted">{{ func.department }}</p>
				</div>
			</template>

			<template slot="size" slot-scope="size">
				<div class="tag-size">
					<h6 class="m-0">{{ size }}</h6>
				</div>
			</template>

			<template slot="editBtn" slot-scope="row">
				<a-button type="link" :data-id="row.key" class="btn-edit">
					...
				</a-button>
			</template>

		</a-table>
	</a-card>
	<!-- / detailss Table Card -->

</template>

<script>

	export default ({
		props: {
			data: {
				type: Array,
				default: () => [],
			},
			columns: {
				type: Array,
				default: () => [],
			},
		},
		data() {
			return {
				// Active button for the "detailss" table's card header radio button group.
				detailsHeaderBtns: 'all',
			}
		},
	})

</script>

<style>
.btn-filter {
    border: 1px solid #E2E5ED;
    border-radius: 20px ;
    padding:2px 5px;
    color: gray;
    border-color: #E2E5ED;
}

.btn-filter:hover{
    color: black;
}

.btn-blue {
    background-color: #0DABD8;
    border-color: #0DABD8;
    color: white;
}
.btn-red {
    background-color: #EF5350;
    border-color: #EF5350;
    color: white;
}
</style>