<script lang="ts">
    import Nightmare from '../../../components/Nightmare.svelte';
</script>

<Nightmare
	Title="Login"
	Description="Login into Popkat CDN Dashboard"
/>

<div class="flex min-h-full flex-col justify-center px-6 py-12 lg:px-8">
	<div class="sm:mx-auto sm:w-full sm:max-w-sm">
		<img class="mx-auto h-[60px]" src="/logo.png" alt="Popkat" />
		<h2 class="mt-6 text-center text-2xl font-bold leading-9 tracking-tight text-white">
			Login to your account
		</h2>
	</div>

	<div class="mt-10 sm:mx-auto sm:w-full sm:max-w-sm">
		<form class="space-y-6" action="#" method="POST">
			<div>
				<label for="email" class="block text-sm font-bold leading-6 text-white"
					>Email address</label
				>
				<div class="mt-2">
					<input
						id="email"
						name="email"
						type="email"
						autocomplete="email"
                        placeholder="Email Address"
						required
						class="block w-full text-black rounded-md border-0 py-1.5 shadow-sm ring-1 ring-inset ring-gray-900 placeholder:text-gray-900 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
					/>
				</div>
			</div>

			<div>
				<div class="flex items-center justify-between">
					<label for="password" class="block text-sm font-bold leading-6 text-white"
						>Password</label
					>
					<div class="text-sm">
						<a href="/auth/forgotpasswd" class="font-bold text-indigo-600 hover:text-indigo-500"
							>Forgot password?</a
						>
					</div>
				</div>
				<div class="mt-2">
					<input
						id="password"
						name="password"
						type="password"
						autocomplete="current-password"
                        placeholder="Password"
						required
						class="block w-full rounded-md border-0 py-1.5 text-black shadow-sm ring-1 ring-inset ring-gray-900 placeholder:text-gray-900 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
					/>
				</div>
			</div>

			<div>
				<button
					type="submit"
					class="flex w-full justify-center rounded-md bg-indigo-600 px-3 py-1.5 text-sm font-semibold leading-6 text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
					><i class="flex mt-1 mr-2 fa-solid fa-unlock"></i> Login</button
				>
			</div>
		</form>
	</div>
</div>
