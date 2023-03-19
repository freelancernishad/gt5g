<template>
    <div>


        <header class="header-text" style="background-color: #0036ca;margin-bottom: -16px;">
        <p class="py-2 text-white">Recharge </p>
    </header>
    <form @submit.stop.prevent="onSubmit">
    <main class="mx-3">
        <div class="bg-white lh-1 mt-4 py-3 topp w-100 shadow">
            <p class="ms-2">Current Balance</p>
            <p class="fs-1 fw-bold py-1 text-center">৳{{ parseFloat(row.user.balance).toFixed(2) }}</p>
        </div>
        <div class="bg-white lh-1 mt-3 w-100 shadow">
          <input type="text" v-model="form.amount" class="border-primary py-3 w-100">
        </div>


    </main>
<section class="fw-bold mt-3 mx-3">
    <div class="grid-container">
        <p class="bg-white py-3 shadow text-center w-100" :class="{ 'active':form.amount == 1100 }" @click="form.amount = 1100">৳1100</p>
        <p class="bg-white py-3 shadow text-center w-100" :class="{ 'active':form.amount == 1200 }" @click="form.amount = 1200">৳1200</p>
        <p class="bg-white py-3 shadow text-center w-100" :class="{ 'active':form.amount == 2600 }" @click="form.amount = 2600">৳2600</p>
        <p class="bg-white py-3 shadow text-center w-100" :class="{ 'active':form.amount == 6000 }" @click="form.amount = 6000">৳6000</p>
        <p class="bg-white py-3 shadow text-center w-100" :class="{ 'active':form.amount == 9000 }" @click="form.amount = 9000">৳9000</p>
        <p class="bg-white py-3 shadow text-center w-100" :class="{ 'active':form.amount == 12000 }" @click="form.amount = 12000">৳12000</p>
        <p class="bg-white py-3 shadow text-center w-100" :class="{ 'active':form.amount == 24000 }" @click="form.amount = 24000">৳24000</p>
        <p class="bg-white py-3 shadow text-center w-100" :class="{ 'active':form.amount == 25000 }" @click="form.amount = 25000">৳25000</p>


      </div>
      <div class="bg-white border border-2 border-primary  mt-3 py-3 shadow w-100">

        <div class="d-flex gap-2 ms-2 w-50">
            <p>Pay Type</p> <img src="https://static.vecteezy.com/system/resources/previews/010/141/449/original/check-mark-icon-sign-symbol-design-free-png.png" alt="" style="width: 25px;"> <p>onepay</p>
        </div>

    </div>
    <button class="btn btn-primary mt-3" type="submit">Recharge Now</button>
</section>
</form>







    </div>
</template>

<script>
export default {
    data() {
        return {
               popup:false,
            form: {
                amount: '',
            },


            payMethods: '',

            amount: 0,
            step: 1,
            copyMessage:'',
            rates:'',
            con:false,
        }
    },
    methods: {


         randomLetter(length) {
                let result = 'S'+this.dateformatglobal()[10]+this.dateformatglobal()[11]+this.dateformatglobal()[12]+Math.floor(Math.random() * (999999999999 - 11111111111));
                return result;
            },
        async onSubmit() {

            if (this.settings.min_deposit > Number(this.form.amount)) {
                Notification.customError(`Minimum deposit amount ${this.settings.min_deposit}`);
            } else {
                this.form['orderid'] = this.randomLetter(20);
                localStorage.setItem('rechargeData',JSON.stringify(this.form))
                var regTimer = new Date(new Date().getTime() + 300000);
                localStorage.setItem('regTimer',regTimer);
                this.$router.push({ name: 'rechargepage' });
            }


        },



    },
    mounted() {


    },
}
</script>
<style scoped>
.mainitem {
    display: flex !important;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: space-between;
}
.money-style {
    text-align: center;
    width: 31%;
    border-radius: 5px;
    background-color: #eceded;
    color: #000;
    font-size: 15px;
    margin: 7px 1%;
    height: 50px;
    box-sizing: border-box;
    line-height: 18px;
    display: flex;
    align-items: center;
    justify-content: center;
}
.active {
    color: #fff;
    background: #0036ca !important;
}
button.btn.btn-primary {
    background: #0036ca !important;
    border: #0036ca !important;
    height: 38px;
    width:100%;
}

.grid-container {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        grid-gap: 5px;
      }



</style>
