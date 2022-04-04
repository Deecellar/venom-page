<script lang="ts">
import { Link } from "svelte-routing";



</script>

<nav>
    <ul class="flex ">
        <li class="ml-2 text-lg"><Link to="/">Home</Link></li>
        <li class="ml-2 text-lg"><Link to="download">Downloads</Link></li>
        <li class="ml-2 text-lg"><Link to="wiki">Wiki</Link></li>
        <li class="ml-2 text-lg"><Link to="about">About</Link></li>
        <li class="ml-2 text-lg"><Link to="contact">Contact</Link></li>
    </ul>    
</nav>