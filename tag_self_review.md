# [TAG Self-Review Questionnaire: Security and Privacy](https://w3ctag.github.io/security-questionnaire/)


> 01.  What information does this feature expose, and for what purposes?

This feature allows SameSite=None cookies to be included in requests to the first party when third-party cookie (3PC) blocking is active. This information is currently available without 3PC Blocking. 
Since this is an opt-in feature the server can decide if the sandbox allow-same-site-none-cookies value would expose information to untrusted contexts. 
> 02.  Do features in your specification expose the minimum amount of information
>      necessary to implement the intended functionality?

Yes
> 03.  Do the features in your specification expose personal information,
>      personally-identifiable information (PII), or information derived from
>      either?

The SameSite=None cookies exposed could be part of authentication/session information and derived from PII but these would only be exposed to the first party.  
> 04.  How do the features in your specification deal with sensitive information?

N/A
> 05.  Does data exposed by your specification carry related but distinct
>      information that may not be obvious to users?

No, first-party information only. 
> 06.  Do the features in your specification introduce state
>      that persists across browsing sessions?

No, scoped to the life of a document. 
> 07.  Do the features in your specification expose information about the
>      underlying platform to origins?

No 
> 08.  Does this specification allow an origin to send data to the underlying
>      platform?

No
> 09.  Do features in this specification enable access to device sensors?

No
> 10.  Do features in this specification enable new script execution/loading
>      mechanisms?

No
> 11.  Do features in this specification allow an origin to access other devices?

No
> 12.  Do features in this specification allow an origin some measure of control over
>      a user agent's native UI?

No
> 13.  What temporary identifiers do the features in this specification create or
>      expose to the web?

N/A
> 14.  How does this specification distinguish between behavior in first-party and
>      third-party contexts?

The SameSite=None cookies we are exposing are only visible to the first party of sandboxed origins. They will continue to be filtered out of third-party contexts with 3PC blocking
> 15.  How do the features in this specification work in the context of a browser’s
>      Private Browsing or Incognito mode?

No effect. 
> 16.  Does this specification have both "Security Considerations" and "Privacy
>      Considerations" sections?

The explainer has a combined Security and Privacy Considerations section that covers both. 
> 17.  Do features in your specification enable origins to downgrade default
>      security protections?

No, this restores default behavior while maintaining the existing security protections when privacy-preserving restrictions are enabled. 
> 18.  What happens when a document that uses your feature is kept alive in BFCache
>      (instead of getting destroyed) after navigation, and potentially gets reused
>      on future navigations back to the document?

The CSP sandbox directive (including this value) is active for the lifetime of a document including if the document was kept alive the BFCache. 
Since the server would have had to send the allow-same-site-none-cookies value in a previous response to include these cookies and they are only being sent to the first-party site, this doesn't seem to be a large concern. 
> 19.  What happens when a document that uses your feature gets disconnected?

The Content-Security-Policy is delivered on the initial document load so the value would still remain in effect as the CSP is enforced by the browser’s security context. The cookies are stored in the browser and included on requests so a disconnected document wouldn't have access to the cookie store. 
> 20.  Does your feature allow sites to learn about the users use of assistive technology?

No
> 21.  What should this questionnaire have asked?

N/A
