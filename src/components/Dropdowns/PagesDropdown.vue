<template>
  <div>
    <a
      class="
        lg:text-white
        lg:hover:text-blueGray-200
        text-blueGray-700
        px-3
        py-4
        lg:py-2
        flex
        items-center
        text-xs
        uppercase
        font-bold
      "
      href="#pablo"
      ref="btnDropdownRef"
      v-on:click="toggleDropdown($event)"
    >
      User Pages
    </a>
    <div
      ref="popoverDropdownRef"
      class="bg-white text-base z-50 float-left py-2 list-none text-left rounded shadow-lg min-w-48"
      v-bind:class="{
        hidden: !dropdownPopoverShow,
        block: dropdownPopoverShow,
      }"
    >
      <span
        class="
          text-sm
          pt-2
          pb-0
          px-4
          font-bold
          block
          w-full
          whitespace-nowrap
          bg-transparent
          text-blueGray-400
        "
      >
        Main
      </span>
      <router-link
        to="/auth/login"
        class="
          text-sm
          py-2
          px-4
          font-normal
          block
          w-full
          whitespace-nowrap
          bg-transparent
          text-blueGray-700
        "
      >
        Login
      </router-link>
      <router-link
        to="/admin/dashboard"
        class="
          text-sm
          py-2
          px-4
          font-normal
          block
          w-full
          whitespace-nowrap
          bg-transparent
          text-blueGray-700
        "
      >
        Dashboard
      </router-link>
      <router-link
        to="/admin/settings"
        class="
          text-sm
          py-2
          px-4
          font-normal
          block
          w-full
          whitespace-nowrap
          bg-transparent
          text-blueGray-700
        "
      >
        Profile
      </router-link>
      <router-link
        to="/admin/tables"
        class="
          text-sm
          py-2
          px-4
          font-normal
          block
          w-full
          whitespace-nowrap
          bg-transparent
          text-blueGray-700
        "
      >
        Transactions
      </router-link>
      <router-link
        to="/admin/maps"
        class="
          text-sm
          py-2
          px-4
          font-normal
          block
          w-full
          whitespace-nowrap
          bg-transparent
          text-blueGray-700
        "
      >
        Investment Packages
      </router-link>
    </div>
  </div>
</template>
<script>
import { createPopper } from "@popperjs/core";

export default {
  data() {
    return {
      dropdownPopoverShow: false,
    };
  },
  methods: {
    toggleDropdown(event) {
      event.preventDefault();
      if (this.dropdownPopoverShow) {
        this.dropdownPopoverShow = false;
      } else {
        this.dropdownPopoverShow = true;
        createPopper(this.$refs.btnDropdownRef, this.$refs.popoverDropdownRef, {
          placement: "bottom-start",
        });
      }
    },
  },
};
</script>
