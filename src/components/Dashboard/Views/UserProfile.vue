<template>
    <div class="row custom-padding">
      <div class="col-lg-12 col-md-12">
        <form class="card">
          <h4>Test Field</h4>
          <div class="form-group">
            <label for="">Test form</label>
            <input type="text" class="form-control">
          </div>
        </form>
      </div>
    </div>
</template>
<script>
  import EditProfileForm from './UserProfile/EditProfileForm.vue'
  import UserCard from './UserProfile/UserCard.vue'
  import MembersCard from './UserProfile/MembersCard.vue'
  export default {
    components: {
      EditProfileForm,
      UserCard,
      MembersCard
    }
  }

</script>
<style scoped>
.custom-padding {
  padding: 20px;
}
.card {
  min-height: 400px;
  background-color: #1d1f3e;
  border-radius: 0px;
  box-shadow: none!important;
  border: 0px;
  padding: 20px 20px !important;
}

.card h4 {
  color: rgb(110, 127, 255);
  margin: 0px;
  font-size: 18px;
  margin-bottom: 20px;
}

.form-group {
  margin: 10px 0px;
}

.form-group label {
  color: white;
  margin-bottom: 8px;
}

.form-group input {
  background: transparent;
  border: 1px solid rgb(110, 127, 255);
  color: white;
}
</style>
