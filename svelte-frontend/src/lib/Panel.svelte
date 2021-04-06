<style>
	@import "/static/css/dashboard.css";
	
</style>
<script >
    import { onMount } from 'svelte';
    import "/static/js/feather.min.js"; 
    onMount(async () => {
		feather.replace();
    });
    let navItems = [
        {
            name:"home",
            link:"/",
            icon:"home"
        },
        {
            name:"Cool Charts",
            link:"/charts",
            icon:"bar-chart-2"
		},
		{
            name:"Create Post",
            link:"/edit",
            icon:"bar-chart-2"
        }
        
    ]
</script>


	<header class="navbar navbar-dark sticky-top bg-dark flex-md-nowrap p-0 shadow">
		<a class="navbar-brand col-md-3 col-lg-2 me-0 px-3" href="#">Awesome Dashboard</a>
		<button class="navbar-toggler position-absolute d-md-none collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#sidebarMenu" aria-controls="sidebarMenu" aria-expanded="false" aria-label="Toggle navigation">
		  <span class="navbar-toggler-icon"></span>
		</button>
		<input class="form-control form-control-dark w-100" type="text" placeholder="Search" aria-label="Search">
		<ul class="navbar-nav px-3">
		  <li class="nav-item text-nowrap">
			<a class="nav-link" href="#">Sign out</a>
		  </li>
		</ul>
	  </header>
	  
	  <div class="container-fluid">
		<div class="row">
		  <nav id="sidebarMenu" class="col-md-3 col-lg-2 d-md-block bg-light sidebar collapse">
			<div class="position-sticky pt-3">
			  <ul class="nav flex-column">
                {#each navItems as { name,link,icon }, i}
                    <li class="nav-item">
                        <a class="nav-link " aria-current="page" href={link}>
                        <span data-feather={icon}></span>
                            {name}
                        </a>
                    </li>
                    
                {/each}
	  
			  <h6 class="sidebar-heading d-flex justify-content-between align-items-center px-3 mt-4 mb-1 text-muted">
				<span>Saved reports</span>
				<a class="link-secondary" href="#" aria-label="Add a new report">
				  <span data-feather="plus-circle"></span>
				</a>
			  </h6>
			  <ul class="nav flex-column mb-2">
				<li class="nav-item">
				  <a class="nav-link" href="#">
					<span data-feather="file-text"></span>
					Current month
				  </a>
				</li>
				<li class="nav-item">
				  <a class="nav-link" href="#">
					<span data-feather="file-text"></span>
					Last quarter
				  </a>
				</li>
				<li class="nav-item">
				  <a class="nav-link" href="#">
					<span data-feather="file-text"></span>
					Social engagement
				  </a>
				</li>
				<li class="nav-item">
				  <a class="nav-link" href="#">
					<span data-feather="file-text"></span>
					Year-end sale
				  </a>
				</li>
			  </ul>
			</div>
		  </nav>
          <main  class="col-md-9 ms-sm-auto col-lg-10 px-md-4">
             <slot></slot>
	      </main>
          
		</div>
	  </div>


