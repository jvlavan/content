---
title: Sec-CH-Prefers-Reduced-Transparency header
short-title: Sec-CH-Prefers-Reduced-Transparency
slug: Web/HTTP/Reference/Headers/Sec-CH-Prefers-Reduced-Transparency
page-type: http-header
status:
  - experimental
browser-compat: http.headers.Sec-CH-Prefers-Reduced-Transparency
sidebar: http
---

{{SeeCompatTable}}{{SecureContext_Header}}

The HTTP **`Sec-CH-Prefers-Reduced-Transparency`** {{Glossary("request header")}} is a [user agent client hint](/en-US/docs/Web/HTTP/Guides/Client_hints#user_preference_media_features_client_hints) that indicates the user agent's preference for reduced transparency.

If a server signals to a client via the {{httpheader("Accept-CH")}} header that it accepts `Sec-CH-Prefers-Reduced-Transparency`, the client can then respond with this header to indicate the user's preference for reduced transparency. The server can send the client appropriately adapted content — for example, CSS or images — to reduce the transparency of the content.

This header is modeled on the {{cssxref("@media/prefers-reduced-transparency", "prefers-reduced-transparency")}} media query.

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">Header type</th>
      <td>
        {{Glossary("Request header")}},
        <a href="/en-US/docs/Web/HTTP/Guides/Client_hints">Client hint</a>
      </td>
    </tr>
    <tr>
      <th scope="row">{{Glossary("Forbidden request header")}}</th>
      <td>Yes (<code>Sec-</code> prefix)</td>
    </tr>
  </tbody>
</table>

## Syntax

```http
Sec-CH-Prefers-Reduced-Transparency: <preference>
```

### Directives

- `<preference>`
  - : The user agent's preference for reduced transparency. This is often taken from the underlying operating system's setting. The value of this directive can be either `no-preference` or `reduce`.

## Examples

### Using Sec-CH-Prefers-Reduced-Transparency

The client makes an initial request to the server:

```http
GET / HTTP/1.1
Host: example.com
```

The server responds, telling the client via {{httpheader("Accept-CH")}} that it accepts `Sec-CH-Prefers-Reduced-Transparency`. In this example {{httpheader("Critical-CH")}} is also used, indicating that `Sec-CH-Prefers-Reduced-Transparency` is considered a [critical client hint](/en-US/docs/Web/HTTP/Guides/Client_hints#critical_client_hints).

```http
HTTP/1.1 200 OK
Content-Type: text/html
Accept-CH: Sec-CH-Prefers-Reduced-Transparency
Vary: Sec-CH-Prefers-Reduced-Transparency
Critical-CH: Sec-CH-Prefers-Reduced-Transparency
```

> [!NOTE]
> We've also specified `Sec-CH-Prefers-Reduced-Transparency` in the {{httpheader("Vary")}} header, to indicate to the browser that the served content will differ based on this header value — even if the URL stays the same — so the browser shouldn't just use an existing cached response and instead should cache this response separately. Each header listed in the `Critical-CH` header should also be present in the `Accept-CH` and `Vary` headers.

The client automatically retries the request (due to `Critical-CH` being specified above), telling the server via `Sec-CH-Prefers-Reduced-Transparency` that it has a user preference for reduced transparency:

```http
GET / HTTP/1.1
Host: example.com
Sec-CH-Prefers-Reduced-Transparency: "reduce"
```

The client will include the header in subsequent requests in the current session unless the `Accept-CH` changes in responses to indicate that it is no longer supported by the server.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Client hints](/en-US/docs/Web/HTTP/Guides/Client_hints)
- [User-Agent Client Hints API](/en-US/docs/Web/API/User-Agent_Client_Hints_API)
- {{HTTPHeader("Accept-CH")}}
- [HTTP Caching: Vary](/en-US/docs/Web/HTTP/Guides/Caching#vary) and the {{HTTPHeader("Vary")}} header
- [Improving user privacy and developer experience with User-Agent Client Hints](https://developer.chrome.com/docs/privacy-security/user-agent-client-hints) (developer.chrome.com)
