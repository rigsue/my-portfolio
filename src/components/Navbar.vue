<template>
  <nav class="navbar navbar-expand-md fixed-top py-2 shadow-sm container-fluid" id="nav-bar">
    <div class="row px-4">
      <!-- Brand -->
      <div class="col-md-3 mx-5 px-5">
      	<a class="navbar-brand fw-bold text-light fs-4" href="#landing">
        <!-- <i class="bi bi-code-slash me-2"></i>  -->
      	<strong>
        RICHARD REGALA
        </strong>
      </a>
		
      </div>
    

      <!-- Toggler -->
      
        <button
        class="navbar-toggler border-0"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#collapsnavbar"
        aria-controls="collapsnavbar"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon-custom"></span>
      </button>
     
      <div class="d-none d-md-block col-md-3 ms-3">
        <img src="/images/riglog.png" class="w-15 mx-5 rounded-circle" id="riglog">
      </div>
      	
      <!-- Links -->
      <div class="col-md-3 collapse navbar-collapse justify-content-end px-5 mx-5" id="collapsnavbar">
      		
        <!-- <div class="navbar-nav text-center px-5 ms-5"> -->
        	
          <a class="nav-link px-3 fw-semibold" href="#landing">Home</a>
          <a class="nav-link px-3 fw-semibold" href="#projects">My Projects</a>
          <a class="nav-link px-3 fw-semibold" href="#tools">Tools</a>
          <a class="nav-link px-3 fw-semibold" href="#contact">Contact</a>
        <!-- </div> -->
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  mounted() {
    // highlight active section on scroll
    const sections = document.querySelectorAll("section, main");
    const navLinks = document.querySelectorAll(".nav-link");

    window.addEventListener("scroll", () => {
      let current = "";
      sections.forEach((section) => {
        const sectionTop = section.offsetTop - 80;
        if (scrollY >= sectionTop) current = section.getAttribute("id");
      });

      navLinks.forEach((link) => {
        link.classList.remove("active");
        if (link.getAttribute("href").includes(current)) {
          link.classList.add("active");
        }
      });
    });
  },
};
</script>

<style scoped>
/* === Navbar Base Style === */
.w-15 {
  width: 15% !important;
}
#nav-bar {
  background: linear-gradient(90deg, #007bff, #6610f2);
  transition: background 0.3s ease;
  z-index: 1000;
}

#nav-bar .navbar-brand {
  color: #fff !important;
}

#nav-bar .nav-link {
  color: #f8f9fa !important;
  position: relative;
  transition: color 0.3s ease;
}

#nav-bar .nav-link::after {
  content: "";
  position: absolute;
  bottom: 2px;
  left: 50%;
  transform: translateX(-50%);
  width: 0%;
  height: 2px;
  background: #fff;
  transition: width 0.3s ease;
}

#nav-bar .nav-link:hover::after,
#nav-bar .nav-link.active::after {
  width: 60%;
}

#nav-bar .nav-link:hover {
  color: #fff !important;
}

/* === Custom Hamburger Icon === */
.navbar-toggler-icon-custom {
  position: relative;
  width: 28px;
  height: 3px;
  background-color: #fff;
  display: block;
  transition: all 0.3s ease;
}

.navbar-toggler-icon-custom::before,
.navbar-toggler-icon-custom::after {
  content: "";
  position: absolute;
  left: 0;
  width: 28px;
  height: 3px;
  background-color: #fff;
  transition: all 0.3s ease;
}

.navbar-toggler-icon-custom::before {
  top: -8px;
}

.navbar-toggler-icon-custom::after {
  top: 8px;
}

/* Make sure toggler is always visible */
.navbar-toggler {
  color: white !important;
  z-index: 1100;
}

/* Smooth scroll */
html {
  scroll-behavior: smooth;
}
</style>
