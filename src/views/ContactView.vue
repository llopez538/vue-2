<template>
    <v-container>
        <v-row justify="center">
            <v-col cols="12" md="4">
                <ValidationObserver
                    ref="observer"
                    
                >
                    <v-form @submit.prevent="submit">
                        <ValidationProvider
                            v-slot="{ errors }"
                            name="Name"
                            rules="required|max:10"
                        >
                            <v-text-field
                                v-mode="name"
                                :counter="10"
                                :rules="nameRules"
                                :error-messages="errors"
                                label="Name"
                            ></v-text-field>
                        </ValidationProvider>
    
                        <v-text-field
                            v-model="email"
                            :rules="emailRules"
                            type="email"
                            label="Email"
                            required
                        ></v-text-field>
    
                        <v-select
                            v-model="select"
                            :items="items"
                            :rules="[v => !!v || 'Item is required']"
                            label="Item"
                            required
                        ></v-select>
    
                        <v-checkbox
                            v-model="checkbox"
                            :rules="[v => !!v || 'You must agreeto continue!']"
                            label="Do you agree? "
                            required
                        ></v-checkbox>
                        
                        <v-btn
                            class="mr-4"
                            type="submit"
                            :disable="invalid"
                        >
                            Submit
                        </v-btn>

                        <v-btn @click="clear">
                            Clear
                        </v-btn>
                    </v-form>
                </ValidationObserver>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
import { required, digits, email, max, regex } from 'vee-validate/dist/rules'
import { configure, extend, ValidationObserver, ValidationProvider, setInteractionMode } from 'vee-validate'

const config = {
  classes: {
    valid: 'is-valid',
    invalid: 'is-invalid'
  },
  bails: true,
  skipOptional: true,
  mode: 'aggressive',
  useConstraintAttrs: true
};

// Sets the options.
configure(config);
setInteractionMode('eager')

extend('required', {
    ...required,
    message: '{_field_} can not empty'
})

export default {
    components: {
        ValidationObserver,
        ValidationProvider
    },
    data() {
        return {
            
        }
    },
}
</script>

<script>

</script>