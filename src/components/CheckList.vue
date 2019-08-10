<template>
    <div class="row mt-5">
        <div class="col-lg-8">
            <div class="card">
                <div class="card-header">
                    <h5 class="card-title text-center m-0">Trade CheckList</h5>
                </div>
                <div class="card-body">
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
                <div class="card-header">
                    <h5 class="card-title text-center m-0">Can I Enter A Trade?</h5>
                </div>
                <div class="card-body text-center">
                    <img :src="imgUrl" class="rounded">
                </div>
            </div>
        </div>
    </div>

    <!-- <div>Icons made by <a href="https://www.flaticon.com/authors/dave-gandy" title="Dave Gandy">Dave Gandy</a> from <a href="https://www.flaticon.com/"                 title="Flaticon">www.flaticon.com</a> is licensed by <a href="http://creativecommons.org/licenses/by/3.0/"                 title="Creative Commons BY 3.0" target="_blank">CC 3.0 BY</a></div> -->
</template>

<script>
export default {
    name: 'CheckList',
    data () {
        return {
            // imgUrl: 'https://via.placeholder.com/150',
            imgUrl: '/assets/frown.png',
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

            this.checkTrade();

        },
        checkTrade: function () {
            this.imgUrl = this.doTrade ? '/assets/happiness.png' : '/assets/frown.png';
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

    li:hover {
        background-color: #E1E1E1;
        opacity: 0.8;
    }

    img {
        margin-top: 25px;
        max-width: 60%;
    }

    .card-header {
        background-color: #006DB0;
        color: #fff;
    }
</style>