<script setup lang="ts">
import { ref, reactive } from "vue";
import { useRouter } from "vue-router";

const router = useRouter();
const passwordType = ref<string>("password");
const isValid = ref(false);
const loading = ref(false);

const backNav = () => {
  router.back();
};

const form = reactive({
  phone: "",
  password: "",
});

const rules = reactive({
  password: (v: string) => !!v || "Password is required",
  phone: (v: string) => !!v || "Phone number is required",
  valid_phone: (v: string) =>
    /^0[789][01]\d{8}$/.test(v) || "Enter a valid phone number",
});

const handleSubmit = async () => {
  if (!isValid.value) return;

  loading.value = true;

  setTimeout(() => {
    router.push("/dashboard");
    loading.value = false;
  }, 3000);
};
</script>

<template>
  <v-container fluid class="signin-page">
    <v-btn
      @click="backNav"
      elevation="0"
      variant="text"
      class="mr-2"
      icon="mdi-arrow-left"
    />
    <div class="flex justify-center items-center">
      <img
        width="100"
        src="https://media.licdn.com/dms/image/v2/C4D0BAQHWFN4vkNFGWQ/company-logo_200_200/company-logo_200_200/0/1630579436099?e=1745452800&v=beta&t=JpcGZMFWwTh7mYJZEVnsiqIfxOPJv3yid8gQdsaG8WM"
        alt="logo"
      />
    </div>

    <!-- Card -->
    <div class="h-[85dvh] flex items-center justify-center">
      <v-card class="w-[327px] lg:w-[380px] max-h-[527px] pa-4">
        <v-card-title class="mb-5">
          <p class="text-sm text-[#626F86]">PROCUREMENT</p>
          <p class="font-medium">Sign in to your account</p>
        </v-card-title>
        <!-- Phone number -->
        <v-card-text>
          <v-form @submit.prevent v-model="isValid">
            <div>
              <label
                for="phone"
                class="block text-sm font-medium text-gray-700 mb-2"
                >Phone</label
              >
              <v-text-field
                id="phone"
                placeholder="Enter phone number"
                color="#0C66E4"
                variant="outlined"
                density="comfortable"
                rounded
                v-model="form.phone"
                :rules="[rules.phone, rules.valid_phone]"
                maxlength="11"
              />
            </div>

            <!-- Password -->
            <div>
              <label
                for="password"
                class="block text-sm font-medium text-gray-700 mb-2"
                >Password</label
              >
              <v-text-field
                id="password"
                placeholder="Enter password"
                @click:append-inner="
                  passwordType == 'password'
                    ? (passwordType = 'text')
                    : (passwordType = 'password')
                "
                :append-inner-icon="
                  passwordType == 'password'
                    ? 'mdi-eye-outline'
                    : 'mdi-eye-off-outline'
                "
                :type="passwordType"
                color="#0C66E4"
                variant="outlined"
                density="comfortable"
                rounded
                maxlength="8"
                v-model="form.password"
                :rules="[rules.password]"
              />
            </div>

            <v-checkbox label="Keep me signed in" color="#0C66E4"></v-checkbox>

            <!-- Submit btn -->
            <v-btn
              :loading="loading"
              type="submit"
              @click="handleSubmit"
              color="#0C66E4"
              class="w-full text-lg py-2 font-medium"
              >Proceed</v-btn
            >
            <br />
            <br />
            <v-divider :thickness="1" class="border-opacity-100" />
            <br />
            <br />
            <p class="cursor-pointer text-center text-sm text-[#44546F]">
              Forgot Password
            </p>
          </v-form>
        </v-card-text>
      </v-card>
    </div>
    <!-- /Card -->
  </v-container>
</template>

<style scoped>
.signin-page {
  background: rgba(8, 180, 214, 0.503);
  background: linear-gradient(
    to bottom,
    rgba(8, 180, 214, 0) 80%,
    rgba(8, 180, 214, 0.561) 120%,
    rgba(0, 255, 104, 0.6) 120%
  );
}
</style>
