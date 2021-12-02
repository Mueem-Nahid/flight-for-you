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
                  <h5 class="card-text">Dhaka</h5>
                </div>
              </div>
              <div class="card btn" data-bs-toggle="modal"
                data-bs-target="#exampleModal">
                <div class="card-body">
                  <h5 class="card-title">Going to</h5>
                  <h4 class="card-text">DAC</h4>
                  <h5 class="card-text">Dhaka</h5>
                  <p class="card-text"></p>
                </div>
              </div>
              <div class="card">
                <div class="card-body">
                  <h5 class="card-title">Departing on</h5>
                  <h5 class="card-title">Returning on</h5>
                </div>
              </div>
              <div class="card">
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
              />
            </div>
            <div class="">
              <label for="goinTo" class="form-label">Going to</label>
              <input
                type="text"
                class="form-control"
                id="goinTo"
                aria-describedby="emailHelp"
              />
            </div>
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
