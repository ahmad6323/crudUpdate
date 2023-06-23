<script>

export default {
  name:'navbar'
  }

</script>
<template>
  <nav class="navbar navbar-dark fixed-top bg-dark px-5">
    <!-- Navbar content -->
    <a class="navbar-brand">Crud App</a>
    <form class="form-inline">

    </form>
  </nav>
  <div class="sidebar">
    <a class="active" href="">Home</a>
    <a href="">Add Product</a>
    <a href="#">Display Product</a>
  </div>

  <div class="content">
    <h2>Crud Application </h2>

  </div>
</template>
<style>
.sidebar {
  margin: 0;
  padding: 0;
  width: 200px;
  background-color: black;
  position: fixed;
  height: 100%;
  overflow: auto;
}

.sidebar a {
  display: block;
  color: white;
  padding: 16px;
  text-decoration: none;
}

.sidebar a.active {
  background-color: black;
  color: white;
}

.sidebar a:hover:not(.active) {
  background-color: white;
  color: black;
}

div.content {
  text-transform: uppercase;
  font-weight: 800;
  margin-top: 50px;
margin-left: 200px;
  padding: 1px 16px;
  height: 100px;
text-align: center;
}
@media screen and (max-width: 700px) {
  .sidebar {
    width: 100%;
    height: auto;
    position: relative;
  }
  .sidebar a {float: left;}
  div.content {margin-left: 0;}
}

@media screen and (max-width: 400px) {
  .sidebar a {
    text-align: center;
    float: none;
  }
}
</style>
