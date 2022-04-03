<template>
  <div>
    <div class="container">
      <div class="items">
        <h1>Ticket Simulator</h1>
        <input type="text" placeholder="Name" />
        <input type="text" placeholder="PhoneNumber" />
        <input type="text" placeholder="LastName" />
        <input type="text" placeholder="Email" />
        <select @change="checkSelectBox">
          <option Value="Please Select">Please Select ...</option>
          <option Value="Iran">Iran</option>
          <option Value="Turkey">Turkey</option>
          <option Value="US">United States</option>
        </select>
        <div>
          <select>
            <option v-for="mainCity in mainCities" :key="mainCities[mainCity]">
              {{ mainCity }}
            </option>
          </select>
          <button @click="toggle">Book A Ticket</button>
        </div>
      </div>
    </div>
    <div class="modal">
      <h3 class="modal-content" v-show="show">Your Trip Has Been Booked</h3>
    </div>
  </div>
</template>

<script>
export default {
  name: "TicketSale",
  data() {
    return {
      countries: {
        Iran: ["Esfehan", "Shiraz", "Tehran"],
        Turkey: ["Istanbul", "Izmir", "Ankara"],
        US: ["Arizona", "LosAngels", "LasVegas", "New York"],
      },
      mainCities: [],
      show: false,
    };
  },
  methods: {
    checkSelectBox(event) {
      let countryName = event.target.value;
      this.mainCities = this.countries[countryName];
    },
    toggle() {
        this.show = true;
        setTimeout(() => {
          this.show = false;
        }, 2000);
    },
  },
};
</script>
<style scoped>
.container {
  display: flex;
  justify-content: center;
}
.items {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 20px;
  background-color: #fff;
  border: 1px solid black;
  box-shadow: 5px 5px 10px black;
}
button {
  display: block;
  background-color: green;
  color: white;
  width: 300px;
  margin-top: 20px;
  margin-bottom: 10px;
}
input {
  display: block;
  margin: 25px;
  width: 200px;
  transition: all 1s;
  border-top: none;
  border-right: none;
  border-left: none;
}
select {
  width: 300px;
  margin-top: 20px;
  border-top: none;
  border-right : none;
  border-left : none;
}
button:hover {
  background-color: darkgreen;
}
input:focus {
  width: 230px;
  outline: none;
}
.modal {
  display: flex;
  justify-content: center;
}
.modal-content{
  color : white;
  background-color : green;
  border : 2px dashed white;
  padding : 10px;
}
</style>
