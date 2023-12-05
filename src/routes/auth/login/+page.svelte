<script lang="ts">
	import Nightmare from '../../../components/Nightmare.svelte';
	import { initializeApp } from 'firebase/app';
	import {
		getAuth,
		signInWithEmailAndPassword,
		signInWithPopup,
		TwitterAuthProvider,
		sendPasswordResetEmail
	} from 'firebase/auth';
	import Swal from 'sweetalert2';

	export let data: any;

	const auth = getAuth(initializeApp(data.firebase_config));

	let email: string = '';
	let password: string = '';

	const login = () => {
		if (email === '' || password === '')
			return Swal.fire(
				'Error:',
				'One of the fields provided down below are empty. Please ensure that they are filled.',
				'error'
			);

		signInWithEmailAndPassword(auth, email, password)
			.then((userCredential) => {
				const user = userCredential.user;
				console.log(user);
			})
			.catch((error) => {
				const errorCode = error.code;
				const errorMessage = error.message;

				return Swal.fire(`Error ${errorCode}`, errorMessage, 'error');
			});
	};

	const twitter = () => {
		signInWithPopup(auth, new TwitterAuthProvider())
			.then((result: any) => {
				const user = result.user;
				console.log(user);
			})
			.catch((error) => {
				const errorCode = error.code;
				const errorMessage = error.message;

				return Swal.fire(`Error ${errorCode}`, errorMessage, 'error');
			});
	};

	const forgotpasswd = () => {
		if (email === '')
			return Swal.fire(
				'Error:',
				'The "email" field is empty. Please ensure that all fields are filled.',
				'error'
			);

		sendPasswordResetEmail(auth, email)
			.then(() => {
				return Swal.fire(
					'Password Reset',
					'We have sent an email to the address provided. Please visit the link provided to reset your password.',
					'success'
				);
			})
			.catch((error) => {
				const errorCode = error.code;
				const errorMessage = error.message;

				return Swal.fire(`Error ${errorCode}`, errorMessage, 'error');
			});
	};
</script>

<Nightmare Title="Login" Description="Login into Popkat CDN Dashboard" />

<div class="flex min-h-full flex-col justify-center px-6 py-12 lg:px-8">
	<div class="sm:mx-auto sm:w-full sm:max-w-sm">
		<img class="mx-auto h-[60px]" src="/logo.png" alt="Popkat" />
		<h2 class="mt-6 text-center text-2xl font-bold leading-9 tracking-tight text-white">
			Login to your account
		</h2>
	</div>

	<div class="mt-10 sm:mx-auto sm:w-full sm:max-w-sm">
		<form class="space-y-6">
			<div>
				<label for="email" class="block text-sm font-bold leading-6 text-white">Email address</label
				>
				<div class="mt-2">
					<input
						id="email"
						name="email"
						type="email"
						autocomplete="email"
						placeholder="Email Address"
						bind:value={email}
						required
						class="block w-full text-black rounded-md border-0 py-1.5 shadow-sm ring-1 ring-inset ring-gray-900 placeholder:text-gray-900 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
					/>
				</div>
			</div>

			<div>
				<div class="flex items-center justify-between">
					<label for="password" class="block text-sm font-bold leading-6 text-white">Password</label
					>
					<div class="text-sm">
						<button
							on:click={forgotpasswd}
							type="button"
							class="font-bold text-indigo-600 hover:text-indigo-500">Forgot password?</button
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
						bind:value={password}
						required
						class="block w-full rounded-md border-0 py-1.5 text-black shadow-sm ring-1 ring-inset ring-gray-900 placeholder:text-gray-900 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
					/>
				</div>
			</div>

			<div>
				<button
					type="button"
					class="flex w-full justify-center rounded-md bg-indigo-600 px-3 py-1.5 text-sm font-semibold leading-6 text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
					on:click={login}><i class="flex mt-1 mr-2 fa-solid fa-unlock"></i> Login</button
				>
			</div>

			<button
				type="button"
				class="flex justify-center rounded-md bg-black px-3 py-1.5 text-sm font-semibold leading-6 text-white shadow-sm hover:bg-gray-800 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
				on:click={twitter}
				>Login with <i class="flex fa-brands fa-x-twitter mt-1.5 ml-1"></i>
			</button>
		</form>
	</div>
</div>
