<script>
	import { page } from '$app/stores';
</script>

<nav>
    
    <ul>
        <li aria-current={$page.url.pathname === "/clippath" ? 'page' : undefined}>
            <a href="/clippath">card</a>
        </li>
        <li aria-current={$page.url.pathname === '/card' ? 'page' : undefined}>
            <a href="/card">card</a>
        </li>
       
    </ul>
   
</nav>