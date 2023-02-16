<template>
  <div class="p-3">
    <p class="text-center fs-1 fw-bold mb-2">排版系統</p>
    <div class="input-group mb-2">
      <textarea
        class="form-control"
        aria-label="With textarea"
        v-model="methods"
      ></textarea>
      <button class="btn btn-success" type="button" @click="typeSetting">
        排版
      </button>
    </div>
    <div class="border border-2 rounded p-3" style="height: 80vh">
      <div id="result"></div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      methods: null,
      result: null,
    };
  },
  methods: {
    // 排版
    typeSetting() {
      let result = "";
      let blank = [];
      for (let i in this.methods) {
        if (this.methods[i] === "{") {
          blank.push("&emsp;&emsp;");
          result += `${this.methods[i]}<br>${blank.join("")}`;
        } else if (this.methods[i] === ",")
          result += `${this.methods[i]}<br>${blank.join("")}`;
        else if (this.methods[i] === "}") {
          blank.pop();
          result += `<br>${blank.join("")}${this.methods[i]}`;
        } else result += this.methods[i];
      }
      document.getElementById("result").innerHTML = result;
    },
  },
};
</script>
