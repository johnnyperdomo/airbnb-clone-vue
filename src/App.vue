<template>
    <div id="app" class="main-content">
        <!-- navbar -->
        <nav class="navbar navbar-light border-bottom border-3 border-light">
            <div class="container">
                <a class="navbar-brand" href="#">
                    <img src="./assets/airbnb.png" alt="" height="30" />
                </a>
            </div>
        </nav>

        <!-- hero -->

        <section id="hero" class="d-flex justify-content-center align-items-center row">
            <div class="my-5 col-8">
                <!-- headline -->
                <h1 class="text-center text-white" style="font-size: 60px">
                    Discover New Adventures
                </h1>
                <!-- subheading -->
                <p class="text-center text-white lead" style="font-size: 30px">
                    Find the perfect vacation rental
                </p>

                <!-- search bar -->
                <div class="input-group col-6 shadow mt-5">
                    <input type="text" class="form-control" placeholder="Miami, FL" />
                    <button class="btn btn-primary btn-lg" type="button">Search</button>
                </div>
            </div>
        </section>

        <!-- listings -->

        <div class="container">
            <h1 class="d-flex justify-content-center mt-5">Explore Rentals in Miami, FL 🏝</h1>

            <div class="row mx-2">
                <div
                    v-for="(listing, idx) in listings"
                    v-bind:key="(listing, idx)"
                    class="col-6 col-md-4 col-lg-3"
                    style="border: 0"
                >
                    <div class="card mt-4" style="border: 0px">
                        <!-- image -->
                        <!-- v-bind:src="listing.image" -->
                        <img
                            class="card-img-top rounded shadow"
                            :src="require(`${listing.image}`)"
                        />

                        <!-- description -->
                        <p class="my-1">{{ listing.description }}</p>

                        <!-- price -->
                        <p class="small">
                            <b>{{ listing.price }}</b>
                            /night
                        </p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "app",

    data() {
        return {
            listings: [],
        };
    },
    methods: {
        buildInventoryObject() {
            for (let index = 0; index < 19; index++) {
                const imgSrc = `./assets/photo-${index + 1}.jpeg`;

                console.log(imgSrc);

                let inventoryItem = {
                    image: imgSrc,
                    description: "Full luxury home | 2-bed 3-bath",
                    price: "$65",
                };

                this.listings.push(inventoryItem);
            }
        },
    },

    mounted() {
        this.$nextTick(function () {
            this.buildInventoryObject();
            console.log(this.listings);
        });
    },
};
</script>

<style scoped>
#hero {
    /* background-image: url("./assets/background.jpeg"); */
    background: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)),
        url("./assets/background.jpeg");
    background-size: cover;
    height: 65vh;
}

.card-img-top {
    width: 100%;
    height: 12vw;
    object-fit: cover;
}

.card:hover {
    transform: scale(1.05);
    cursor: pointer;
}
</style>
