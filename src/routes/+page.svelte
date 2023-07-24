<script lang="ts">
	export let pc: string;
	export let library: string;
	export let media: string;
	export let secured: boolean = true;
	export let kill: string;
	export let access: string;
</script>

<h1>RFID tag</h1>

<input type="checkbox" bind:checked={secured} id="secured" />
<input type="text" bind:value={pc} id="pc" />

{pc}
{library}
{media}
{secured}
{kill}
{access}

<figure>
	<table>
		<thead>
			<tr>
				<th colspan="2">EPC-CRC (Block 0)</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<th>size</th>
				<td>16 bit / 2 byte / 1 block</td>
			</tr>
			<tr>
				<th>blockNo</th>
				<td>1</td>
			</tr>
			<tr>
				<th>bits</th>
				<td class="bits">00011001 11101001</td>
			</tr>
			<tr>
				<th>bytes</th>
				<td>19 E9</td>
			</tr>
			<tr>
				<th>usage</th>
				<td>CRC</td>
			</tr>
		</tbody>

		<thead>
			<tr>
				<th colspan="2">EPC-PC (Block 1)</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<th>size</th>
				<td>16 bit / 2 byte / 1 block</td>
			</tr>
			<tr>
				<th>blockNo</th>
				<td>1</td>
			</tr>
			<tr>
				<th>bits</th>
				<td class="bits">00011001 11101001</td>
			</tr>
			<tr>
				<th>bytes</th>
				<td>19 E9</td>
			</tr>
			<tr>
				<th>usage</th>
				<td>RFID-Meta-Info</td>
			</tr>
			<tr>
				<th>readable</th>
				<td>????</td>
			</tr>
		</tbody>

		<thead>
			<tr>
				<th colspan="9">EPC-DATA (Block 2 bis 9, meist informell "EPC" genannt")</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<th>size</th>
				<td colspan="8">128 bit / 16 byte / 8 block</td>
			</tr>
			<tr>
				<th>blockNo</th>
				<td>2</td>
				<td>3</td>
				<td class="colored">4</td>
				<td class="colored">5</td>
				<td class="colored">6</td>
				<td class="colored">7</td>
				<td>8</td>
				<td>9</td>
			</tr>
			<tr>
				<th>bits</th>
				<td class="bits">00011001 11101001</td>
				<td class="bits">00011001 11101001</td>
				<td class="bits colored">00011001 11101001</td>
				<td class="bits colored">00011001 11101001</td>
				<td class="bits colored">00011001 11101001</td>
				<td class="bits colored">00011001 11101001</td>
				<td class="bits">00011001 11101001</td>
				<td class="bits">00011001 11101001</td>
			</tr>
			<tr>
				<th>bytes</th>
				<td>19 E9</td>
				<td>19 E9</td>
				<td class="colored">19 E9</td>
				<td class="colored">19 E9</td>
				<td class="colored">19 E9</td>
				<td class="colored">19 E9</td>
				<td>00 00</td>
				<td>00 0{secured ? 1 : 0}</td>
			</tr>
			<tr>
				<th>usage</th>
				<td colspan="2">Bibliothekskennung (URN Code 40 enc)</td>
				<td colspan="4" class="colored">Mediennummer (als Zahl)</td>
				<td colspan="2">Variablen (als Bitflags)</td>
			</tr>
			<tr>
				<th>readable</th>
				<td colspan="2">D E 2 9 0 PAD</td>
				<td colspan="4" class="colored">123456789</td>
				<td colspan="2">gesichert</td>
			</tr>
		</tbody>

		<thead>
			<tr>
				<th colspan="7">TID</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<th>size</th>
				<td colspan="6">96 bit / 12 byte / 6 block</td>
			</tr>
			<tr>
				<th>blockNo</th>
				<td>0</td>
				<td>1</td>
				<td>2</td>
				<td>3</td>
				<td>4</td>
				<td>5</td>
			</tr>
			<tr>
				<th>bits</th>
				<td class="bits">00011001 11101001</td>
				<td class="bits">00011001 11101001</td>
				<td class="bits">00011001 11101001</td>
				<td class="bits">00011001 11101001</td>
				<td class="bits">00011001 11101001</td>
				<td class="bits">00011001 11101001</td>
			</tr>
			<tr>
				<th>bytes</th>
				<td>19 E9</td>
				<td>19 E9</td>
				<td>19 E9</td>
				<td>19 E9</td>
				<td>19 E9</td>
				<td>19 E9</td>
			</tr>
			<tr>
				<th>usage</th>
				<td colspan="6">Global eindeutige Tag ID, nicht wiederbeschreibbar</td>
			</tr>
		</tbody>

		<thead>
			<tr>
				<th colspan="5">RES ("reserved")</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<th>size</th>
				<td colspan="4">64 bit / 8 byte / 4 block</td>
			</tr>
			<tr>
				<th>blockNo</th>
				<td>0</td>
				<td>1</td>
				<td class="colored">2</td>
				<td class="colored">3</td>
			</tr>
			<tr>
				<th>bits</th>
				<td class="bits">00011001 11101001</td>
				<td class="bits">00011001 11101001</td>
				<td class="bits colored">00011001 11101001</td>
				<td class="bits colored">00011001 11101001</td>
			</tr>
			<tr>
				<th>bytes</th>
				<td>19 E9</td>
				<td>19 E9</td>
				<td class="colored">19 E9</td>
				<td class="colored">19 E9</td>
			</tr>
			<tr>
				<th>usage</th>
				<td colspan="2">Kill Password </td>
				<td colspan="2" class="colored">Access Password</td>
			</tr>
		</tbody>
	</table>
</figure>

<style>
	.bits {
		white-space: nowrap;
	}
	.colored {
		background-color: var(--primary-focus);
	}
</style>
