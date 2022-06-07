<template>
    <v-container>
        <v-row justify="center">
            <v-col cols="12" md="4">
                <validation-observer
                    ref="observer"
                    
                >
                    <v-form @submit.prevent="submit">
                        <validation-provider
                            v-slot="{ errors }"
                            name="Name"
                        >

                        </validation-provider>
                        <v-text-field
                            v-mode="name"
                            :counter="10"
                            :rules="nameRules"
                            label="Name"
                        ></v-text-field>
    
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
                </validation-observer>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
import { required, digits, email, max, regex } from 'vee-validate/dist/rules'
import { extend, ValidationObserver, ValidationProvider, setInteractionMode } from 'vee-validate'

export default {

    data() {
        return {
            
        }
    },
}
</script>

<script>

</script>