<template>
  <nav
    class="
      md:left-0
      md:block
      md:fixed
      md:top-0
      md:bottom-0
      md:overflow-y-auto
      md:flex-row md:flex-nowrap
      md:overflow-hidden
      shadow-xl
      bg-white
      flex flex-wrap
      items-center
      justify-between
      relative
      md:w-64
      z-10
      py-4
      px-6
    "
  >
    <div
      class="
        md:flex-col
        md:items-stretch
        md:min-h-full
        md:flex-nowrap
        px-0
        flex flex-wrap
        items-center
        justify-between
        w-full
        mx-auto
      "
    >
      <!-- Toggler -->
      <button
        class="
          cursor-pointer
          text-black
          opacity-50
          md:hidden
          px-3
          py-1
          text-xl
          leading-none
          bg-transparent
          rounded
          border border-solid border-transparent
        "
        type="button"
        v-on:click="toggleCollapseShow('bg-white m-2 py-3 px-6')"
      >
        <i class="fas fa-bars"></i>
      </button>
      <!-- Brand -->
      <router-link
        class="
          md:block
          text-left
          md:pb-2
          text-blueGray-600
          mr-0
          inline-block
          whitespace-nowrap
          text-sm
          uppercase
          font-bold
          p-4
          px-0
        "
        to="/"
      >
        Welcome: {{ this.username }}
      </router-link>
      <!-- User -->
      <ul class="md:hidden items-center flex flex-wrap list-none">
        <li class="inline-block relative">
          <notification-dropdown />
        </li>
        <li class="inline-block relative">
          <user-dropdown />
        </li>
      </ul>
      <!-- Collapse -->
      <div
        class="
          md:flex md:flex-col
          md:items-stretch
          md:opacity-100
          md:relative
          md:mt-4
          md:shadow-none
          shadow
          absolute
          top-0
          left-0
          right-0
          z-40
          overflow-y-auto overflow-x-hidden
          h-auto
          items-center
          flex-1
          rounded
        "
        v-bind:class="collapseShow"
      >
        <!-- Collapse header -->
        <div
          class="md:min-w-full md:hidden block pb-4 mb-4 border-b border-solid border-blueGray-200"
        >
          <div class="flex flex-wrap">
            <div class="w-6/12">
              <router-link
                class="
                  md:block
                  text-left
                  md:pb-2
                  text-blueGray-600
                  mr-0
                  inline-block
                  whitespace-nowrap
                  text-sm
                  uppercase
                  font-bold
                  p-4
                  px-0
                "
                to="/"
              >
                {{ this.username }}
              </router-link>
            </div>
            <div class="w-6/12 flex justify-end">
              <button
                type="button"
                class="
                  cursor-pointer
                  text-black
                  opacity-50
                  md:hidden
                  px-3
                  py-1
                  text-xl
                  leading-none
                  bg-transparent
                  rounded
                  border border-solid border-transparent
                "
                v-on:click="toggleCollapseShow('hidden')"
              >
                <i class="fas fa-times"></i>
              </button>
            </div>
          </div>
        </div>
        <!-- Form -->
        <form class="mt-6 mb-4 md:hidden">
          <div class="mb-3 pt-0">
            <input
              type="text"
              placeholder="Search"
              class="
                border-0
                px-3
                py-2
                h-12
                border border-solid border-blueGray-500
                placeholder-blueGray-300
                text-blueGray-600
                bg-white
                rounded
                text-base
                leading-snug
                shadow-none
                outline-none
                focus:outline-none
                w-full
                font-normal
              "
            />
          </div>
        </form>

        <!-- Divider -->
        <hr class="my-4 md:min-w-full" />
        <!-- Heading -->
        <h6
          class="
            md:min-w-full
            text-blueGray-500 text-xs
            uppercase
            font-bold
            block
            pt-1
            pb-4
            no-underline
          "
        >
          User Pages
        </h6>
        <!-- Navigation -->

        <ul class="md:flex-col md:min-w-full flex flex-col list-none">
          <li class="items-center">
            <router-link to="/admin/dashboard" v-slot="{ href, navigate, isActive }">
              <a
                :href="href"
                @click="navigate"
                class="text-xs uppercase py-3 font-bold block"
                :class="[
                  isActive
                    ? 'text-emerald-500 hover:text-emerald-600'
                    : 'text-blueGray-700 hover:text-blueGray-500',
                ]"
              >
                <i
                  class="fas fa-tv mr-2 text-sm"
                  :class="[isActive ? 'opacity-75' : 'text-blueGray-300']"
                ></i>
                Main Dashboard
              </a>
            </router-link>
          </li>

          <li class="items-center">
            <router-link to="/admin/settings" v-slot="{ href, navigate, isActive }">
              <a
                :href="href"
                @click="navigate"
                class="text-xs uppercase py-3 font-bold block"
                :class="[
                  isActive
                    ? 'text-emerald-500 hover:text-emerald-600'
                    : 'text-blueGray-700 hover:text-blueGray-500',
                ]"
              >
                <i
                  class="fa fa-cog mr-2 text-sm"
                  :class="[isActive ? 'opacity-75' : 'text-blueGray-300']"
                ></i>
                YOUR Profile
              </a>
            </router-link>
          </li>

          <li class="items-center">
            <router-link to="/admin/tables" v-slot="{ href, navigate, isActive }">
              <a
                :href="href"
                @click="navigate"
                class="text-xs uppercase py-3 font-bold block"
                :class="[
                  isActive
                    ? 'text-emerald-500 hover:text-emerald-600'
                    : 'text-blueGray-700 hover:text-blueGray-500',
                ]"
              >
                <i
                  class="fas fa-table mr-2 text-sm"
                  :class="[isActive ? 'opacity-75' : 'text-blueGray-300']"
                ></i>
                VIEW DOWNLINES
              </a>
            </router-link>
          </li>

          <li class="items-center">
            <router-link to="/admin/maps" v-slot="{ href, navigate, isActive }">
              <a
                :href="href"
                @click="navigate"
                class="text-xs uppercase py-3 font-bold block"
                :class="[
                  isActive
                    ? 'text-emerald-500 hover:text-emerald-600'
                    : 'text-blueGray-700 hover:text-blueGray-500',
                ]"
              >
                <i
                  class="fas fa-shopping-cart mr-2 text-sm"
                  :class="[isActive ? 'opacity-75' : 'text-blueGray-300']"
                ></i>
                WITHDRAW
              </a>
            </router-link>
          </li>

          <li class="items-center">
            <router-link to="/admin/deposit" v-slot="{ href, navigate, isActive }">
              <a
                :href="href"
                @click="navigate"
                class="text-xs uppercase py-3 font-bold block"
                :class="[
                  isActive
                    ? 'text-emerald-500 hover:text-emerald-600'
                    : 'text-blueGray-700 hover:text-blueGray-500',
                ]"
              >
                <i
                  class="fas fa-shopping-cart mr-2 text-sm"
                  :class="[isActive ? 'opacity-75' : 'text-blueGray-300']"
                ></i>
                DEPOSIT
              </a>
            </router-link>
          </li>
          <li class="items-center">
            <router-link to="admin/invest" v-slot="{ href, navigate, isActive }">
              <a
                :href="href"
                @click="navigate"
                class="text-xs uppercase py-3 font-bold block"
                :class="[
                  isActive
                    ? 'text-emerald-500 hover:text-emerald-600'
                    : 'text-blueGray-700 hover:text-blueGray-500',
                ]"
              >
                <i
                  class="fas fa-box-open mr-2 text-sm"
                  :class="[isActive ? 'opacity-75' : 'text-blueGray-300']"
                ></i>
                INVEST
              </a>
            </router-link>
          </li>
        </ul>

        <!-- Divider -->

        <!-- Navigation -->

        <!-- <ul class="md:flex-col md:min-w-full flex flex-col list-none md:mb-4">
          <li class="items-center">
            <router-link
              class="
                text-blueGray-700
                hover:text-blueGray-500
                text-xs
                uppercase
                py-3
                font-bold
                block
              "
              to="/auth/login"
            >
              <i
                style="color: #006400"
                class="far fa-money-bill-alt text-blueGray-300 mr-2 text-sm"
              ></i>
              Cash investments
            </router-link>
          </li>

          <li class="items-center" style="color: #f7931a">
            <router-link
              class="
                text-blueGray-700
                hover:text-blueGray-500
                text-xs
                uppercase
                py-3
                font-bold
                block
              "
              to="/auth/register"
            >
              <i class="fab fa-btc text-blueGray-300 mr-2 text-sm" style="color: #f7931a"></i>
              Buy & Sell crypto
            </router-link>
          </li>

          <li class="items-center" style="color: #800080">
            <router-link
              class="
                text-blueGray-700
                hover:text-blueGray-500
                text-xs
                uppercase
                py-3
                font-bold
                block
              "
              to="/auth/register"
            >
              <i
                class="fas fa-user-graduate text-blueGray-300 mr-2 text-sm"
                style="color: #800080"
              ></i>
              Refferal Program
            </router-link>
          </li>

          <li class="items-center" style="color: #f7931a">
            <router-link
              class="
                text-blueGray-700
                hover:text-blueGray-500
                text-xs
                uppercase
                py-3
                font-bold
                block
              "
              to="/auth/register"
            >
              <i class="fas fa-dice text-blueGray-300 mr-2 text-sm" style="color: blue"></i>
              Spin & Win
            </router-link>
          </li>

          <li class="items-center" style="color: #f7931a">
            <router-link
              class="
                text-blueGray-700
                hover:text-blueGray-500
                text-xs
                uppercase
                py-3
                font-bold
                block
              "
              to="/auth/register"
            >
              <i
                class="fas fa-question-circle text-blueGray-300 mr-2 text-sm"
                style="color: red"
              ></i>
              Surveys
            </router-link>
          </li>
        </ul> -->
        <!-- Divider -->
        <hr class="my-4 md:min-w-full" />
        <!-- Heading -->
        <h6
          class="
            md:min-w-full
            text-blueGray-500 text-xs
            uppercase
            font-bold
            block
            pt-1
            pb-4
            no-underline
          "
        >
          Actions
        </h6>
        <!-- Navigation -->

        <ul class="md:flex-col md:min-w-full flex flex-col list-none md:mb-4">
          <li class="items-center">
            <router-link
              class="
                text-blueGray-700
                hover:text-blueGray-500
                text-xs
                uppercase
                py-3
                font-bold
                block
              "
              to="/landing"
            >
              <i class="fas fa-key text-blueGray-300 mr-2 text-sm"></i>
              Change password
            </router-link>
          </li>

          <li class="items-center" @click="logout()">
            <router-link
              class="
                text-blueGray-700
                hover:text-blueGray-500
                text-xs
                uppercase
                py-3
                font-bold
                block
              "
              to="/auth/login"
            >
              <i class="fas fa-sign-out-alt text-blueGray-300 mr-2 text-sm"></i>
              LogOut
            </router-link>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>
); }

<script>
import NotificationDropdown from "@/components/Dropdowns/NotificationDropdown.vue";
import UserDropdown from "@/components/Dropdowns/UserDropdown.vue";
import firebase from "firebase";
export default {
  data() {
    return {
      collapseShow: "hidden",
      username: "",
      phonenumber: "",
      activated: false,
      balance: 0,
      plan: "",
      uid: "",
      downlines: 0,
      cashout: 0,
      downline_bonus: 0,
    };
  },
  methods: {
    toggleCollapseShow(classes) {
      this.collapseShow = classes;
    },
  },
  components: {
    NotificationDropdown,
    UserDropdown,
  },
  mounted: function () {
    firebase.auth().onAuthStateChanged((user) => {
      const db = firebase.firestore();
      db.collection("users")
        .doc(user.email)
        .get()
        .then((snapshot) => {
          var data = snapshot.data();
          this.username = data.username;
          this.balance = data.balance;
          this.activated = data.activated;
          this.downlines = data.downlines;
          this.plan = data.plan;
          this.downline_bonus = data.downline_bonus;
        });
    });
  },
};
</script>
