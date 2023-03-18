<template>
    <div>






  <form @submit.stop.prevent="onSubmit">


    <header>


      <div class="heeeeee" style="background: #419EFF; color: #fff;">
   <p>পেমেন্ট তথ্য</p> </div>


</header>

    <div class="text-center mt-4">
    <img src="https://checkout-bdt.onepay.news/static/img/pixlogo.2432dd36.png" alt="" style="width: 75px;">
    <p style="font-size: 16px;font-weight: 600;">ONE PAY</p>
</div>


<div class="mx-3">
  <div class="mx-3 text-end"><a href="javascript:void(0)" @click="$router.go(-1)" class="text-decoration-none text-warning-emphasis" style="font-size: 12px;color: orange;">একাউন্ট সুইচ করতে ক্লিক করুন</a></div>

</div>
<div class="border border-top-0 mb-4 mx-3 rounded">
  <p class="bg-primary text-white headFont paddinglr20 paddingtb10" v-if="rowss.name=='Bkash'"> স্টেপ ১. বিকাশ ইনফর্মেশন </p>
  <p class="bg-primary text-white headFont paddinglr20 paddingtb10" v-else-if="rowss.name=='Nagad'"> স্টেপ ১. নগদ ইনফর্মেশন </p>
  <p class="bg-primary text-white headFont paddinglr20 paddingtb10" v-else-if="rowss.name=='Rocket'"> স্টেপ ১. রকেট ইনফর্মেশন </p>
  <div class="d-flex justify-content-between mx-4" style="border-bottom: 1px dotted black;">

    <p class="text-body-secondary mb-1 textFontSize" style="color: #979797;padding: 10px 0px;" v-if="rowss.name=='Bkash'">বিকাশ একাউন্ট</p>
    <p class="text-body-secondary mb-1 textFontSize" style="color: #979797;padding: 10px 0px;" v-else-if="rowss.name=='Nagad'">নগদ একাউন্ট</p>
    <p class="text-body-secondary mb-1 textFontSize" style="color: #979797;padding: 10px 0px;" v-else-if="rowss.name=='Rocket'">রকেট একাউন্ট</p>
    <p class="mb-1" style="font-size:12px"> {{ paymentNumber }}</p>
  </div>

  <div class="d-flex justify-content-between mx-4 fw-bold mt-2">
    <p class="fs-6  textFontSize" style="font-size: 14px !important;padding: 8px 0px;"> পরিমাণ</p>
    <p class="fs-6 text-danger"  style="padding: 8px 0px;"> {{ form.amount }} TK</p>
  </div>

</div>
<!-- <hr class="mx-4"> -->

<div class="border border-top-0 mb-4 mx-3 rounded">
  <p class="bg-primary text-white mb-1 headFont paddinglr20 paddingtb10" v-if="rowss.name=='Bkash'"> ধাপ 2. বিকাশ ট্রান্সফারের মাধ্যমে আপনি যে পরিমাণ রিচার্জ করতে চান তা আমাদের কাছে ট্রান্সফার করুন। </p>
  <p class="bg-primary text-white mb-1 headFont paddinglr20 paddingtb10" v-else-if="rowss.name=='Nagad'"> ধাপ 2. নগদ ট্রান্সফারের মাধ্যমে আপনি যে পরিমাণ রিচার্জ করতে চান তা আমাদের কাছে ট্রান্সফার করুন। </p>
  <p class="bg-primary text-white mb-1 headFont paddinglr20 paddingtb10" v-else-if="rowss.name=='Rocket'"> ধাপ 2. রকেট ট্রান্সফারের মাধ্যমে আপনি যে পরিমাণ রিচার্জ করতে চান তা আমাদের কাছে ট্রান্সফার করুন। </p>
  <p class="ms-3 my-1">
    <span class="textFontSize acl979797" style="color: #979797;padding: 10px 0px;"><span color="red">*</span> অর্থপ্রদানের পরে অনুগ্রহ করে আপনার [লেনদেন আইডি] অনুলিপি<br>করুন</span>
  </p>
</div>
<div class="border border-top-0 mb-4 mx-3 rounded">
  <p class="bg-primary text-white mb-1 headFont paddinglr20 paddingtb10">
    ধাপ 3। রিচার্জ সম্পূর্ণ করতে অনুগ্রহ করে লেনদেন আইডি লিখুন
  </p>
  <div class="text-center">

    <img v-if="rowss.name=='Bkash'" :src="$asseturl+'Recharge/bkash_tnxid_2.png'" alt="" class="w-50">
    <img v-else-if="rowss.name=='Nagad'" :src="$asseturl+'Recharge/nagad_tnxid_1.jpg'" alt="" class="w-50">
    <img  v-else-if="rowss.name=='Rocket'" src="" alt="" class="w-50">

  </div>
  <div class="">

    <input class="form-control mb-3 onepaynumberInput" v-if="rowss.name=='Bkash'" v-model="form.trx" type="text" placeholder="১০ সংখ্যার লেনদেন আইডি">
    <input class="form-control mb-3 onepaynumberInput" v-if="rowss.name=='Nagad'" v-model="form.trx" type="text" placeholder="৮ সংখ্যার লেনদেন আইডি">
    <input class="form-control mb-3 onepaynumberInput" v-if="rowss.name=='Rocket'" v-model="form.trx" type="text" placeholder="১০ সংখ্যার লেনদেন আইডি">
  </div>

</div>

<div data-v-464536f2="" style="height: 150px;"></div>

<div data-v-464536f2="" class="fifbutton flex_row_between afz14">
    <button type="button" @click="onCancel" data-v-464536f2="" style="border: 0 !important;background: transparent;" class="flex1 flex_row_center">আদেশ বাতিল</button>
    <button type="button" @click="onSubmit" data-v-464536f2="" style="border: 0 !important;" class="flexauto onbut flex_row_center">পেমেন্ট নিশ্চিত করুন</button>
</div>



<!--
<div class="mb-5 mx-3">
  <button type="button" class="btn btn-secondary btn-sm px-3 py-2 rounded-4" style="    padding: 7px 8px !important;   margin-top: 10px;" @click="onCancel">অর্ডার বাতিল করুন</button>
<button type="button" class=" btn btn-primary btn-sm px-3 py-2 rounded-4" style="     padding: 7px 8px !important;   margin-top: 10px;" @click="onSubmit">অর্ডার নিশ্চিত করুন</button>
</div> -->



</form>






<Message :Isactive="Messageactive" :Message="Message" />




    </div>
</template>

<script>
export default {
    data(){
        return {

            Messageactive:false,
            Message:'',
              rowss: {},
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
            this.rowss = res.data;
            if(this.rowss.name=='Bkash'){
                const random = Math.floor(Math.random() * this.bkash.length);
                this.paymentNumber = this.bkash[random];
            }else if(this.rowss.name=='Nagad'){
                const random = Math.floor(Math.random() * this.nagad.length);
                this.paymentNumber = this.nagad[random];
            }else if(this.rowss.name=='Rocket'){
                const random = Math.floor(Math.random() * this.rocket.length);
                this.paymentNumber = this.rocket[random];
            }

        },



        async onSubmit() {

            if(!this.form.trx){

                this.notifiyGlobal('Please enter valid trxn id');
            }else{




            this.con = true
                var id = localStorage.getItem('userid');
                this.form['user_id'] = id;
                var res = await this.callApi('post', `/api/admin/deposit`, this.form);
                this.$router.push({ name: 'rechargesuccess' });
            }
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

<style scoped>

.textFontSize{
    font-size: 10px !important;
}
.headFont {
    font-size: 14px !important;
    font-weight: 700;
}

.li {
    display: flex;
    justify-content: space-between;
}
.onepaynumberInput:focus {
    box-shadow: 0px 0px 0px black !important;
}
.onepaynumberInput {
    border: 1px solid #00000042 !important;
    border-radius: 11px !important;
    margin: 10px auto !important;
    width: 98%;
    font-size: 12px;
    padding: 8px 10px;
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


.bg-primary {
    background-color: #419EFE !important;
}

.paddinglr20 {
    padding-left: 10px;
    padding-right: 10px;
}
.paddingtb10 {
    padding-top: 7px;
    padding-bottom: 7px;
}


.fifbutton {
    position: fixed;
    bottom: 80px;
    width: 341px;
    height: 52px;
    border-radius: 26px;
    box-shadow: 0 3px 6px rgba(183,197,255,.38);
    left: 17px;
    z-index: 99;
    background: #fff;
}
.fifbutton .flex1 {
    width: 125px;
    min-width: 125px!important;
    color: #abbcff;
}
.fifbutton .onbut {
    background: #5370e5;
    opacity: 1;
    height: 52px;
    border-radius: 0 26px 26px 0;
    color: #fff;
    width: 62%;
}


</style>
