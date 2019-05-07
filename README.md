# ![LOGO](logo.png) Digital Asset Links **flow**ground Connector

## Description

A generated **flow**ground connector for the Digital Asset Links API (version v1).

Generated from: https://api.apis.guru/v2/specs/googleapis.com/digitalassetlinks/v1/swagger.json<br/>
Generated at: 2019-05-07T17:41:34+03:00

## API Description

Discovers relationships between online assets such as websites or mobile apps.

## Authorization

This API does not require authorization.

## Actions

### Determines whether the specified (directional) relationship exists between<br/>
> the specified source and target assets.<br/>
> <br/>
> The relation describes the intent of the link between the two assets as<br/>
> claimed by the source asset.  An example for such relationships is the<br/>
> delegation of privileges or permissions.<br/>
> <br/>
> This command is most often used by infrastructure systems to check<br/>
> preconditions for an action.  For example, a client may want to know if it<br/>
> is OK to send a web URL to a particular mobile app instead. The client can<br/>
> check for the relevant asset link from the website to the mobile app to<br/>
> decide if the operation should be allowed.<br/>
> <br/>
> A note about security: if you specify a secure asset as the source, such as<br/>
> an HTTPS website or an Android app, the API will ensure that any<br/>
> statements used to generate the response have been made in a secure way by<br/>
> the owner of that asset.  Conversely, if the source asset is an insecure<br/>
> HTTP website (that is, the URL starts with `http://` instead of `https://`),<br/>
> the API cannot verify its statements securely, and it is not possible to<br/>
> ensure that the website's statements have not been altered by a third<br/>
> party.  For more information, see the [Digital Asset Links technical design<br/>
> specification](https://github.com/google/digitalassetlinks/blob/master/well-known/details.md).

*Tags:* `assetlinks`

#### Input Parameters
* `relation` - _optional_ - Query string for the relation.

We identify relations with strings of the format `<kind>/<detail>`, where
`<kind>` must be one of a set of pre-defined purpose categories, and
`<detail>` is a free-form lowercase alphanumeric string that describes the
specific use case of the statement.

Refer to [our API documentation](/digital-asset-links/v1/relation-strings)
for the current list of supported relations.

For a query to match an asset link, both the query's and the asset link's
relation strings must match exactly.

Example: A query with relation `delegate_permission/common.handle_all_urls`
matches an asset link with relation
`delegate_permission/common.handle_all_urls`.
* `source.androidApp.certificate.sha256Fingerprint` - _optional_ - The uppercase SHA-265 fingerprint of the certificate.  From the PEM
 certificate, it can be acquired like this:

    $ keytool -printcert -file $CERTFILE | grep SHA256:
    SHA256: 14:6D:E9:83:C5:73:06:50:D8:EE:B9:95:2F:34:FC:64:16:A0:83: \
        42:E6:1D:BE:A8:8A:04:96:B2:3F:CF:44:E5

or like this:

    $ openssl x509 -in $CERTFILE -noout -fingerprint -sha256
    SHA256 Fingerprint=14:6D:E9:83:C5:73:06:50:D8:EE:B9:95:2F:34:FC:64: \
        16:A0:83:42:E6:1D:BE:A8:8A:04:96:B2:3F:CF:44:E5

In this example, the contents of this field would be `14:6D:E9:83:C5:73:
06:50:D8:EE:B9:95:2F:34:FC:64:16:A0:83:42:E6:1D:BE:A8:8A:04:96:B2:3F:CF:
44:E5`.

If these tools are not available to you, you can convert the PEM
certificate into the DER format, compute the SHA-256 hash of that string
and represent the result as a hexstring (that is, uppercase hexadecimal
representations of each octet, separated by colons).
* `source.androidApp.packageName` - _optional_ - Android App assets are naturally identified by their Java package name.
For example, the Google Maps app uses the package name
`com.google.android.apps.maps`.
REQUIRED
* `source.web.site` - _optional_ - Web assets are identified by a URL that contains only the scheme, hostname
and port parts.  The format is

    http[s]://<hostname>[:<port>]

Hostnames must be fully qualified: they must end in a single period
("`.`").

Only the schemes "http" and "https" are currently allowed.

Port numbers are given as a decimal number, and they must be omitted if the
standard port numbers are used: 80 for http and 443 for https.

We call this limited URL the "site".  All URLs that share the same scheme,
hostname and port are considered to be a part of the site and thus belong
to the web asset.

Example: the asset with the site `https://www.google.com` contains all
these URLs:

  *   `https://www.google.com/`
  *   `https://www.google.com:443/`
  *   `https://www.google.com/foo`
  *   `https://www.google.com/foo?bar`
  *   `https://www.google.com/foo#bar`
  *   `https://user@password:www.google.com/`

But it does not contain these URLs:

  *   `http://www.google.com/`       (wrong scheme)
  *   `https://google.com/`          (hostname does not match)
  *   `https://www.google.com:444/`  (port does not match)
REQUIRED
* `target.androidApp.certificate.sha256Fingerprint` - _optional_ - The uppercase SHA-265 fingerprint of the certificate.  From the PEM
 certificate, it can be acquired like this:

    $ keytool -printcert -file $CERTFILE | grep SHA256:
    SHA256: 14:6D:E9:83:C5:73:06:50:D8:EE:B9:95:2F:34:FC:64:16:A0:83: \
        42:E6:1D:BE:A8:8A:04:96:B2:3F:CF:44:E5

or like this:

    $ openssl x509 -in $CERTFILE -noout -fingerprint -sha256
    SHA256 Fingerprint=14:6D:E9:83:C5:73:06:50:D8:EE:B9:95:2F:34:FC:64: \
        16:A0:83:42:E6:1D:BE:A8:8A:04:96:B2:3F:CF:44:E5

In this example, the contents of this field would be `14:6D:E9:83:C5:73:
06:50:D8:EE:B9:95:2F:34:FC:64:16:A0:83:42:E6:1D:BE:A8:8A:04:96:B2:3F:CF:
44:E5`.

If these tools are not available to you, you can convert the PEM
certificate into the DER format, compute the SHA-256 hash of that string
and represent the result as a hexstring (that is, uppercase hexadecimal
representations of each octet, separated by colons).
* `target.androidApp.packageName` - _optional_ - Android App assets are naturally identified by their Java package name.
For example, the Google Maps app uses the package name
`com.google.android.apps.maps`.
REQUIRED
* `target.web.site` - _optional_ - Web assets are identified by a URL that contains only the scheme, hostname
and port parts.  The format is

    http[s]://<hostname>[:<port>]

Hostnames must be fully qualified: they must end in a single period
("`.`").

Only the schemes "http" and "https" are currently allowed.

Port numbers are given as a decimal number, and they must be omitted if the
standard port numbers are used: 80 for http and 443 for https.

We call this limited URL the "site".  All URLs that share the same scheme,
hostname and port are considered to be a part of the site and thus belong
to the web asset.

Example: the asset with the site `https://www.google.com` contains all
these URLs:

  *   `https://www.google.com/`
  *   `https://www.google.com:443/`
  *   `https://www.google.com/foo`
  *   `https://www.google.com/foo?bar`
  *   `https://www.google.com/foo#bar`
  *   `https://user@password:www.google.com/`

But it does not contain these URLs:

  *   `http://www.google.com/`       (wrong scheme)
  *   `https://google.com/`          (hostname does not match)
  *   `https://www.google.com:444/`  (port does not match)
REQUIRED
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters.
* `uploadType` - _optional_ - Legacy upload protocol for media (e.g. "media", "multipart").
* `upload_protocol` - _optional_ - Upload protocol for media (e.g. "raw", "multipart").

### Retrieves a list of all statements from a given source that match the<br/>
> specified target and statement string.<br/>
> <br/>
> The API guarantees that all statements with secure source assets, such as<br/>
> HTTPS websites or Android apps, have been made in a secure way by the owner<br/>
> of those assets, as described in the [Digital Asset Links technical design<br/>
> specification](https://github.com/google/digitalassetlinks/blob/master/well-known/details.md).<br/>
> Specifically, you should consider that for insecure websites (that is,<br/>
> where the URL starts with `http://` instead of `https://`), this guarantee<br/>
> cannot be made.<br/>
> <br/>
> The `List` command is most useful in cases where the API client wants to<br/>
> know all the ways in which two assets are related, or enumerate all the<br/>
> relationships from a particular source asset.  Example: a feature that<br/>
> helps users navigate to related items.  When a mobile app is running on a<br/>
> device, the feature would make it easy to navigate to the corresponding web<br/>
> site or Google+ profile.

*Tags:* `statements`

#### Input Parameters
* `relation` - _optional_ - Use only associations that match the specified relation.

See the [`Statement`](#Statement) message for a detailed definition of
relation strings.

For a query to match a statement, one of the following must be true:

*    both the query's and the statement's relation strings match exactly,
     or
*    the query's relation string is empty or missing.

Example: A query with relation `delegate_permission/common.handle_all_urls`
matches an asset link with relation
`delegate_permission/common.handle_all_urls`.
* `source.androidApp.certificate.sha256Fingerprint` - _optional_ - The uppercase SHA-265 fingerprint of the certificate.  From the PEM
 certificate, it can be acquired like this:

    $ keytool -printcert -file $CERTFILE | grep SHA256:
    SHA256: 14:6D:E9:83:C5:73:06:50:D8:EE:B9:95:2F:34:FC:64:16:A0:83: \
        42:E6:1D:BE:A8:8A:04:96:B2:3F:CF:44:E5

or like this:

    $ openssl x509 -in $CERTFILE -noout -fingerprint -sha256
    SHA256 Fingerprint=14:6D:E9:83:C5:73:06:50:D8:EE:B9:95:2F:34:FC:64: \
        16:A0:83:42:E6:1D:BE:A8:8A:04:96:B2:3F:CF:44:E5

In this example, the contents of this field would be `14:6D:E9:83:C5:73:
06:50:D8:EE:B9:95:2F:34:FC:64:16:A0:83:42:E6:1D:BE:A8:8A:04:96:B2:3F:CF:
44:E5`.

If these tools are not available to you, you can convert the PEM
certificate into the DER format, compute the SHA-256 hash of that string
and represent the result as a hexstring (that is, uppercase hexadecimal
representations of each octet, separated by colons).
* `source.androidApp.packageName` - _optional_ - Android App assets are naturally identified by their Java package name.
For example, the Google Maps app uses the package name
`com.google.android.apps.maps`.
REQUIRED
* `source.web.site` - _optional_ - Web assets are identified by a URL that contains only the scheme, hostname
and port parts.  The format is

    http[s]://<hostname>[:<port>]

Hostnames must be fully qualified: they must end in a single period
("`.`").

Only the schemes "http" and "https" are currently allowed.

Port numbers are given as a decimal number, and they must be omitted if the
standard port numbers are used: 80 for http and 443 for https.

We call this limited URL the "site".  All URLs that share the same scheme,
hostname and port are considered to be a part of the site and thus belong
to the web asset.

Example: the asset with the site `https://www.google.com` contains all
these URLs:

  *   `https://www.google.com/`
  *   `https://www.google.com:443/`
  *   `https://www.google.com/foo`
  *   `https://www.google.com/foo?bar`
  *   `https://www.google.com/foo#bar`
  *   `https://user@password:www.google.com/`

But it does not contain these URLs:

  *   `http://www.google.com/`       (wrong scheme)
  *   `https://google.com/`          (hostname does not match)
  *   `https://www.google.com:444/`  (port does not match)
REQUIRED
* `fields` - _optional_ - Selector specifying which fields to include in a partial response.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters.
* `uploadType` - _optional_ - Legacy upload protocol for media (e.g. "media", "multipart").
* `upload_protocol` - _optional_ - Upload protocol for media (e.g. "raw", "multipart").

## License

**flow**ground :- Telekom iPaaS / googleapis-com-digitalassetlinks-connector<br/>
Copyright © 2019, [Deutsche Telekom AG](https://www.telekom.de)<br/>
contact: flowground@telekom.de

All files of this connector are licensed under the Apache 2.0 License. For details
see the file LICENSE on the toplevel directory.
