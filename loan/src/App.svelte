<script>
	let interestRate = 3;
	let loanAmount = 2000000;
	let years = 30;
	const MONTHS_PER_YEAR = 12;

	$: months = years * MONTHS_PER_YEAR;
	$: monthlyInterestRate = interestRate / 100 / MONTHS_PER_YEAR;
	$: numerator = loanAmount * monthlyInterestRate;
	$: denominator = 1 - (1 + monthlyInterestRate) ** -months;
	$: payment = 
		!loanAmount || !years ? 0 :
		interestRate ? numerator / denominator :
		loanAmount / months;
</script>

<label for="loan">Loan Amount</label>
<input type="number" id="loan" bind:value={loanAmount}>

<label for="loan">Years</label>
<input type="number" id="interest" bind:value={interestRate}>

<label for="loan">Years</label>
<input type="number" id="years" bind:value={years}>

<div>
	Monthly Payment: ${payment.toFixed(2)}
</div>



<style>
	
	
</style>