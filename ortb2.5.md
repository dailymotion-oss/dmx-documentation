| oRTB field coming from upstream request | Type / Example | Specs | Recommendation |
| --- | --- | --- | --- |
| id | string | Internally controlled - Unique uuid generated | Required |
| tmax  | integer | Default min 100ms, max 500ms. | Optional |
| bcat | string[] | Blocked categories | Optional |
|cattax | integer | Follow oRTB spec | Optional |
| badv | string[] List of domains (eg: ford.com) | Blocked advertisers | Optional |
| imp |  |  | Required |
| imp[].id | string | Follows oRTB spec. | Required |
| imp[].tagid | string | -- | Optional |
| imp[].displaymanager | string | Follows oRTB spec. | Recommended |
| imp[].displaymanagerver | string | Follows oRTB spec. | Recommended |
| imp[].bidfloor | float | -- | Optional |
| imp[].bidfloorcur | string | Important: Note that we can only bid if we support the currency that is sent to us. | Optional |
| imp[].clickbrowser | integer 0 for embedded 1 for native | Follows oRTB spec. | Optional |
| imp[].secure | integer 0 or 1 | Follows oRTB spec. | Optional |
| imp[].{audio\|video} |  | We can bid for video or audio inventory. In the event where we receive an audio placement through oRTB to bid on, only audio bidders would be eligible. In the event where we receive a video placement through oRTB, we would look at mimetypes to see if audio bidders can be included. | Required |
| imp[].{video\|audio}.mimes | string[] | Follows oRTB spec. We append VPAID mimetypes ("application/javascript", "application/x-javascript", "text/javascript") if ever we have VPAID support. | Required |
| imp[].{video\|audio}.minduration | integer | Follows oRTB spec. Fallbacks to 0 if not defined.| Recommended |
| imp[].{video\|audio}.maxduration | integer | -- | Recommended |
| imp[].{video\|audio}.protocols | integer[] | Follows oRTB spec. | Recommended |
| imp[].{video\|audio}.startdelay | integer | Follows oRTB spec. | Recommended |
| imp[].{video\|audio}.battr | integer[] | Follows oRTB spec. | Optional |
| imp[].{video\|audio}.delivery | integer[] | Follows oRTB spec. Note that we will only support 1 or 2 as our creatives won’t be downloadable. | Optional |
| imp[].{video\|audio}.api | integer[] | Follows oRTB spec. | Optional |
| imp[].video.placement | integer | Follows oRTB spec. | Recommended |
| imp[].video.plcmt | integer | Follows oRTB spec. | Optional |
| imp[].video.w | integer | Follows oRTB spec. | Recommended |
| imp[].video.h | integer | Follows oRTB spec. | Recommended |
| imp[].video.pos | integer | Follows oRTB spec. | Optional |
| imp[].video.linearity | integer | Follows oRTB spec. | Optional |
| imp[].video.skip | integer 0 or 1 | Follows oRTB spec. If no value is defined, we fallback to our skip values. | Optional |
| imp[].video.skipafter | integer | Follows oRTB spec. If no value is defined in oRTB, we fallback to our skip values. | Optional |
 | imp[].video.playbackmethod | integer[] | Follows oRTB spec. | Optional |
| {site\|app} |  |  | Recommended |
| {site\|app}.name | string | -- | Optional |
| {site\|app}.domain | string | -- | Optional |
| site.page | string | -- | Optional |
| app.storeurl | string | For IOS, ios app store id, prefixed with https://apps.apple.com/us/app/idapp.bundle prefixed with https://play.google.com/store/apps/details?id= | Optional (CTV) |
| app.bundle | string | -- | Recommended |
| {site\|app}.cat | string[] IAB v1 categories | Note that no matter the version of IAB cats we receive, we always give the IAB v1 equivalent to our bidders (if we can map >= v2 to v1) | Optional |
| {site\|app}.cattax | integer | Follows oRTB specIf {site\|app}.cat doesn’t come from oRTB, we use cattax 1 | Optional |
| {site\|app}.keywords | string Comma-separated string | -- | Optional |
| {site\|app}.publisher |  |  | Required (app) |
| {site\|app}.publisher.id | string | Comes from our system, fallbacks to oRTB request. | Recommended |
| {site\|app}.publisher.name | string |Comes from our system, fallbacks to oRTB. | Optional |
| {site\|app}.publisher.ext | object | Fully controlled through bidder feature publisher.ext | - |
| {site\|app}.content |  |  | Optional |
| {site\|app}.content.id | string | Follows oRTB spec | Optional |
| {site\|app}.content.title | string | Follows oRTB spec | Optional |
| {site\|app}.content.url | string | Follows oRTB spec | Optional |
| {site\|app}.content.cat | string[] | Note that no matter the version of IAB cats we receive, we always give the IAB v1 equivalent to our bidders (if we can map >= v2 to v1) | Optional (CTV) |
| {site\|app}.content.cattax | integer We support 1, 2, 5 and 6 | Follows oRTB spec | Optional |
| {site\|app}.content.language | string Example: fr | Follows oRTB spec | Optional |
| {site\|app}.content.context | integer | Follows oRTB spec | Optional |
| {site\|app}.content.livestream | integer 0 or 1 | Follows oRTB spec | Optional |
| {site\|app}.content.len | integer | Follows oRTB spec | Optional |
| {site\|app}.content.keywords | string Comma separated per keyword | Follows oRTB spec | Optional |
| {site\|app}.content.episode | integer | Follows oRTB spec | Optional (CTV) |
| {site\|app}.content.series | string | Follows oRTB spec | Optional |
| {site\|app}.content.artist | string | Follows oRTB spec | Optional (CTV) |
| {site\|app}.content.genre | string | Follows oRTB spec | Optional |
| {site\|app}.content.season | string | Follows oRTB spec | Optional (CTV) |
| {site\|app}.content.contentrating | string | Follows oRTB spec Note from DV360: Recommended for Audio & Video/CTV, as we will start decisioning on this attribute. | Optional |
| {site\|app}.content.network | object | Follows oRTB spec | Optional (CTV) |
| {site\|app}.content.channel | object | Follows oRTB spec | Optional (CTV) |
| {site\|app}.content.ext.dm |  |  | - |
| {site\|app}.content.ext.dm.iscreatedforkids | integer 0 or 1 | Used to evaluate likeliness of user being a child (for privacy purposes) | - |
| {site\|app}.content.ext.dm.detectedlang | string Example: fr | Used in condition matching | - |
| device |  |  | Recommended |
| device.ua | string | UA string comes from HTTP header in all cases | Recommended |
| device.ip | string | IP comes from HTTP remote address (or x-forwarded-for) in all cases | Recommended |
| device.devicetype | integer | -- | Optional |
| device.make | string Example: Apple | Derived from user agent or fallbacks to oRTB value if sent | Optional |
| device.model | string Example: Macbook Pro | Derived from user agent or fallbacks to oRTB value if sent | Optional |
| device.os | string Example: Mac OS X | Derived from user agent or fallbacks to oRTB value if sent | Optional |
| device.osv | string Example: 10.15.7 | Derived from user agent or fallbacks to oRTB value if sent | Optional |
| device.language | string Example: fr | Follows oRTB spec | Optional |
| device.ifa | string | Follows oRTB spec | Optional |
| device.ext.ifa_typedevice.ifa_type | string | Follows oRTB spec | Recommended (Required CTV) |
| device.lmt | integer0 or 1 | Follows oRTB spec Defaults to 0 if no value is sent from upstream | Recommended |
| device.geo |  |  | Recommended |
| device.geo.country | string Example: FRA | Derived from IP or fallbacks to oRTB value if sent | Optional |
| device.geo.region | string Example: IDF | Derived from IP or fallbacks to oRTB value if sent | Optional |
| device.geo.metro | string Google Geo metro codes Example: 1006094 for Paris | Derived from IP or fallbacks to oRTB value if sent | Optional |
| device.geo.city | string Example: Paris | Derived from IP or fallbacks to oRTB value if sent | Optional |
| device.geo.zip | string Example: 75017 | Derived from IP or fallbacks to oRTB value if sent | Optional |
| device.geo.ext |  |  | - |
| device.geo.ext.asnum | string Example: AS41690 | Derived from IP or fallbacks to oRTB value if sent Unused field | - |
| device.ext |  |  | Optional |
| device.ext.atts | integer One of 0, 1, 2, 3 | Follows oRTB spec | Optional |
| user |  |  | Recommended |
| user.buyeruid | string | -- | Recommended |
| user.yob | integer | Used to assess if viewer is likely a child. | Optional |
| user.consent | string | GDPR consent string We transmit this signal to bidders no matter what | Optional |
| user.ext.eids | oRTB eids objects | -- | Optional |
| user.ext |   |  | Optional |
| source |  |  | Optional |
| source.fd | integer | If we receive source.fd from upstream we apply it. In all cases, we fallback to 0. | Recommended |
| source.ext |  |  | Required |
| source.ext.omidpn | string | OMID partner nameRequired to inject AdVerification script | Recommended |
| source.ext.omidpv | string | OMID partner version | Recommended |
| source.schainsource.ext.schain |  |  | Recommended |
| source.ext.schain.ver | string | Only read object if schain spec version is 1.0 | Required |
| source.ext.schain.complete | integer 0 or 1 | The upstream determines schain completeness.Eg: If incomplete (0), even when DMX adds its own schain node, we keep it as incomplete. If noted as complete from upstream, we add our own node and mark as complete. | Required |
| source.ext.schain.nodes[].asi | string | Follows IAB spec | Required |
| source.ext.schain.nodes[].sid | string | Follows IAB spec | Required |
| source.ext.schain.nodes[].hp | integer | Follows IAB spec | Required |
| source.ext.sspname | string | Determines name of SSP calling us. | N/A |
| regs |  |  | Optional |
| regs.coppa | integer 0 or 1 | Coppa is set to 1 when one of the following conditions is true:It is sent from the upstream Or for a user is younger than 16 (based on user.yob) Or when content is created for kids (see {site\|app}.content.ext.dm.iscreatedforkids) | Optional |
| regs.gpp | string | -- | Optional |
| regs.gpp_sid | integer[] | -- | Optional |
| regs.gdpr | integer 0 or 1 | Follows oRTB spec If we do not receive any value, we would check the country of the user (via device.geo.country). If the user is in a GDPR country, we will set this flag to 1. | Optional |
| regs.ext.dsa |  | This object is only sent when on gdpr context. | Optional |
| regs.ext.dsa.dsarequired | integer One of 0, 1, 2, 3 | -- | Optional |
| regs.ext.dsa.pubrender | integer One of 0, 1, 2 | -- | Optional |
| regs.ext.dsa.datatopub | integer One of 0, 1, 2 | -- | Optional |
| regs.ext.dsa.transparency[].domain | string | -- | Optional |
| regs.ext.dsa.transparency[].dsaparams | integer[] | -- | Optional |