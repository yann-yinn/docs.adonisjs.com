---
summary: List of available Edge template helpers
---

Following is the list of all other available view helpers.

---

### app
Reference to the [Application](../../../guides/fundamentals/application.md) instance.

```edge
@if(app.nodeEnvironment === 'development')
  Print some debug log
@endif
```

---

### env
Reference to the [Env.get](../../../guides/fundamentals/environment-variables.md#access-environment-variables) method.

```edge
{{ env('APP_URL') }}
```

---

### config
Reference to the [Config.get](../../../guides/fundamentals/config.md#using-the-config-provider) method.

```edge
{{ config('app.appKey') }}
```

---

### asset
The `asset` helper returns the path to a [compiled frontend assets](../../../guides/http/assets-manager.md#assets-view-helpers) by doing a lookup inside the `manifest.json` file.

```edge
<script src="{{ asset('assets/app.js') }}"></script>

<link
  rel="stylesheet"
  type="text/css"
  href="{{ asset('assets/app.css') }}"
> 
```

---

### assetsManager
The `assetsManager` helpers is a reference to the instance of [AssetsManager class](https://github.com/adonisjs/core/blob/develop/src/AssetsManager/index.ts#L29). 

You will hardly rely on assets manager directly, as the `asset` helper and the `@entryPointStyles` and `@entryPointScripts` tags let you reference the assets inside your templates.

---

### csrfToken
Returns the value of the CSRF token. The helper is only available when the `@adonisjs/shield` is installed and configured.

```edge
<input type="hidden" value="{{ csrfToken }}" name="_token">
```

---

### csrfField
Returns the hidden input element for the CSRF token. The helper is only available when the `@adonisjs/shield` is installed and configured.

```edge
<form method="POST" action="posts">
  {{ csrfField() }}
</form>
```

---

### cspNonce
Returns the value for the `nonce` to be used with inline script tags. Make sure to read the [CSP section](../../../guides/security/web-security.md#csp-nonce) in the web security guide. The helper is only available when the `@adonisjs/shield` is installed and configured.

```edge
<script nonce="{{ cspNonce }}">
</script>
```

---

### auth
Reference to the [ctx.auth](../../../guides/auth/introduction.md#usage) instance. You can use it to display the specific portion of your markup conditionally.

This helper is only available when using the `@adonisjs/auth` package.

```edge
@if(auth.isLoggedIn)
  <p> Hello {{ auth.user.username }} </p>
@endif
```

---

### bouncer
Reference to the [ctx.bouncer](../../../guides/digging-deeper/authorization.md#basic-example) instance. You can make use of the [@can/@cannot](../tags/can.md) tags to conditionally display markup inside your templates.

This helper is only available when using the `@adonisjs/bouncer` package.

```edge
@if(await bouncer.allows('editPost'))
  <a href="/posts/1/edit"> Edit post </a>
@end
```
