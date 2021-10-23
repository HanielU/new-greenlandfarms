<script>
	import { prefetch, Router } from "@roxi/routify";
	import { routes } from "../.routify/routes";

	prefetch("/");
</script>

<Router {routes} />
