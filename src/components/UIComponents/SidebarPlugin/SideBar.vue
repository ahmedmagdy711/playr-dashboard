<template>
  <div :class="sidebarClasses" :data-background-color="backgroundColor" :data-active-color="activeColor">
    <!--
            Tip 1: you can change the color of the sidebar's background using: data-background-color="white | black | darkblue"
            Tip 2: you can change the color of the active button using the data-active-color="primary | info | success | warning | danger"
        -->
    <!-- -->
    <div class="sidebar-wrapper" id="style-3">
      <div class="logo">
        <a href="#" class="simple-text">
            <span class="logo-white">PLAYR</span><span class="logo-purple">DASHBOARD</span>
        </a>
      </div>
      <slot>

      </slot>
      <ul :class="navClasses">
        <!--By default vue-router adds an active class to each route link. This way the links are colored when clicked-->
        <router-link v-for="(link,index) in sidebarLinks" :to="link.path" tag="li" :ref="link.name" :key="index">
          <a>
            <i :class="link.icon"></i>

            <p>{{link.name}}
            </p>
          </a>
        </router-link>
        <li class="expandable">
          <router-link to="/admin/icons" class="expand">
            <i class="ti-cup"></i>
            <p>Test</p>
            <ul>
              <li>
                <router-link to="">Sub 1</router-link>
                </li>
                <li>
                  <router-link to="">Sub 2</router-link>
                 </li>
            </ul>
            </router-link>
        </li>
      </ul>
      <moving-arrow :move-y="arrowMovePx">

      </moving-arrow>
    </div>
  </div>
</template>
<script>
  import MovingArrow from './MovingArrow.vue'
  export default {
    props: {
      type: {
        type: String,
        default: 'sidebar',
        validator: (value) => {
          let acceptedValues = ['sidebar', 'navbar']
          return acceptedValues.indexOf(value) !== -1
        }
      },
      backgroundColor: {
        type: String,
        default: 'black',
        validator: (value) => {
          let acceptedValues = ['white', 'black', 'darkblue']
          return acceptedValues.indexOf(value) !== -1
        }
      },
      activeColor: {
        type: String,
        default: 'success',
        validator: (value) => {
          let acceptedValues = ['primary', 'info', 'success', 'warning', 'danger']
          return acceptedValues.indexOf(value) !== -1
        }
      },
      sidebarLinks: {
        type: Array,
        default: () => []
      }
    },
    components: {
      MovingArrow
    },
    computed: {
      sidebarClasses () {
        if (this.type === 'sidebar') {
          return 'sidebar'
        } else {
          return 'collapse navbar-collapse off-canvas-sidebar'
        }
      },
      navClasses () {
        if (this.type === 'sidebar') {
          return 'nav'
        } else {
          return 'nav navbar-nav'
        }
      },
      /**
       * Styles to animate the arrow near the current active sidebar link
       * @returns {{transform: string}}
       */
      arrowMovePx () {
        return this.linkHeight * this.activeLinkIndex
      }
    },
    data () {
      return {
        linkHeight: 60,
        activeLinkIndex: 0,

        windowWidth: 0,
        isWindows: false,
        hasAutoHeight: false
      }
    },
    methods: {
      findActiveLink () {
        this.sidebarLinks.find((element, index) => {
          let found = element.path === this.$route.path
          if (found) {
            this.activeLinkIndex = index
          }
          return found
        })
      }
    },
    mounted () {
      this.findActiveLink()
    },
    watch: {
      $route: function (newRoute, oldRoute) {
        this.findActiveLink()
      }
    }
  }

</script>
<style >
  .sidebar-wrapper {
    background-color: #1d1e3e;
    border-right: 0px;
    box-shadow: inset -1px 0px 0px 0px #1d1e3e !important;
  }

  .sidebar-wrapper {
    position: fixed !important;
  }

  .router-link-exact-active.active {
    color: white !important;
    background-color: #6e7fff !important;
  }
  .router-link-exact-active.active * {
    color: white !important; 
  }

   .expandable {
     padding: 0px;
   }

    .expandable .expand p{
      padding: 10px 70px !important;
    }

    .expandable .expand i {
      padding: 10px 26px  !important;
    }

    .expandable > a {
      padding: 0px !important;
    } 

  .expand ul li{
    display: block !important;
    list-style: none;
    padding: 10px 0px;
  }

   .expand ul {
     padding-left: 0px;
     border-left: 1px solid #17192f;
   }

    .expand ul,
    .expand ul li a

     {
     background-color: #17192f !important;
    }


    .expand .router-link-exact-active.active  {
     background-color: #17192f !important;

    }

    .expand > ul {
      display: none !important;
    }

    .expand.router-link-exact-active > ul {
      display: block !important
    }
 </style>
