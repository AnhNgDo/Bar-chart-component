<script>
	import Logo from '/src/logo.svg';
	import Chart from 'svelte-frappe-charts';

	// chart data
	let data = {
		labels: ['Mon', 'Tues', 'Wed', 'Thurs', 'Fri', 'Sat', 'Sun'],
		datasets: [
			{
				values: [17.45, 34.91, 52.36, 31.07, 23.39, 43.28, 25.48]
			}
		]
	};

	// chart interaction
	let selected;

	const onDataSelect = (event) => {
		console.log('Data select event fired!', event);
		selected = event;
	};
</script>

<svelte:head>
	<title>Expenses chart component | Frontend Mentor Challenge</title>
</svelte:head>

<!-- Fill screen with background -->
<div class="grid min-h-screen place-items-center bg-orange-50">
	<!-- Dashboard component -->
	<div class="w-96 max-w-full">
		<!-- My Balance Component -->
		<div class="flex items-center justify-between rounded-xl bg-orange-primary p-4">
			<div>
				<p class="text-sm text-white">My Balances</p>
				<p class="text-2xl text-white">$921.48</p>
			</div>
			<div><img src={Logo} alt="" class="w-12" /></div>
		</div>
		<!-- Chart & Stats component -->
		<div class="mt-4 rounded-xl bg-white p-4">
			<div class="text-2xl font-bold">Spending - Last 7 days</div>
			<!-- Note: display:flex does not work with svelte-frappe-charts -->
			<div>
				<Chart
					{data}
					type="bar"
					height="300"
					barOptions={{ spaceRatio: 0.2 }}
					axisOptions={{ xAxisMode: 'tick', yAxisMode: 'tick' }}
					colors={['#EC755D']}
					isNavigable={true}
				/>
			</div>
			<hr />
			<div class="mt-4 grid grid-cols-2">
				<p class="col-span-2 text-gray-500">Total this month</p>
				<p class="row-span-2 text-3xl">$478.33</p>
				<p class="place-self-end text-xs text-gray-500">+2.4%</p>
				<p class="place-self-end text-xs">from last month</p>
			</div>
		</div>
	</div>
</div>
