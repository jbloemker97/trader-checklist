<template>
    <div class="row mt-5">
        <div class="col-lg-8">
            <div class="card">
                <div class="card-body">
                    <h5 class="card-title">Trade CheckList</h5>
                    <ul class="list-group">
                        <li class="list-group-item checkListItem" @click="onClick">Two previous tests of level on 30min (or greater) chart</li>
                        <li class="list-group-item checkListItem" @click="onClick">At least one previous intraday rejection</li>
                        <li class="list-group-item checkListItem" @click="onClick">Not a higher high or lower low</li>
                        <li class="list-group-item checkListItem" @click="onClick">Not entering opposite side of momentum</li>
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
            doTrade: false,
        }
    },
    methods: {
        onClick: function (event) {
            event.target.classList.toggle('line-through');

            let checkListItems = document.querySelectorAll('.checkListItem');
            let changeState = true;

            checkListItems.forEach((item) => {
                if (!item.classList.contains('line-through')) {
                    changeState = false;
                }
            });

            this.doTrade = changeState;

        }
    }
}
</script>

<style scoped>
    .line-through {
        text-decoration: line-through;
    }

    li {
        cursor: pointer;
    }
</style>