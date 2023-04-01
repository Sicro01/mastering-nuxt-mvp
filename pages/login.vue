<template>
  <div class="prose w-full max-w-2xl h-9">
    <h1>Login to {{ title }}</h1>
    <button
      @click="login"
      class="bg-blue-500 text-white font-bold py-2 px-4 rounded">
      Login with Github
    </button>

  </div>
</template>

<script setup lang ="ts">
const { title } = useCourse();

const supabase = useSupabaseClient();

const login = async () => {
  const error = ref();
  try {
    const { error: signInError } = await supabase.auth.signInWithOAuth(
      {
        provider: 'github',
      });
    console.log('here 1');
    const user = useSupabaseUser();
    console.log('user', user);

    if (signInError) {
      error.value = signInError;
      console.log(signInError);
      console.log('here 1');
    }
  } catch (err) {
    {
      console.log('here 1');
      error.value = err;
      console.log(err);
    }
  }
};

</script>