<script lang="ts">
	import Button from '$lib/components/ui/button/button.svelte';
	import Input from '$lib/components/ui/input/input.svelte';

	let videoFile: File | null = $state(null);
	let outputFormat = $state('mp4');

	function handleSubmit() {
		console.log({
			videoFile,
			outputFormat
		});
	}

	function handleFileChange(event: Event) {
		const target = event.target as HTMLInputElement;
		if (target.files) {
			videoFile = target.files[0];
		}
	}
</script>

<div class="mx-auto max-w-xl rounded-lg bg-white p-6 shadow-md">
	<h1 class="mb-6 text-2xl font-bold">FFmpeg Video Transformation</h1>

	<form on:submit|preventDefault={handleSubmit} class="space-y-4">
		<div>
			<label for="video-upload" class="mb-1 block text-sm font-medium text-gray-700">
				Upload Video
			</label>
			<Input
				type="file"
				id="video-upload"
				accept="video/*"
				on:change={handleFileChange}
				class="w-full rounded-md border border-gray-300 px-3 py-2 shadow-sm focus:border-primary focus:outline-none focus:ring-primary"
				required
			/>
		</div>

		<div>
			<label for="output-format" class="mb-1 block text-sm font-medium text-gray-700">
				Output Format
			</label>
			<select
				id="output-format"
				bind:value={outputFormat}
				class="w-full rounded-md border border-gray-300 px-3 py-2 shadow-sm focus:border-primary focus:outline-none focus:ring-primary"
			>
				<option value="mp4">MP4</option>
				<option value="webm">WebM</option>
				<option value="mov">MOV</option>
				<option value="avi">AVI</option>
			</select>
		</div>
		<Button type="submit">Transform Video</Button>
	</form>
</div>
