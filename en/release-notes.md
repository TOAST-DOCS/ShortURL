<!-- pre-align:aligned sig=3152e719e565 -->

<a id="application-service-shorturl-release-notes"></a>
## Application Service > ShortURL > Release Notes { #application-service-shorturl-release-notes }

<a id="march-10-2026"></a>
### March 10, 2026 { #march-10-2026 }

<!-- TODO: translate body -->

<a id="march-10-2026-feature-updates"></a>
#### Feature Updates

<!-- TODO: translate body -->

<a id="april-25-2023"></a>
### April 25, 2023 { #april-25-2023 }

<a id="april-25-2023-feature-updates"></a>
#### Feature Updates
* Changed so that a short description (within 100 characters) can be enterred when creating or modifying a shortened URL.

<a id="january-31-2023"></a>
### January 31, 2023 { #january-31-2023 }

<a id="january-31-2023-bug-fixes"></a>
#### Bug Fixes
* Fixed an issue where, when characters outside the ASCII(7) encoding range such as Korean are contained in the original URL, redirection of shortened URLs does not work properly.
    * When accessing the original URL through the shortened URL created, the original URL is converted into an ASCII (7) string and added to the Location header.
    * In this case, the character + is used without any additional encoding.
        * For example, `https://nhn.com?query=안+녕` is converted to `https://nhn.com?query=%EC%95%88+%EB%85%95` and the character `+ ` is not encoded separately as `%2B`.

<a id="october-25-2022"></a>
### October 25, 2022 { #october-25-2022 }

<a id="october-25-2022-feature-updates"></a>
#### Feature Updates
* Changed so that the status value cannot be used when searching for a shortUrl.
* Changed so that the text search condition is limited to the backHalf of the shortUrl when searching for a shortUrl.

<a id="june-30-2022"></a>
### June 30, 2022 { #june-30-2022 }

<a id="june-30-2022-feature-updates"></a>
#### Feature Updates
* Changed the domain name of the API endpoint from `api-shorturl.cloud.toast.com` to `api-shorturl.nhncloudservice.com`.
* Added the QR code download function.
    * You can download a QR code image by clicking the QR code of a generated shortened URL.

<a id="march-29-2022"></a>
### March 29, 2022 { #march-29-2022 }

<a id="march-29-2022-feature-updates"></a>
#### Feature Updates
* Changed so that the queryParameter feature can be enabled or disabled on a per-project basis.

<a id="november-23-2021"></a>
### November 23, 2021 { #november-23-2021 }

<a id="november-23-2021-feature-updates"></a>
#### Feature Updates
* Switched from beta service to official service.
* Improved certificate renewal feature
    * Expired certificates are displayed as expired status.
    * You can use the Edit button to renew the certificate to a certificate with the same common name (CN).

<a id="november-23-2021-bug-fixes"></a>
#### Bug Fixes
* Fixed an issue where expiration date is not set correctly when generating shortUrl through API.

<a id="september-28-2021"></a>
### September 28, 2021 { #september-28-2021 }

<a id="september-28-2021-feature-updates"></a>
#### Feature Updates
* Added a feature to append a query parameter after ShortUrl.
    * For example, if `nh.nu/abc` is linked to `www.coupang.com/vp/products/1821016708`, `nh.nu/abc?param=param` is linked to `www.coupang.com/vp/products/1821016708?param=param`.

<a id="september-28-2021-bug-fixes"></a>
#### Bug Fixes
* Fixed an issue where the status display color in the certificate list does not match the actual status intermittently.

<a id="august-24-2021"></a>
### August 24, 2021 { #august-24-2021 }

<a id="august-24-2021-bug-fixes"></a>
#### Bug fixes
* Fixed an issue where, when you delete an affiliated URL of a campaign, all affiliated URLs of the campaign are deleted.

<a id="july-27-2021"></a>
### July 27, 2021 { #july-27-2021 }

<a id="july-27-2021-feature-updates"></a>
#### Feature Updates
* You can check each event in Cloud Trail.

<a id="july-27-2021-bug-fixes"></a>
#### Bug Fixes
* Fixed an issue where a project that was supposed to be unavailable could be selected when specifying the target to share the domain and certificate.

<a id="june-29-2021"></a>
### June 29, 2021 { #june-29-2021 }

<a id="june-29-2021-feature-updates"></a>
#### Feature Updates
* When registering a certificate for an already existing domain, the name of the project with the registered certificate will be provided.
* The recently registered shortUrl is at the top of the list.

<a id="june-29-2021-bug-fixes"></a>
#### Bug Fixes
* Fixed an issue where the full URL can be modified in the shortened URL edit screen.

<a id="may-25-2021"></a>
### May 25, 2021 { #may-25-2021 }

<a id="may-25-2021-feature-updates"></a>
#### Feature Updates
* Added a [Console] page feature
    * Added the page feature to View > URL screen.

<a id="april-27-2021"></a>
### April 27, 2021 { #april-27-2021 }

<a id="april-27-2021-new-service-release"></a>
#### New Service Release
* ShortURL allows you to share your website link with a shorter character length in a wide variety of environments where writing space is limited.
* RESTful API is provided to users for easy link with apps.
