<template>
  <div>
    <nav class="navbar navbar-expand-lg navbar-dark mybg">
      <div class="container-fluid px-5">
        <button
          class="navbar-toggler"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarTogglerDemo01"
          aria-controls="navbarTogglerDemo01"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarTogglerDemo01">
          <img class="pe-1" src="../../assets/logo.png" alt="">
          <a class="navbar-brand" href="#">Flight For You</a>
          <ul class="navbar-nav ms-auto mb-2 mb-lg-0">
            <li class="nav-item">
              <a class="nav-link" aria-current="page" href="#">Offers</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">Manage</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">Experience</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">Macro Polo Club</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">Login</a>
            </li>            
          </ul>
        </div>
      </div>
    </nav>
    
    <div class="px-5 pt-1 d-flex justify-content-between alert-secondary">
      <div>
        <p>
          <i class="fas fa-exclamation-triangle text-danger pe-1"></i>
          2 Latest updates.
        <a href="#" class="myAlert">View the latest COVID-19 travel restrictions, quarantine requirements and more</a>
      </p>
      </div>
      <div>
        <p> <a href="#"> View all </a> </p>
      </div>
    </div>

    <div class="my-4 px-5">
      <h4 class="text-muted">Ready for your next trip? Book with us now.</h4>
    </div>
  </div>
</template>

<style>
  .mybg {
    background: rgb(0, 93, 99);
  }
  .myAlert {
    text-decoration: none;
  }
</style>