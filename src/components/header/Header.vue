<template>
  <header :class="{ active: isHeaderMenuActive }">
    <nav class="base container">
      <ul>
        <li class="logo">
          <a href="/"> <LogoIcon /> </a>
        </li>
        <li class="lang">
          <button><EarthIcon />Eng</button>
        </li>
        <li class="menu">
          <button @click="setActiveHeaderMenu"><HamburgerIcon /></button>
        </li>
        <li class="account three-dots">
          <button><AccountIcon />My account<ArrowIcon /></button>
        </li>
        <li class="wallet three-dots">
          <button><WalletIcon /></button>
        </li>
        <li class="notifications three-dots">
          <button><NotificationIcon /></button>
          <Basket
            :isBasketActive="isBasketActive"
            :setActiveBasket="setActiveBasket"
            :basket="basket"
            :removeBasketList="removeBasketList"
          />
        </li>
        <li class="basket">
          <button @click="setActiveBasket">
            {{ setBasketSize }}<BasketIcon />
          </button>
        </li>
      </ul>
    </nav>
    <nav :class="{ show: isHeaderMenuActive }">
      <ul>
        <li class="cross">
          <button @click="setActiveHeaderMenu">
            <img src="/assets/imgs/base-icons/close.svg" alt="" />
          </button>
        </li>
        <li><a href="#">Home</a></li>
        <li><a href="#">Sell</a></li>
        <li><a href="#">Host</a></li>
        <li><a href="#">About us</a></li>
        <li><a href="#">Support</a></li>
      </ul>
      <span class="text-bg">menu</span>
    </nav>
  </header>
</template>

<script>
import Basket from "./Basket";

import LogoIcon from "../../assets/images/headerIcons/logo-icon.svg";
import EarthIcon from "../../assets/images/headerIcons/earth-icon.svg";
import HamburgerIcon from "../../assets/images/headerIcons/hamburger-icon.svg";
import AccountIcon from "../../assets/images/headerIcons/account-icon.svg";
import WalletIcon from "../../assets/images/headerIcons/wallet-icon.svg";
import NotificationIcon from "../../assets/images/headerIcons/notification-icon.svg";
import BasketIcon from "../../assets/images/headerIcons/basket-icon.svg";
import ArrowIcon from "../../assets/images/headerIcons/arrow-icon.svg";

export default {
  name: "Header",
  props: ["basket", "removeBasketList"],
  data() {
    return {
      isHeaderMenuActive: false,
      isBasketActive: false
    };
  },
  components: {
    Basket,
    LogoIcon,
    EarthIcon,
    HamburgerIcon,
    AccountIcon,
    WalletIcon,
    BasketIcon,
    NotificationIcon,
    ArrowIcon
  },
  methods: {
    setActiveHeaderMenu() {
      this.isHeaderMenuActive = !this.isHeaderMenuActive;
      document.body.classList.toggle("menu-active");
    },
    setActiveBasket() {
      this.isBasketActive = !this.isBasketActive;

    }
  },
  computed: {
    setBasketSize: function() {
      return this.basket.length;
    }
  }
};
</script>
