<template>
  <section class="filters">
    <h2>Filters</h2>
    <div class="filter-container">
      <button class="corner-dots">By Algorithm</button>
    </div>
    <div class="filter-container active">
      <button class="corner-dots">By Coin</button>
      <ul class="coin-list">
        <li>
          <button class="corner-dots">
            <img src="/assets/imgs/base-icons/btc.png" alt="" />
            <span>Btc</span>
          </button>
        </li>
        <li>
          <button class="corner-dots">
            <img src="/assets/imgs/base-icons/ppc.png" alt="" />
            <span>Ppc</span>
          </button>
        </li>
        <li>
          <button class="corner-dots">
            <img src="/assets/imgs/base-icons/etp.png" alt="" />
            <span>Etp</span>
          </button>
        </li>
        <li>
          <button class="corner-dots">
            <img src="/assets/imgs/base-icons/btc.png" alt="" />
            <span>Btc</span>
          </button>
        </li>
        <li>
          <button class="corner-dots">
            <img src="/assets/imgs/base-icons/ppc.png" alt="" />
            <span>Ppc</span>
          </button>
        </li>
        <li>
          <button class="corner-dots">
            <img src="/assets/imgs/base-icons/etp.png" alt="" />
            <span>Etp</span>
          </button>
        </li>
      </ul>
    </div>
    <div class="filter-container">
      <button class="corner-dots">By Equipment</button>
    </div>
    <div class="filter-container">
      <button class="corner-dots">By Manufacturer</button>
    </div>
    <div class="input-container corner-dots">
      <input type="number" placeholder="Minimum price" />
    </div>
    <div class="input-container corner-dots">
      <input type="number" placeholder="Maximum price" />
    </div>
    <button class="corner-dots">Search</button>
  </section>
</template>
<script>
export default {
  name: "Filters",
  mounted() {
    const getAllContainers = document.querySelectorAll(".filter-container");

    getAllContainers.forEach(container => {
      const button = container.querySelector("button");
      button.addEventListener("click", () =>
        container.classList.toggle("active")
      );
    });
  }
};
</script>
