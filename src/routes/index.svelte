<script context="module">
	import { browser, dev } from '$app/env';

	// we don't need any JS on this page, though we'll load
	// it in dev so that we get hot module replacement...
	export const hydrate = dev;

	// ...but if the client-side router is already loaded
	// (i.e. we came here from elsewhere in the app), use it
	export const router = browser;

	// since there's no dynamic data here, we can prerender
	// it so that it gets served as a static asset in prod
	export const prerender = true;

	import RangeSlider from 'svelte-range-slider-pips';
</script>

<script>
	const price = 10;

	let value = [1, 1];
</script>

<svelte:head>
	<title>Landing</title>

	<style>
		.background {
			position: fixed;
			top: -50%;
			left: -50%;
			width: 200%;
			height: 200%;
			z-index: -1;
		}

		.background img {
			position: absolute;
			top: 0;
			left: 0;
			right: 0;
			bottom: 0;
			margin: auto;
			min-width: 50%;
			min-height: 50%;
		}

		.button {
			right: -100px;
			top: -100px;
			position: absolute;
			display: flex;
			flex-direction: row;
			background-color: #fff;
			height: 44px;
			width: 300px;
			border-radius: 44px;
			align-items: center;
			justify-content: center;
			text-decoration: none;
		}

		.button .icon {
			width: 24px;
			height: 24px;
			margin-left: 10px;
		}

		.button .label {
			text-transform: uppercase;
			letter-spacing: 1.5px;
			font-size: 14px;
			color: #fc3890;
			font-weight: 700;
			text-decoration: none;
		}

		.landing-container {
			display: flex;
			flex: 1;
			flex-direction: column;
			align-items: center;
			justify-content: center;
			margin-top: 158px;
		}

		.landing-content-container {
			background: #fff;
			border-radius: 20px;
			margin-top: 80px;
			max-width: 970px;
			min-height: 364px;
			position: relative;
		}

		.logo-container {
			display: flex;
			justify-content: center;
			position: absolute;
			left: 0;
			right: 0;
			top: -250px;
		}

		.logo {
			width: 858px;
			height: 445px;
		}

		.content-container {
			display: flex;
			flex: 1;
			padding: 90px 70px;
			z-index: 1;
		}

		.title {
			font-size: 24px;
			font-style: normal;
			font-weight: 600;
			line-height: 33px;
			letter-spacing: 0px;
			text-align: left;
			color: #fc3890;
		}

		.description p {
			font-size: 16px;
			font-style: normal;
			font-weight: 400;
			line-height: 35px;
			letter-spacing: 0px;
			text-align: left;
			line-height: 35px;
		}

		.description strong {
			font-weight: 600;
		}

		.content-inner-container {
			flex: 1;
			flex-direction: column;
		}

		.footer {
			position: fixed;
			bottom: 0;
			width: 100%;
			height: 422px;
			overflow: hidden;
		}

		.footer img {
			width: 100%;
		}

		.mint-slider-container {
			background-color: #f4f4f4;
			border-radius: 100px;
			height: 65px;
			padding: 0 30px;
		}

		#mint-slider {
			background-color: #fff;
			box-shadow: inset 0px 2px 3px rgba(155, 47, 96, 0.2);
			height: 7px;
			top: 20px;
		}

		#mint-slider .rangeNub {
			background-color: transparent;
			background: url('/sliderIcon.svg') no-repeat;
			height: 30px;
			width: 30px;
			top: -5px;
			transform: none;
		}

		#mint-slider .rangePips {
			bottom: -20px;
		}

		#mint-slider .rangeBar {
			background-color: #fc3890;
		}

		#mint-slider .pip {
			background-color: transparent;
		}

		#mint-slider .pip .pipVal {
			font-size: 10px;
		}

		#mint-slider .pip.selected {
			height: 0.4em !important;
		}

		#mint-slider .pip.selected .pipVal {
			top: 0.4em !important;
		}

		.mint-description {
			display: flex;
			flex-direction: row;
			margin-top: 13px;
			justify-content: space-between;
		}

		.mint-description p {
			font-style: normal;
			font-weight: normal;
			font-size: 12px;
			line-height: 136%;
			letter-spacing: 2px;
			text-transform: uppercase;
		}

		.mint-button-container {
			display: flex;
			flex: 1;
			justify-content: flex-end;
		}

		.mint-button {
			display: flex;
			flex-direction: row;
			justify-content: center;
			align-items: center;
			padding: 10px 32px;
			width: 106px;
			height: 41px;
			background: #fc3890;
			border-radius: 100px;
			margin-top: 40px;
			align-self: right;
		}

		.mint-button span {
			font-style: normal;
			font-weight: bold;
			font-size: 14px;
			line-height: 21px;
			text-align: center;
			letter-spacing: 1.5px;
			color: #ffffff;
			text-transform: uppercase;
		}

		@media only screen and (max-width: 1170px) {
			.button {
				left: 0;
				right: 0;
				top: -200px;
				margin: auto;
			}
		}

		@media only screen and (max-width: 970px) {
			.content-container {
				flex-direction: column;
				height: 100%;
			}
		}
	</style>
</svelte:head>

<div class="background">
	<img alt="background" src={'/background.svg'} />
</div>

<div class="landing-container">
	<div class="landing-content-container">
		<a href="#" class="button">
			<span class="label">Connect your wallet</span>

			<img class="icon" alt="arrow" src={'/arrow.svg'} />
		</a>

		<div class="logo-container">
			<img alt="logo" class="logo" src={'/logo.svg'} />
		</div>

		<div class="content-container">
			<div class="content-inner-container">
				<h1 class="title">Get yout ticket today!</h1>

				<div class="description">
					<p>
						Current minting price is <strong>1,5 ADA per ticket</strong>. Select how many you would
						like to buy via the slider on the side. After that please connect your wallet.
					</p>
				</div>
			</div>

			<div class="content-inner-container">
				<div class="mint-slider-container">
					<RangeSlider
						bind:values={value}
						id="mint-slider"
						range="min"
						min={1}
						max={5}
						pips
						pipstep={1}
						all="label"
						hoverable={false}
						on:change={({ detail }) => {
							value = [1, detail.values];
						}}
					/>
				</div>

				<div class="mint-description">
					<p>Quantity: {value}</p>

					<p>Minting price: {price} ADA</p>
				</div>

				<div class="mint-button-container">
					<a href="#" class="mint-button">
						<span>Mint</span>
					</a>
				</div>
			</div>
		</div>
	</div>
</div>

<div class="footer">
	<img alt="footer" src={'/footer.svg'} />
</div>
