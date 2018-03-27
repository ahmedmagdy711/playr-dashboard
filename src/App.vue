<template>
  <div :class="{'nav-open': $sidebar.showSidebar}">
    <fixed-nav></fixed-nav>
    <router-view></router-view>
    <!--This sidebar appears only for screens smaller than 992px-->
    <side-bar type="navbar" :sidebar-links="$sidebar.sidebarLinks">
      <ul class="nav navbar-nav">
        <li>
          <a class="dropdown-toggle" data-toggle="dropdown">
            <i class="ti-panel"></i>
            <p>Stats</p>
          </a>
        </li>
        <drop-down title="5 Notifications" icon="ti-bell">

          <li><a>Notification 1</a></li>
          <li><a>Notification 2</a></li>
          <li><a>Notification 3</a></li>
          <li><a>Notification 4</a></li>
          <li><a>Another notification</a></li>

        </drop-down>
        <li>
          <a>
            <i class="ti-settings"></i>
            <p>Settings</p>
          </a>
        </li>
        <li class="divider"></li>
      </ul>
    </side-bar>
  </div>
</template>

<script>
  import FixedTopNav from './components/UIComponents/FixedTopNav'
  export default {
    components: {
      'fixed-nav': FixedTopNav
    }
  }
</script>

<style lang="scss">
.moving-arrow {
  display: none;
}

.main-panel {
  background-color: #17192f !important;
  top: 80px;
  max-height: none !important;
  height: auto !important;
}

.main-panel > .content {
  top: 60px;
}

</style>
