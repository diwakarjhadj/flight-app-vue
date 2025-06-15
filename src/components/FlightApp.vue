<template>
    <div class="flight-app">
        <div class="flight-heading">To Book Your Flight with GB International</div>
      <div class="dropdowns">
        <label for="source">
          Source <span class="required">*</span>:
        </label>
        <select v-model="source">
          <option value="" disabled>Select Source</option>
          <option v-for="(city, index) in cities" :key="index" :value="city">
            {{ city }}
          </option>
        </select>
  
        <label for="destination">
          Destination <span class="required">*</span>:
        </label>
        <select v-model="destination">
          <option value="" disabled>Select Destination</option>
          <option v-for="(city, index) in filteredCities" :key="index" :value="city">
            {{ city }}
          </option>
        </select>
  
        <button 
          :disabled="!canSearch" 
          @click="searchFlights" 
          class="search-button"
        >
          Search Flights
        </button>
      </div>

      <div v-if="!showResults && (!source || !destination)">
        <p class="message">Please select both Source and Destination to view available flights.</p>
    </div>
  
      <div v-if="showResults">
        <div v-if="filteredFlights.length" class="flights">
          <h2>Available Flights</h2>
          <div v-for="flight in filteredFlights" :key="flight.id" class="flight-card">
            <h3>{{ flight.company }}</h3>
            <p><strong>Departure:</strong> {{ formatDate(flight.segment[0].departureTime) }}</p>
            <p><strong>Arrival:</strong> {{ formatDate(flight.segment[0].arrivalTime) }}</p>
            <p><strong>Duration:</strong> {{ flight.duration }} minutes</p>
          </div>
        </div>
        <div v-else>
          <p>No flights available for the selected source and destination.</p>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        cities: ["Sao Paulo", "New York", "London", "Germany", "Toronto", "Miami"],
        source: "",
        destination: "",
        flights: [
          {
            id: "fc704c16fd79",
            company: "US Airlines",
            duration: 590,
            segment: [
              {
                departureTime: "2023-10-10T21:30-03:00",
                arrivalTime: "2023-10-11T06:20-04:00",
                origin: "Sao Paulo",
                destination: "New York",
              },
            ],
          },
          {
            id: "fc704c16fd75",
            company: "UK Airlines",
            duration: 590,
            segment: [
              {
                departureTime: "2023-10-10T21:30-06:00",
                arrivalTime: "2023-10-11T06:20-11:00",
                origin: "London",
                destination: "New York",
              },
            ],
          },
        ],
        showResults: false,
      };
    },
    computed: {
      filteredCities() {
        return this.cities.filter((city) => city !== this.source);
      },
      filteredFlights() {
        return this.flights.filter(
          (flight) =>
            flight.segment[0].origin === this.source &&
            flight.segment[0].destination === this.destination
        );
      },
      canSearch() {
        return this.source && this.destination;
      },
    },
    methods: {
      searchFlights() {
        if (!this.source || !this.destination) {
          alert("Please select both source and destination.");
          this.showResults = false;
          return;
        }
  
        if (this.source === this.destination) {
          alert("Source and destination cannot be the same!");
          this.showResults = false;
          return;
        }
  
        // Show results when search button is clicked
        this.showResults = true;
      },
      formatDate(dateTime) {
        return new Date(dateTime).toLocaleString();
      },
    },
  };
  </script>
  
  <style>
  .flight-app {
    font-family: Arial, sans-serif;
    padding: 20px;
  }
  
  .dropdowns {
    margin-bottom: 20px;
  }
  
  label {
    display: block;
    margin-bottom: 5px;
    font-weight: bold;
  }
  
  .required {
    color: red;
    font-weight: bold;
  }
  
  select {
    width: 100%;
    padding: 10px;
    margin-bottom: 10px;
    border-radius: 4px;
    border: 1px solid #ccc;
  }
  
  .search-button {
    display: block;
    width: 100%;
    padding: 10px;
    background-color: #0e1464;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  .search-button:disabled {
    background-color: #6a6b80;
    cursor: not-allowed;
  }
  
  .search-button:hover:enabled {
    background-color: #08103d;
  }
  
  .flights {
    margin-top: 20px;
  }
  
  .flight-card {
    padding: 15px;
    border: 1px solid #ccc;
    margin-bottom: 10px;
    border-radius: 4px;
    background-color: #08103d;
    color: #fff;
  }
  .flight-card:hover {
  transform: translateY(-1px);
  box-shadow: 0 8px 12px rgba(0, 0, 0, 0.2);
}
  
  h2 {
    margin-top: 0;
  }
  
  p {
    margin: 5px 0;
  }

  .message {
    text-align: center;
    color: #333;
    font-size: 1rem;
    margin: 20px 0;
}
.flight-heading{
    font-weight: 600;
    text-align: center;
    margin: 0px 0px 10px 0px;
}
  </style>
  