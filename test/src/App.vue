
<template>
    <main>
        <div class="selected__groups">
            <div class="selected__groups-user-thing">
                <div class="list__things-block"
                     v-for = "item in selected.userThings"
                     :key = "'user_things_' + item.id"
                     @click = "selectUserThings(item)"
                >
                    {{item.name}}
                </div>
            </div>
            <div
                class="selected__groups-other-thing"
                @click = "selectOtherThings(selected.other)"
            >{{nameOtherThing}}</div>
        </div>

        <div class="list__things">
            <div class="list__things-user">
                <div class="list__things-block"
                     v-for = "item in listUserThings"
                     :key = "'user_things_' + item.id"
                     @click = "selectUserThings(item)"
                >
                    {{item.name}}
                </div>

            </div>
            <div class="list__things-other">
                <div class="list__things-block"
                     v-for = "item in listThings"
                     :key = "'other_things_' + item.id"
                     @click = "selectOtherThings(item.id)"
                >
                    {{item.name}}
                </div>
            </div>
        </div>

    </main>
</template>

<script>
export default {
    data () {
        return {
            listThings: [
                {
                    "id": 11,
                    "name": "Jacket 1"
                },
                {
                    "id": 12,
                    "name": "Jacket 2"
                },
                {
                    "id": 13,
                    "name": "Jacket 3"
                },
                {
                    "id": 14,
                    "name": "Jacket 4"
                },
                {
                    "id": 15,
                    "name": "Hoodie 1"
                },
                {
                    "id": 16,
                    "name": "Hoodie 2"
                },
                {
                    "id": 17,
                    "name": "Hoodie 3"
                },
                {
                    "id": 18,
                    "name": "Hoodie 4"
                }
            ],
            listUserThings: [
                {
                    "id": 1,
                    "name": "Shoes 1"
                },
                {
                    "id": 2,
                    "name": "Shoes 2"
                },
                {
                    "id": 3,
                    "name": "Shoes 3"
                },
                {
                    "id": 4,
                    "name": "Shoes 4"
                },
                {
                    "id": 5,
                    "name": "T-shirt 1"
                },
                {
                    "id": 6,
                    "name": "T-shirt 2"
                },
                {
                    "id": 7,
                    "name": "T-shirt 3"
                },
                {
                    "id": 8,
                    "name": "T-shirt 4"
                }
            ],
            selected: {
                userThings: [],
                other: false,
            }

        }
    },
    computed: {
        nameOtherThing() {
            return this.listThings.find(item => item.id === this.selected.other)?.name || 'ничего не выбрано';
        }

    },
    methods: {
        selectOtherThings(id) {
            if (this.selected.other === id) this.selected.other = false;
            else this.selected.other = id;

        },
        selectUserThings(thing) {
            if(this.selected.userThings.find(item => item.id === thing.id)) {
                this.selected.userThings.splice(this.selected.userThings.findIndex(item => item.id === thing.id), 1)
            } else if(this.selected.userThings.length < 6){
                this.selected.userThings.push(thing);
            }

        },

    },

}
</script>

<style>
body {
    margin: 0;
}
#app {
    display: block;
    height: calc(100vh - 20px);
}
</style>

<style scoped>


main {
    display: flex;
    flex-direction: column;
    gap: 20px;

    margin: 20px;
    height: 100%;
}

.selected__groups,
.list__things {
    display: flex;
    gap: 20px;
    justify-content: space-between;
}
.list__things-user,
.selected__groups-user-thing,
.selected__groups-other-thing,
.list__things-other {
    border: 2px solid;
    padding: 20px;
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
    flex: 1;
}


.list__things-block {
    border: 2px solid;
    padding: 20px;
    width: 200px;
    height: 60px;
    cursor: pointer;
}
.list__things-block:hover {
    background: beige;
}

</style>
