<template>
  <div class="divided-height">
    <div>
      <p>{{ cardNumbers }}</p>
      <p>{{ name }}</p>
      <p>{{ month }}</p>
      <p>{{ year }}</p>
      <p>{{ cvv }}</p>
    </div>
    <div class="form">
      <form action>
        <div>
          <label>Card number</label>
          <input class="full-width" type="text" v-model="number" />
        </div>
        <div>
          <label>Card name</label>
          <input class="full-width" type="text" v-model="name" />
        </div>

        <div>
          <div class="flex-input">
            <label>Expiration date</label>
            <label>CVV</label>
          </div>
          <div class="flex-input">
            <select v-model="month">
              <option selected disabled value="">Month</option>
              <option v-for="i in 12" value="i" :key="i">{{ i | addZero }}</option>
            </select>
            <select v-model="year">
              <option selected disabled value="">Year</option>
              <option value=""></option>
            </select>
            <input type="text" v-model="cvv" />
          </div>
        </div>
        <div>
          <input class="full-width" type="submit" value="submit" />
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data: function () {
    return {
      number: null,
      name: null,
      month: null,
      year: null,
      cvv: null
    }
  },
  computed: {
    currentYear: function () {
      return new Date().getFullYear()
    },
    cardNumbers: function () {
      let returnedNumbers = ''
      if (this.number !== null) {
        const arrayNumbers = this.number.split('')
        for (let i = 0; i < 4; i++) {
          returnedNumbers += arrayNumbers[i]
        }
        returnedNumbers += ' '
        for (let i = 4; i < 8; i++) {
          returnedNumbers += arrayNumbers[i]
        }
        returnedNumbers += ' '
        for (let i = 8; i < 12; i++) {
          returnedNumbers += arrayNumbers[i]
        }
        returnedNumbers += ' '
        for (let i = 12; i < 16; i++) {
          returnedNumbers += arrayNumbers[i]
        }
      } else {
        returnedNumbers = ''
      }

      return returnedNumbers
    }
  },
  filters: {
    addZero: function (value) {
      if (value < 10) return '0' + value
      return value
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
form {
  max-width: 100%;
}
.divided-height {
  height: 50%;
}
.flex-input {
  display: flex;
  justify-content: space-between;
}
.form {
  width: 50%;
  margin: 0 auto;
  padding: 20px;
  background-color: white;
  border-radius: 5px;
  box-shadow: 5px 10px 15px 2px grey;
}
.full-width {
  width: 100%;
}
</style>
