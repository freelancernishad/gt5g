<template>
    <div>


    <main class="main-bg-absulate" style="background-image: url(/img/earnings.png);">

<div class=" bg-white mx-4 px-4 shadow-lg">
    <div class="d-flex gap-4 justify-content-between ms-0 py-1 w-50 pb-3">
        <div>
            <img :src="$asseturl+'img/my.png'" alt="">
        </div>
        <div>
            <p class="mb-0 py-2">{{ row.user.mobile }}</p>
            <p class="mb-0 py-2">{{ row.user.username }}</p>
        </div>
    </div>
    <div class="border-top d-flex justify-content-around lh-1 pt-4">
        <div class="text-center">
            <p class="fw-bold mb-0 pb-2 defaltColor">{{ parseFloat(row.user.balance).toFixed(2) }}</p>
            <p>Balance</p>
        </div>
        <div class="text-center">
            <p class="fw-bold mb-0 pb-2 defaltColor">{{ parseFloat(levelTeam.reacharge).toFixed(2) }}</p>
            <p>Promotion</p>
        </div>
        <div class="text-center">
            <p class="fw-bold mb-0 pb-2 defaltColor">{{ parseFloat(levelTeam.purchase).toFixed(2) }}</p>
            <p>Investment</p>
        </div>

    </div>


</div>
<div class="d-flex justify-content-around bg-white mx-4 my-3 shadow-lg py-4 ">

    <router-link :to="{name:'Recharge'}" class="recharge-flex defaltColor">
        <img :src="$asseturl+'img/11111.png'" alt="">
        <p class="mb-0">Recharge</p>
    </router-link>
    <router-link :to="{name:'withdraw'}" class="recharge-flex defaltColor">
        <img :src="$asseturl+'img/11111.png'" alt="">
        <p class="mb-0">Withdrawal</p>
    </router-link>
    <!-- <router-link :to="{name:'treasure'}" class="recharge-flex defaltColor">
        <img :src="$asseturl+'img/11111.png'" alt="">
        <p class="mb-0">Treasure</p>
    </router-link> -->
</div>

<div class="bg-white mx-4 my-3 py-4 shadow-lg">
    <router-link :to="{name:'banlance'}" class="mx-3 defaltColor">
        <img :src="$asseturl+'img/book.126a5a8e.png'" alt="">
        <p class="d-inline fw-bold mb-0 ms-1">Balance Record</p>
    </router-link>
</div>

<div class="bg-white mx-4 my-3 py-4 shadow-lg">
    <router-link :to="{name:'peraccpass'}"  class="mx-3 defaltColor">
        <img :src="$asseturl+'img/book.126a5a8e.png'" alt="">
        <p class="d-inline fw-bold mb-0 ms-1">personal</p>
    </router-link>

</div>
<div class="bg-white  mx-4 my-3 py-4 shadow-lg">
    <router-link :to="{name:'RechargeRecord'}"  class="mx-3 defaltColor">
        <img :src="$asseturl+'img/book.126a5a8e.png'" alt="">
        <p class="d-inline fw-bold mb-0 ms-1">Recharge Record</p>
    </router-link>

</div>
<div class="bg-white  mx-4 my-3 py-4 shadow-lg">
    <router-link :to="{name:'WithdrawalRecord'}"  class="mx-3 defaltColor">
        <img :src="$asseturl+'img/book.126a5a8e.png'" alt="">
        <p class="d-inline fw-bold mb-0 ms-1">Withdrawal Record</p>
    </router-link>

</div>
<div class="bg-white  mx-4 my-3 py-4 shadow-lg">
    <router-link :to="{name:'aboutus'}"  class="mx-3 defaltColor">
        <img :src="$asseturl+'img/book.126a5a8e.png'" alt="">
        <p class="d-inline fw-bold mb-0 ms-1">About Us</p>
    </router-link>

</div>
<div class="bg-white  mx-4 my-3 py-4 shadow-lg">
    <a :href="$asseturl+''"  class="mx-3 defaltColor">
        <img :src="$asseturl+'img/book.126a5a8e.png'" alt="">
        <p class="d-inline fw-bold mb-0 ms-1">Download APP</p>
    </a>

</div>



<div class="bg-white mx-4 my-3 py-4 shadow-lg mb-5">
    <router-link :to="{name:'logout'}"  class="mx-3 defaltColor">
        <img :src="$asseturl+'img/book.126a5a8e.png'" alt="">
        <p class="d-inline fw-bold mb-0 ms-1">Log Out</p>
    </router-link>

</div>



</main>

    </div>
</template>




<script>


export default {

    data(){
        return {
            levelTeam: {
                level1: {},
                level2: {},
                level3: {},
            },
        }
    },
    methods: {
        async getData(){
            var id = localStorage.getItem('userid');
            var res = await this.callApi('get', `/api/user/multi/refer?id=${id}`, []);
            this.levelTeam = res.data;
        },
    },
    mounted() {
        this.getData();
    },
}
</script>
