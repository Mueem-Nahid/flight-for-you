<template>
  <div>
    <div class="px-5 mt-4">
      <div class="row">
        <div class="col-md-7 border">
          <h5 class="py-3 myColor fw-bold"><span class="underline">Flights</span></h5>
          <p> <span class="me-4"><a class="myAlert" href="#">Redeem flights</a></span>  <span><a class="myAlert" href="#">Multi-city / Stopover</a></span></p>
          <div>
            <div class="card-group">
              <div
                class="card  btn border-start-0 border-top-0 border border-3"
                data-bs-toggle="modal"
                data-bs-target="#exampleModal"
              >
                <div class="card-body row row-cols-1">
                  <h5 class="card-title text-muted mt-2">Leaving from</h5>
                  <h4 class="card-text fw-bold">DAC</h4>
                  <h5 class="card-text">{{ leavingFrom }}</h5>
                </div>
              </div>
              <div
                class="card btn border-start-0 border-top-0 border border-3"
                data-bs-toggle="modal"
                data-bs-target="#exampleModal"
              >
                <div class="card-body row row-cols-1">
                  <h5 class="card-title text-muted mt-2">Going to</h5>
                  <h4 class="card-text fw-bold">DAC</h4>
                  <h5 class="card-text">{{ goingTo }}</h5>
                </div>
              </div>
              <div class="card border-start-0 border-top-0 border border-3" data-bs-toggle="modal" data-bs-target="#exampleModal2">
                <div class="card-body text-center btn">
                  <div class="d-flex flex-column">
                   <div> 
                     <h6 class="card-title text-muted">Departing on</h6>
                      <p class="fw-bold"> {{departingOn}}</p>
                    </div>
                  <!-- <input type="date" v-model="departingOn" /> -->
                  <hr>
                  <div>
                    <h6 class="card-title text-muted">Returning on</h6>
                    <p class="fw-bold"> {{returningOn}}</p>
                  </div>
                  <!-- <input type="date" v-model="returningOn" /> -->
                  </div>
                </div>
              </div>
              <div class="card btn srchBtn" @click="search">
                <div class="card-body row row-cols-1" data-bs-toggle="modal" data-bs-target="#exampleModal3">
                  <i class="fas fa-plane fa-3x p-2 text-light"></i>
                  <h5 class="card-title fw-bold text-light">Search Flight</h5>
                </div>
              </div>
            </div>
          </div>
          <div class="mt-3">
            <p class="border py-2"> <i class="fas fa-bell px-2 text-warning"></i> <a href="#" class="myAlert"> Check the latest travel restrictions issued by United Kingdom </a></p>
          </div>
        </div>
        <div class="col-md-5">
          <img
            class="img-fluid"
            src="../../assets/images/main-section-image.jpg"
            alt=""
          />
        </div>
      </div>
    </div>

    <!-- Modal for city-->
    <div
      class="modal fade"
      id="exampleModal"
      tabindex="-1"
      aria-labelledby="exampleModalLabel"
      aria-hidden="true"
    >
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-body">
            <div class="mb-2">
              <label for="leavingFrom" class="form-label fw-bold">Leaving from</label>
              <input
                type="text"
                class="form-control"
                id="leavingFrom"
                aria-describedby="emailHelp"
                v-model="leavingFrom"
              />
            </div>
            <div class="">
              <label for="goinTo" class="form-label fw-bold">Going to</label>
              <input
                type="text"
                class="form-control"
                id="goinTo"
                aria-describedby="emailHelp"
                v-model="goingTo"
              />
            </div>

            <!-- <div v-if="suggestions">
              <ul>
                <li v-for="suggestion in suggestions" :key="suggestion">
                  {{ suggestion }}
                </li>
              </ul>
            </div> -->
          </div>
          <div class="modal-footer">
            <button
              type="button"
              class="btn btn-secondary"
              data-bs-dismiss="modal"
            >
              Done
            </button>
            <!-- <button type="button" class="btn btn-primary">Save changes</button> -->
          </div>
        </div>
      </div>
    </div>

    <!-- Modal for date -->
    <div
      class="modal fade"
      id="exampleModal2"
      tabindex="-1"
      aria-labelledby="exampleModalLabel2"
      aria-hidden="true"
    >
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-body">
            <div class="mb-2">
              <label for="departingOn" class="form-label fw-bold">Departing on</label>
              <input
                type="date"
                class="form-control"
                id="departingOn"
                aria-describedby="emailHelp"
                v-model="departingOn"
              />
            </div>
            <div class="">
              <label for="returningOn" class="form-label fw-bold">Returning on</label>
              <input
                type="date"
                class="form-control"
                id="returningOn"
                aria-describedby="emailHelp"
                v-model="returningOn"
              />
            </div>
          </div>
          <div class="modal-footer">
            <button
              type="button"
              class="btn btn-secondary"
              data-bs-dismiss="modal"
            >
              Done
            </button>
          </div>
        </div>
      </div>
    </div>

    <!-- Modal for search results -->
    <div
      class="modal fade"
      id="exampleModal3"
      tabindex="-1"
      aria-labelledby="exampleModalLabel3"
      aria-hidden="true"
    >
      <div class="modal-dialog modal-fullscreen">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="exampleModalLabel">Available Flights</h5>
            <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
          </div>
          <div class="modal-body">
            <!-- table -->
            <table class="table" v-if="flights.length">
              <thead>
                <tr>
                  <th scope="col">Airlines</th>
                  <th scope="col">Arrival Date</th>
                  <th scope="col">Arrival Time</th>
                  <th scope="col">Departure Date</th>
                  <th scope="col">Departure Time</th>
                  <th scope="col">Destination Name</th>
                  <th scope="col">Duration</th>
                  <th scope="col">Origin Name</th>
                  <!-- <th scope="col">Price</th>
                  <th scope="col">Currency</th>
                  <th scope="col">Deal</th> -->
                </tr>
              </thead>
              <tbody  v-for="flight in flights" :key="flight">
                <tr>
                  <td>{{ flight.airlines.full }}</td>
                  <td>{{ flight.arrivalDateTime.date }}</td>
                  <td>{{ flight.arrivalDateTime.time }}</td>
                  <td>{{ flight.departureDateTime.date }}</td>
                  <td>{{ flight.departureDateTime.time }}</td>
                  <td>{{ flight.destinationName.city }}</td>
                  <td>{{ flight.duration }}</td>
                  <td>{{ flight.originName.city }}</td>
                  <!-- <td>{{ price }}</td>
                  <td>{{ flight.currency }}</td>
                  <td>{{ flight.deal }}</td> -->
                </tr>
              </tbody>
            </table>
            <div v-else class="spinner-border" role="status">
              <span class="visually-hidden">Loading...</span>
            </div>
            <!-- table end -->
          </div>
          <div class="modal-footer">
            <button
              type="button"
              class="btn btn-secondary"
              data-bs-dismiss="modal"
            >
              Done
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      leavingFrom: "",
      goingTo: "",
      departingOn: "",
      returningOn: "",
      //price: [],
      // destinationIataCode: "",
      // originIataCode: "",
      // destinationTime: "",
      // originTime: "",
      // duration: "",
      // price: "",
      // airlineCode: "",
      // flightNumber: "",
      flights: []
    };
  },

  methods: {
    async search() {
      var url =
        "https://api.sharetrip.net/api/v1/flight/search?tripType=Return&adult=1&child=0&infant=0&class=Economy&origin=" +
        this.leavingFrom +
        "&destination=" +
        this.goingTo +
        "&depart=" +
        this.departingOn +
        "&depart=" +
        this.returningOn;

      await fetch(url)
        .then((res) => res.json())
        .then((data) => {
          // console.log(data);

         for(let i=0; i<data.response.flights.length; i++) {
            this.flights[i] = data.response.flights[i].flight[0];
            //this.price[i] = data.response.flights[i].price;
            console.log("Flight ", i, ": ", this.flights[i]);
          }
          // this.destinationIataCode =
            // data.response.flights[0].flight[0].destinationName.code;
          // this.originIataCode =
          //   data.response.flights[0].flight[0].originName.code;
          // (this.destinationTime =
          //   data.response.flights[0].flight[0].departureDateTime.time),
            // (this.originTime =
            //   data.response.flights[0].flight[0].arrivalDateTime.time);
          // this.duration = data.response.flights[0].flight[0].duration;
          // this.price = data.response.flights[0].price;
          // this.airlineCode =
          //   data.response.flights[0].segments[0].segment[1].airlines.code;
          // this.flightNumber =
            // data.response.flights[0].segments[0].segment[1].flightNumber;
        })
        .catch(() => {
          alert("Opps! There is no flight available. Try again!");
        });
    },
    /*autoSug() {
      let url =
        "https://api.sharetrip.net/api/v1/flight/search/airport?name=" +
        this.leavingFrom;
      console.log(url);
      fetch(url)
        .then((res) => res.json())
        .then((data) => {
          console.log(data.response[0]);
          this.suggestions = data.response[0].name;
        });
    },*/
  },
};
</script>

<style>
  .myColor {
    color: #4c4c4c;
  }
  .srchBtn {
    background: linear-gradient(315deg,#005d63 0,#202f42 99.93%);
  }
  .underline {
    text-decoration: none; 
    position: relative; 
  }
  .underline:after {
    position: absolute;
    content: '';
    height: 3px;
    bottom: -5px;
    margin: 0 auto;
    left: 0;
    width: 100%;
    background: #4c4c4c;
  }
</style>
