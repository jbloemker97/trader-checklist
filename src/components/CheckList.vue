<template>
    <div class="row mt-5">
        <div class="col-lg-8">
            <div class="card">
                <div class="card-body">
                    <h5 class="card-title">Trade CheckList</h5>
                    <ul class="list-group">
                        <li class="list-group-item">Two previous tests of level on 30min (or greater) chart</li>
                        <li class="list-group-item">At least one previous intraday rejection</li>
                        <li class="list-group-item">Not a higher high or lower low</li>
                        <li class="list-group-item" data-is-checked="false" @click="trade">Not entering opposite side of momentum</li>
                    </ul>
                </div>
            </div>
        </div>

        <div class="col-lg-4">
            <div class="card">
                <div class="card-body">
                    <h5 class="text-center">Can I Enter A Trade?</h5>
                    <img :src="imgUrl" class="rounded">
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'CheckList',
    data () {
        return {
            imgUrl: 'https://via.placeholder.com/150',
            isTrade: false,
        }
    },
    methods: {
        trade: function (event) {
            var dataCheck = event.target.getAttribute("data-is-checked");

            event.target.setAttribute("data-is-checked", !!dataCheck);

            console.log(dataCheck)
        }
    }
}
</script>

<style scoped>
    .line-through {
        text-decoration: line-through;
    }
</style>