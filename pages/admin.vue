<template>
	
</template>

<script>
import CMS from 'netlify-cms'

// Now the registry is available via the CMS object.
CMS.registerPreviewTemplate('my-template', MyTemplate)

export default {
	script: [
        { src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }
	],
	mounted: [
		{
			if (window.netlifyIdentity) {
				window.netlifyIdentity.on("init", user => {
				if (!user) {
					window.netlifyIdentity.on("login", () => {
					document.location.href = "/admin/";
					});
				}
				});
			}
		}
	]
}
</script>
