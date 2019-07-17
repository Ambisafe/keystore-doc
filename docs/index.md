<a href="https://www.ambisafe.co/">![test](img/logo_red.png)</a>
**********
# Keystore Service

Service deployed on <https://keystore.ambisafe.co>.

**********

## Persist newly generated key:

**POST /keystore/&lt;uuid v4&gt;** with header **Authorization: &lt;JWT keystore token&gt;**

```json
{
  "crypto" : "<according to secret storage definition>",
  "address" : "<eth address>",
  "id" : "<uuid v4>",
  "version" : "arbitrary"
}
```
returns:
```markdown
http 201 - created
http 400 - uuid in json does not match uuid in url / no address contained
http 401 - storageToken not valid
http 409 - conflict
```

## Retrieve key:
```
GET /keystore/<uuid v4>
```
returns:
```
http 200 - ok
http 403 - banned
http 404 - not found
```
