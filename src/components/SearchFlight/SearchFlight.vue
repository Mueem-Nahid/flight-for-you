<template>
    <div>
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
    </div>
</template>