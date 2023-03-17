<template>
    <div>






  <form @submit.stop.prevent="onSubmit">


    <header>


      <div class="heeeeee" style="background: #419EFF; color: #fff;">
   <p>পেমেন্ট তথ্য</p> </div>


</header>

    <div class="text-center mt-4">
    <img src="https://checkout-bdt.onepay.news/static/img/pixlogo.2432dd36.png" alt="" style="width: 70px;">
    <p>One Pay</p>
</div>


<div class="mx-3">
  <div class="mx-3 text-end"><a href="javascript:void(0)" @click="$router.go(-1)" class="text-decoration-none text-warning-emphasis" style="font-size: 12px;color: orange;">একাউন্ট সুইচ করতে ক্লিক করুন</a></div>

</div>
<div class="border border-top-0 mb-4 mx-3 rounded">
  <p class="bg-primary px-3 py-1 text-white headFont" v-if="row.name=='Bkash'"> স্টেপ ১. বিকাশ ইনফর্মেশন </p>
  <p class="bg-primary px-3 py-1 text-white headFont" v-else-if="row.name=='Nagad'"> স্টেপ ১. নগদ ইনফর্মেশন </p>
  <p class="bg-primary px-3 py-1 text-white headFont" v-else-if="row.name=='Rocket'"> স্টেপ ১. রকেট ইনফর্মেশন </p>
  <div class="d-flex justify-content-between mx-4" style="border-bottom: 1px dotted black;">

    <p class="text-body-secondary mb-1 textFontSize" v-if="row.name=='Bkash'">বিকাশ একাউন্ট</p>
    <p class="text-body-secondary mb-1 textFontSize" v-else-if="row.name=='Nagad'">নগদ একাউন্ট</p>
    <p class="text-body-secondary mb-1 textFontSize" v-else-if="row.name=='Rocket'">রকেট একাউন্ট</p>
    <p class="mb-1" style="font-size:12px"> {{ paymentNumber }}</p>
  </div>

  <div class="d-flex justify-content-between mx-4 fw-bold mt-2">
    <p class="fs-6  textFontSize"> পরিমাণ</p>
    <p class="fs-6 text-danger"> {{ form.amount }} TK</p>
  </div>

</div>
<!-- <hr class="mx-4"> -->

<div class="border border-top-0 mb-4 mx-3 rounded">
  <p class="bg-primary px-3 py-1 text-white mb-1 headFont" v-if="row.name=='Bkash'"> ধাপ 2. বিকাশ ট্রান্সফারের মাধ্যমে আপনি যে পরিমাণ রিচার্জ করতে চান তা আমাদের কাছে ট্রান্সফার করুন। </p>
  <p class="bg-primary px-3 py-1 text-white mb-1 headFont" v-else-if="row.name=='Nagad'"> ধাপ 2. নগদ ট্রান্সফারের মাধ্যমে আপনি যে পরিমাণ রিচার্জ করতে চান তা আমাদের কাছে ট্রান্সফার করুন। </p>
  <p class="bg-primary px-3 py-1 text-white mb-1 headFont" v-else-if="row.name=='Rocket'"> ধাপ 2. রকেট ট্রান্সফারের মাধ্যমে আপনি যে পরিমাণ রিচার্জ করতে চান তা আমাদের কাছে ট্রান্সফার করুন। </p>
  <p class="ms-3 my-1">
    <span class="textFontSize"><span color="red">*</span> অর্থপ্রদানের পরে অনুগ্রহ করে আপনার [লেনদেন আইডি] অনুলিপি<br>করুন</span>
  </p>
</div>
<div class="border border-top-0 mb-4 mx-3 rounded">
  <p class="bg-primary px-3 py-1 text-white mb-1 headFont">
    ধাপ 3। রিচার্জ সম্পূর্ণ করতে অনুগ্রহ করে লেনদেন আইডি লিখুন
  </p>
  <div class="text-center">

    <img v-if="row.name=='Bkash'" :src="$asseturl+'Recharge/bkash_tnxid_2.png'" alt="" class="w-50">
    <img v-else-if="row.name=='Nagad'" :src="$asseturl+'Recharge/nagad_tnxid_1.jpg'" alt="" class="w-50">
    <img  v-else-if="row.name=='Rocket'" src="" alt="" class="w-50">

  </div>
  <div class="">

    <input class="form-control mb-3 onepaynumberInput" v-if="row.name=='Bkash'" v-model="form.trx" type="text" placeholder="১০ সংখ্যার লেনদেন আইডি">
    <input class="form-control mb-3 onepaynumberInput" v-if="row.name=='Nagad'" v-model="form.trx" type="text" placeholder="৮ সংখ্যার লেনদেন আইডি">
    <input class="form-control mb-3 onepaynumberInput" v-if="row.name=='Rocket'" v-model="form.trx" type="text" placeholder="১০ সংখ্যার লেনদেন আইডি">
  </div>

</div>
<div class="mb-5 mx-3">
  <button type="button" class="btn btn-secondary btn-sm px-3 py-2 rounded-4" style="    padding: 7px 8px !important;   margin-top: 10px;" @click="onCancel">অর্ডার বাতিল করুন</button>
<button type="button" class=" btn btn-primary btn-sm px-3 py-2 rounded-4" style="     padding: 7px 8px !important;   margin-top: 10px;" @click="onSubmit">অর্ডার নিশ্চিত করুন</button>
</div>



</form>











    </div>
</template>

<script>
export default {
    data(){
        return {
              row: {},
              copyMessage:'111111',
              form:{
                method: '',
                amount: '',
                sender: '',
                screenshot: '',
                trx: '',
              },

              bkash: [
                '01401933621',
                '01902904383',
                ],

              nagad: [
                '01401933621',
                '01902904383',
                ],

              rocket: [
                '01863476555'
                ],

              settings: {},
              paymentNumber:''
        }
    },
    methods: {
          async getData() {


            var res = await this.callApi('get', `/api/admin/withdraw/gateway/${this.form.method}`, []);
            this.row = res.data;
            if(this.row.name=='Bkash'){
                const random = Math.floor(Math.random() * this.bkash.length);
                this.paymentNumber = this.bkash[random];
            }else if(this.row.name=='Nagad'){
                const random = Math.floor(Math.random() * this.nagad.length);
                this.paymentNumber = this.nagad[random];
            }else if(this.row.name=='Rocket'){
                const random = Math.floor(Math.random() * this.rocket.length);
                this.paymentNumber = this.rocket[random];
            }

        },



        async onSubmit() {
            this.con = true
                var id = localStorage.getItem('userid');
                this.form['user_id'] = id;
                var res = await this.callApi('post', `/api/admin/deposit`, this.form);
                // Notification.customSuccess(`Recharge Successfuly Complete`);


                this.$router.push({ name: 'rechargesuccess' });

        },
        onCancel(){
            localStorage.removeItem('regTimer');
            this.$router.push({ name: 'rechargeFailed' });
        }

    },
    mounted() {
        this.form = JSON.parse(localStorage.getItem('rechargeData'));
            this.getData();









            // console.log(localStorage.getItem('rechargeData'))

    },
}
</script>

<style>

.textFontSize{
    font-size: 10px !important;
}
.headFont{
    font-size: 12px !important;
}

.li {
    display: flex;
    justify-content: space-between;
}
.onepaynumberInput:focus {
    box-shadow: 0px 0px 0px black !important;
}
.onepaynumberInput {
    border: 1px solid black !important;
    border-radius: 26px !important;
    margin: 10px 0px !important;
}
.heeeeee {
    width: 100%;
    height: 45px;
    font-size: 16px;
    color: #4a4a4a;
    text-align: center;
    padding-top: 8px;
    font-weight: 700;
}
</style>
