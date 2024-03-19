<script>
	import logo from "$lib/img/logo.png"
    import user from "$lib/img/person.svg"

</script>

<nav class="navbar navbar-expand-lg bg-body-tertiary">
    <div class="container-fluid">
        <a class="navbar-brand" href="/">
            <img src={logo} alt="Bootstrap" width="40" height="40">
          </a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <a class="nav-link active" aria-current="page" href="#">Home</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">Link</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="/message">Message</a>
          </li>
          
    
        </ul>
        <form class="d-flex" role="search">
          <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
          <button class="btn btn-outline-success" type="submit">Search</button>
        </form>
        <ul class="navbar-nav me-rigth mb-0 mb-lg-0">
            <li class="nav-item dropdown">
              <a class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown" aria-expanded="false">
                <img src={user} alt="Bootstrap" width="30" height="30">
              </a>
              <ul class="dropdown-menu drop">
                <li><a class="dropdown-item" href="/mypage">Pagina mea</a></li>
                <li><a class="dropdown-item" href="#">Setari</a></li>
                <li><hr class="dropdown-divider"></li>
                <li><a class="dropdown-item" href="/login">Iesire</a></li>
              </ul>
            </li>
          </ul>
      </div>
    </div>
  </nav>

<style>
.navbar {
    padding-inline: 80px;
    padding-inline-end: 100px;
}
</style>