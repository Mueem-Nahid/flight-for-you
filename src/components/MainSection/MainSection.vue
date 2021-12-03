<template>
  <div>
    <div class="m-2 p-3">
      <div class="row">
        <div class="col-md-7 p=3">
          <h5>Flights</h5>
          <div>
            <div class="card-group">
              <div
                class="card btn"
                data-bs-toggle="modal"
                data-bs-target="#exampleModal"
              >
                <div class="card-body">
                  <h5 class="card-title">Leaving from</h5>
                  <h4 class="card-text">DAC</h4>
                  <h5 class="card-text">{{ leavingFrom }}</h5>
                </div>
              </div>
              <div
                class="card btn"
                data-bs-toggle="modal"
                data-bs-target="#exampleModal"
              >
                <div class="card-body">
                  <h5 class="card-title">Going to</h5>
                  <h4 class="card-text">DAC</h4>
                  <h5 class="card-text">{{ goingTo }}</h5>
                  <p class="card-text"></p>
                </div>
              </div>
              <div class="card">
                <div class="card-body">
                  <h5 class="card-title">Departing on</h5>
                  <input type="date" v-model="departingOn" />
                  <h5 class="card-title">Returning on</h5>
                  <input type="date" v-model="returningOn" />
                </div>
              </div>
              <div class="card btn btn-light" @click="search">
                <div class="card-body">
                  <h5 class="card-title">Search Flight</h5>
                  <p class="card-text"></p>
                </div>
              </div>
            </div>
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

    <!-- flights -->
    <!-- <div v-for="item in all" :key="item">
      <h3>
        destination code:
        {{ all.response.flights[item].flight[0].destinationName.code }}
      </h3>
    </div> -->
    <table class="table">
      <thead>
        <tr>
          <th scope="col">Destination code</th>
          <th scope="col">origin Iata Code</th>
          <th scope="col">destinationTime</th>
          <th scope="col">originTime</th>
          <th scope="col">duration</th>
          <th scope="col">price</th>
          <th scope="col">airlineCode</th>
          <th scope="col">flightNumber</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>{{ destinationIataCode }}</td>
          <td>{{ originIataCode }}</td>
          <td>{{ destinationTime }}</td>
          <td>{{ originTime }}</td>
          <td>{{ duration }}</td>
          <td>{{ price }}</td>
          <td>{{ airlineCode }}</td>
          <td>{{ flightNumber }}</td>
        </tr>
      </tbody>
    </table>

    <!-- Modal -->
    <div
      class="modal fade"
      id="exampleModal"
      tabindex="-1"
      aria-labelledby="exampleModalLabel"
      aria-hidden="true"
    >
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="exampleModalLabel">
              Select a departure city
            </h5>
            <button
              type="button"
              class="btn-close"
              data-bs-dismiss="modal"
              aria-label="Close"
            ></button>
          </div>
          <div class="modal-body">
            <div class="mb-2">
              <label for="leavingFrom" class="form-label">Leaving from</label>
              <input
                type="text"
                class="form-control"
                id="leavingFrom"
                aria-describedby="emailHelp"
                v-model="leavingFrom"
              />
            </div>
            <div class="">
              <label for="goinTo" class="form-label">Going to</label>
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
              Close
            </button>
            <button type="button" class="btn btn-primary">Save changes</button>
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
      destinationIataCode: "",
      originIataCode: "",
      destinationTime: "",
      originTime: "",
      duration: "",
      price: "",
      airlineCode: "",
      flightNumber: "",
    };
  },

  methods: {
    search() {
      //var maindata;
      // var destinationIataCode;
      // var originIataCode;
      // var destinationTime;
      // var originTime;
      // var duration;
      // var price;
      // var airlineCode;
      // var flightNumber;

      console.log(
        this.leavingFrom,
        this.goingTo,
        this.departingOn,
        this.returningOn
      );
      var url =
        "https://api.sharetrip.net/api/v1/flight/search?tripType=Return&adult=1&child=0&infant=0&class=Economy&origin=" +
        this.leavingFrom +
        "&destination=" +
        this.goingTo +
        "&depart=" +
        this.departingOn +
        "&depart=" +
        this.returningOn;

      console.log(url);

      fetch(url)
        .then((res) => res.json())
        .then((data) => {
          console.log(data);
          this.destinationIataCode =
            data.response.flights[0].flight[0].destinationName.code;
          this.originIataCode =
            data.response.flights[0].flight[0].originName.code;
          (this.destinationTime =
            data.response.flights[0].flight[0].departureDateTime.time),
            (this.originTime =
              data.response.flights[0].flight[0].arrivalDateTime.time);
          this.duration = data.response.flights[0].flight[0].duration;
          this.price = data.response.flights[0].price;
          this.airlineCode =
            data.response.flights[0].segments[0].segment[1].airlines.code;
          this.flightNumber =
            data.response.flights[0].segments[0].segment[1].flightNumber;
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
