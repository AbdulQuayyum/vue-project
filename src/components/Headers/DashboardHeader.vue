<template>
	
	<!-- Main Sidebar -->
	<component :is="navbarFixed ? 'a-affix' : 'div'" :offset-top="top">

		<!-- Layout Header -->
		<a-layout-header>
			<a-row :gutter="24">
				<!-- Header Control Column -->
				<a-col :span="24" :md="24" style="display: flex; align-items: center; justify-content:space-between" class="header-control">
					<a-list item-layout="horizontal" class="header-notifications-list" :data-source="notificationsData" slot="overlay">
						<a-list-item slot="renderItem" slot-scope="item">
							<a-list-item-meta>
								<template #description>
									<svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
										<path fill-rule="evenodd" clip-rule="evenodd" d="M10 18C14.4183 18 18 14.4183 18 10C18 5.58172 14.4183 2 10 2C5.58172 2 2 5.58172 2 10C2 14.4183 5.58172 18 10 18ZM11 6C11 5.44772 10.5523 5 10 5C9.44772 5 9 5.44772 9 6V10C9 10.2652 9.10536 10.5196 9.29289 10.7071L12.1213 13.5355C12.5118 13.9261 13.145 13.9261 13.5355 13.5355C13.9261 13.145 13.9261 12.5118 13.5355 12.1213L11 9.58579V6Z" fill="#111827"/>
									</svg>
									<span>{{ item.time }}</span>
								</template>
								<a slot="title" href="#">{{ item.title }}</a>
								<a-avatar v-if="item.img"
									slot="avatar"
									shape="square"
									:src="item.img"
								/>
								<a-avatar v-else
									shape="square"
									slot="avatar"  v-html="item.svg"/>
								
							</a-list-item-meta>
						</a-list-item>
					</a-list>
				<div class="table-avatar-info">
					<a-avatar :size="44" shape="square" src="images/face-2.jpg" />
					  <div class="avatar-info">
						<h6 class="font-semibold m-0">John Doe</h6>
						<p>Johndoe@gmail.com</p>
				      </div>
				</div>
				<div :md="0" style="justify-content:space-between">
					<router-link to="/sign-in" class="btn-sign-in" @click="e => e.preventDefault()">
						<span>Projects</span>
					</router-link>
					<a-dropdown :trigger="['click']" class="btn-sign-in" overlayClassName="header-notifications-dropdown" :getPopupContainer="() => wrapper">
							<a class="ant-dropdown-link" @click="e => e.preventDefault()">
								<span>Tools & App</span> <span></span>
							</a>
						<a-list item-layout="horizontal" class="header-notifications-list" :data-source="notificationsData" slot="overlay">
							<a-list-item slot="renderItem" slot-scope="item">
								<a-list-item-meta>
									<a slot="title" href="#">{{ item.title }}</a>
								</a-list-item-meta>
							</a-list-item>
						</a-list>
					</a-dropdown>
						<router-link to="/sign-in" class="btn-sign-in" @click="e => e.preventDefault()">
						<span>Channels</span>
					</router-link>
					<router-link to="/sign-in" class="btn-sign-in" @click="e => e.preventDefault()">
						<span>Contacts</span>
					</router-link>
					<router-link to="/sign-in" class="btn-sign-in" @click="e => e.preventDefault()">
						<span>Analytics</span>
					</router-link>
					<router-link to="/sign-in" class="btn-sign-in" @click="e => e.preventDefault()">
					     <span>Settings</span>
					</router-link>
				</div>
				<div style="display: flex; align-items: center; justify-content:flex-start"><img class="brand" src="images/logo-ct-black.png" alt=""> 
				<span class="brand-text">Adilo</span></div>
				</a-col>
			</a-row>
		</a-layout-header>
		<!--  /Layout Header -->

	</component>
	<!-- / Main Sidebar -->

</template>

<script>

	const notificationsData = [
		{
			title: 'Snapbyte Recorder',
		},
		{
			title: 'AudioBounce',
		},
		{
			title: 'Sugar Voice',
		},
	] ;

	export default ({
		props: {
			// Header fixed status.
			navbarFixed: {
				type: Boolean,
				default: false,
			},

			// Sidebar collapsed status.
			sidebarCollapsed: {
				type: Boolean,
				default: false,
			},

			// Header notifications data.
			notificationsData: {
				type: Array,
				default: () => notificationsData,
			},
		},
		data() {
			return {
				// Fixed header/sidebar-footer ( Affix component ) top offset.
				top: 0,

				// Search input loading status.
				searchLoading: false,

				// The wrapper element to attach dropdowns to.
				wrapper: document.body,
			}
		},
		methods: {
			resizeEventHandler(){
				this.top = this.top ? 0 : -0.01 ;
				// To refresh the header if the window size changes.
				// Reason for the negative value is that it doesn't activate the affix unless
				// scroller is anywhere but the top of the page.
			},
			onSearch(value){
			}
		},
		mounted: function(){
			// Set the wrapper to the proper element, layout wrapper.
			this.wrapper = document.getElementById('layout-myrecordings') ;
		},
		created() {
			// Registering window resize event listener to fix affix elements size
			// error while resizing.
			window.addEventListener("resize", this.resizeEventHandler);
		},
		destroyed() {
			// Removing window resize event listener.
			window.removeEventListener("resize", this.resizeEventHandler);
		},
	})

</script>

<style lang="scss">
.brand {
	height: 50px;
	width: 50px;
}
.brand-text {
	font-weight: 900;
	font-size: 30px;
}

.table-avatar-info {
	display: flex;
}
.avatar-info {
h6 {
		font-size: 14px;
		line-height: 14px;
		margin-bottom: 3px;
	}
	p {
		font-size: 14px;
		font-weight: 700;
		color: gray;
	}
}
</style>
