<template>
    <nav class="fixed-top-nav">
        <div class="logo">
            <a href="#" class="simple-text">
                <span class="logo-white">PLAYR</span><span class="logo-purple">DASHBOARD</span>
            </a>
        </div>
        <div class="dropdown-container">
            <img src="http://via.placeholder.com/60/6e7fff" alt="">
            <dropdown title="Austin Walper">
                <ul>
                    <li><a href="!#">Home</a></li>
                    <li><a href="!#">About</a></li>
                    <li><a href="!#">Profile</a></li>
                </ul>
            </dropdown>
        </div>
    </nav>
</template>
<script>
import Dropdown from './Dropdown'
export default {
  components: {
    dropdown: Dropdown
  }
}
</script>
<style scoped>
.fixed-top-nav {
  position: fixed;
  top: 0px;
  width: 100%;
  z-index: 1000;
  background-color: #1d1e3e;
  height: 80px;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-pack: justify;
  -ms-flex-pack: justify;
  justify-content: space-between;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
}
.logo {
  text-align: center;
  display: inline-block;
  width: 200px;
  vertical-align: middle;
  height: 80px;
}

.dropdown-container {
  display: inline-block;
  width: calc(100% -220px);
  padding-right: 40px;
}

.dropdown-container li {
  list-style: none;
      padding: 4px;
}

.dropdown-container img {
  display: inline-block;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  margin-right: 4px;
}

.dropdown-container > * {
  display: inline-block;
}

.dropdown-container  ul {
    padding-left: 0px;
    text-align: center
}

.open .dropdown-menu {
    padding: 20px;
    background-color: #d2d2ff
}

li p.notification {
  color: white !important;
}

a:after {
  content: "";
  display: inline-block;
  height: 80px;
  vertical-align: middle;
}

.logo span {
  vertical-align: middle;
  display: inline-block;
}

.logo-white {
  color: white;
  font-size: 1.1em;
  padding-right: 2px;
  display: inline-block;
  vertical-align: middle;
}

.logo-purple {
  font-size: 1.05em;
  color: #6e7fff;
  font-weight: 800;
  display: inline-block;
  position: relative;
  top: 1px;
}
</style>
