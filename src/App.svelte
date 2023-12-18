<script>
	let elapsedDays = "";
	let initDate = null;
	let endDate = null;

	function updateLocation(from, to) {
		const url = new URL(window.location.toString());
		url.searchParams.set("from", from);
		url.searchParams.set("to", to);
		history.replaceState({}, "", url);
	}

	function computeDays() {
		let init = new Date(initDate);
		let end = new Date(endDate);
		elapsedDays = Math.floor((end - init) / 1000 / 3600 / 24) + 1;
		updateLocation(initDate, endDate);
	}
</script>

<div class="card rounded shadow">
	<div class="card-body">
		<h1>Calculadora de días</h1>
		<div class="card-text">
			<p>
				<strong>Instrucciones:</strong> Selecciona los días inicial y final
				para ver el número de días transcurridos.
			</p>
			<div>
				<form on:submit|preventDefault={computeDays}>
					<div class="mb-3">
						<label for="inicioInput">Inicio</label>
						<input
							type="date"
							id="inicioInput"
							bind:value={initDate}
							required
							class="form-control"
						/>
					</div>
					<div class="mb-3">
						<label for="finInput">Fin</label>
						<input
							type="date"
							bind:value={endDate}
							id="finInput"
							required
							class="form-control"
						/>
					</div>
					<div>
						<input
							type="submit"
							value="Calcular"
							class="btn btn-primary float-end"
						/>
					</div>
				</form>
			</div>
			<div>
				<h3>
					Días transcurridos:
					<span
						class={elapsedDays
							? "badge rounded-pill bg-primary"
							: ""}
					>
						{elapsedDays || "-"}
					</span>
				</h3>
			</div>
		</div>
	</div>
</div>
