<template>
  <div>
    <b-sidebar id="sidebar-no-header" aria-labelledby="sidebar-no-header-title" no-header shadow>
      <template>
        <div class="p-3 mt-5">
          <nav class="mb-3 mt-4">
            <b-nav vertical>
              <b-nav-item active><router-link to="/" class="nav-item">Profile</router-link></b-nav-item>
              <b-nav-item><router-link to="/payment" class="nav-item">Payment</router-link></b-nav-item>
            </b-nav>
          </nav>
        </div>
      </template>
    </b-sidebar>
  </div>
</template>

<style>
  .nav-item{
    color: #484d4e;
    text-decoration: none;
    font-weight: 600;
    font-size: 18px;
  }
  .nav-item:hover{
    color: #484d4e;
    text-decoration: none;
  }
  @media only screen and (max-width: 600px) {
    #sidebar-no-header{
      width: 100%;
    }  
  }
</style>