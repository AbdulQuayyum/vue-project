<template>
	<div>
		<a-layout-header>
			<a-row type="flex">

				<!-- Header Breadcrumbs & Title Column -->
				<a-col :span="24" :md="6">

					<!-- Header Breadcrumbs -->
					<a-breadcrumb>
						<a-breadcrumb-item><router-link to="/"> Pages</router-link></a-breadcrumb-item>
						<a-breadcrumb-item>{{ this.$route.name }}</a-breadcrumb-item>
					</a-breadcrumb>
					<!-- / Header Breadcrumbs -->

					<!-- Header Page Title -->
					<div class="ant-page-header-heading">
						<span class="ant-page-header-heading-title">{{ this.$route.name }}</span>
					</div>
					<!-- / Header Page Title -->

				</a-col>
				<!-- / Header Control Column -->

			</a-row>
		</a-layout-header>
		<a-row :gutter="24" type="flex">

			<!-- detailss Table Column -->
			<a-col :span="24" class="mb-24">

				<!-- detailss Table Card -->
				<CardTable
					:data="table1Data"
					:columns="table1Columns"
				></CardTable>
				<!-- / detailss Table Card -->

			</a-col>
			<!-- / detailss Table Column -->

		</a-row>
	</div>
</template>

<script>

import CardTable from "../components/Cards/CardTable"

	const table1Columns = [
		{
			title: 'Recordings',
			dataIndex: 'details',
			scopedSlots: { customRender: 'details' },
		},
		{
			title: 'Views',
			dataIndex: 'func',
			scopedSlots: { customRender: 'func' },
		},
		{
			title: 'Size',
			dataIndex: 'size',
			scopedSlots: { customRender: 'size' },
		},
		{
			title: 'Last Modified',
			dataIndex: 'employed',
			class: 'text-muted',
		},
		{
			title: '',
			scopedSlots: { customRender: 'editBtn' },
			width: 50,
		},
	];

	const table1Data = [
		{
			key: '1',
			details: {
				avatar: 'images/face-2.jpg',
				header: 'Getting it right the first time',
				info: 'The Video description is shown here if the user has added it.',
			},
			func: {
				views: '324',
			},
			size: '946 Kb',
			employed: 'Last 3 Months',
		},
		{
			key: '2',
			details: {
				avatar: 'images/face-3.jpg',
				header: 'Getting it right the first time',
				info: 'The Video description is shown here if the user has added it.',
			},
			func: {
				views: '324',
			},
			size: '946 Kb',
			employed: 'Last 3 Months',
		},
		{
			key: '3',
			details: {
				avatar: 'images/face-1.jpg',
				header: 'Getting it right the first time',
				info: 'The Video description is shown here if the user has added it.',
			},
			func: {
				views: '324',
			},
			size: '946 Kb',
			employed: 'Last 3 Months',
		},
		{
			key: '4',
			details: {
				avatar: 'images/face-4.jpg',
				header: 'Getting it right the first time',
				info: 'The Video description is shown here if the user has added it.',
			},
			func: {
				views: '324',
			},
			size: '946 Kb',
			employed: 'Last 3 Months',
		},
		{
			key: '5',
			details: {
				avatar: 'images/face-5.jpeg',
			header: 'Getting it right the first time',
				info: 'The Video description is shown here if the user has added it.',
			},
			func: {
				views: '324',
			},
			size: '946 Kb',
			employed: 'Last 3 Months',
		},
		{
			key: '6',
			details: {
				avatar: 'images/face-6.jpeg',
				header: 'Getting it right the first time',
				info: 'The Video description is shown here if the user has added it.',
			},
			func: {
				views: '324',
			},
			size: '946 Kb',
			employed: 'Last 3 Months',
		},
	];
	

	export default ({
		components: {
			CardTable,
		},
		data() {
			return {
				table1Data: table1Data,

				table1Columns: table1Columns,
			}
		},
	})

</script>

<style lang="scss">
</style>