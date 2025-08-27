| oRTB fieldComing from upstream request | oRTB fieldWhen sending requests to our bidders | Type / Example | Specs | Status | oRTB / SSPs / DSPs support & recommendation |
| --- | --- | --- | --- | --- | --- |
| id | id | string | Internally controlled - Unique uuid generated | Fully implemented | oRTB - Required |
| - | test | integer 0 or 1 | Internally controlled | Fully implemented | oRTB - Optional |
| - | at | integer 1 or 2 | Internally controlled | Fully implemented | oRTB - Optional |
| tmax | tmax | integer | Default min 100ms, max 500ms. | Fully implemented | oRTB - Optional |
| - | wseat | string[] | Internally controlled | Fully implemented | oRTB - Optional |
| - | cur | string[] ISO-4217 alpha codes | Internally controlled - floor price is always expressed in USD. | Fully implemented | oRTB - Optional |
| bcat | bcat | string[] | Blocked categories come from blocklists in DMX. If we receive non-empty bcat from oRTB upstream, we use it instead | Fully implemented | oRTB - Optional |
| cattax | cattax | integer | Follow oRTB spec | Fully implemented | oRTB - Optional |
| badv | badv | string[] List of domains (eg: ford.com) | Blocked advertisers come from blocklists in DMX. If we receive non-empty badv from oRTB upstream, we use it instead | Fully implemented | oRTB - Optional |
| imp |  |  |  |  | oRTB - Required |
| imp[].id | imp[].id | string | Follows oRTB spec. | Fully implemented | oRTB - Required |
| imp[].tagid | imp[].tagid | string | -- | Fully implemented | oRTB - Optional |
| imp[].displaymanager | imp[].displaymanager | string | Follows oRTB spec. | Fully implemented | oRTB - Recommended |
| imp[].displaymanagerver | imp[].displaymanagerver | string | Follows oRTB spec. | Fully implemented | oRTB - Recommended |
| imp[].bidfloor | imp[].bidfloor | float | -- | Fully implemented | oRTB - Optional |
| imp[].bidfloorcur | imp[].bidfloorcur | string | Important: Note that we can only bid if we support the currency that is sent to us. | Fully implemented | oRTB - Optional |
| imp[].clickbrowser | imp[].clickbrowser | integer 0 for embedded 1 for native | Follows oRTB spec. | Fully implemented | oRTB - Optional |
| imp[].secure | imp[].secure | integer 0 or 1 | Follows oRTB spec. | Fully implemented | oRTB - Optional |
| imp[].rwdd | imp[].rwdd | integer 0 or 1 | Follows oRTB spec. | Not Implemented | oRTB - Optional |
| imp[].instl | imp[].instl | integer | Follows oRTB spec | Not Implemented | oRTB - Recommended |
| imp[].ext |  |  | Can be extended through bidder feature imp.ext |  | - |
| imp[].{audio\|video} |  |  | Today we can bid for video or audio inventory. In the event where we receive an audio placement through oRTB to bid on, only audio bidders would be eligible. In the event where we receive a video placement through oRTB, we would look at mimetypes to see if audio bidders can be included. | Fully implemented | oRTB - Required |
| imp[].{video\|audio}.mimes | imp[].{video\|audio}.mimes | string[] | Follows oRTB spec. We append VPAID mimetypes ("application/javascript", "application/x-javascript", "text/javascript") if ever we have VPAID support. | Fully implemented | oRTB - Required |
| imp[].{video\|audio}.minduration | imp[].{video\|audio}.minduration | integer | Follows oRTB spec. Fallbacks to 0 if not defined.| Fully implemented | oRTB - Recommended |
| imp[].{video\|audio}.maxduration | imp[].{video\|audio}.maxduration | integer | -- | Fully implemented | oRTB - Recommended |
| imp[].{video\|audio}.protocols | imp[].{video\|audio}.protocols | integer[] | Follows oRTB spec. | Fully implemented | oRTB - Recommended |
| imp[].{video\|audio}.startdelay | imp[].{video\|audio}.startdelay | integer | Follows oRTB spec. | Fully implemented | oRTB - Recommended |
| imp[].{video\|audio}.battr | imp[].{video\|audio}.battr | integer[] | Follows oRTB spec. | Fully implemented | oRTB - Optional |
| imp[].{video\|audio}.delivery | imp[].{video\|audio}.delivery | integer[] | Follows oRTB spec. Note that we will only support 1 or 2 as our creatives won’t be downloadable. | Fully implemented | oRTB - Optional |
| imp[].{video\|audio}.api | imp[].{video\|audio}.api | integer[] | Follows oRTB spec. | Fully implemented | oRTB - Optional |
| imp[].video.sequence | imp[].video.sequence | integer | If multiple ad impressions are offered in the same bid request, the sequence number allows for the coordinated delivery of multiple creatives. The default value is 1. | Not implemented | oRTB - Optional |
| imp[].video.rqddurs | imp[].video.rqddurs | integer[] | An array of precise, acceptable durations (in seconds) for video creatives. This field specifically targets the live TV use case where non-exact ad durations would result in undesirable ‘dead air.’ If specified, this field takes precedence if the minduration and maxduration values are also present in the request. | Not implemented | oRTB - Optional (CTV) |
| imp[].video.placement | imp[].video.placement | integer | Follows oRTB spec. | Fully implemented | oRTB - Recommended |
| imp[].video.plcmt | imp[].video.plcmt | integer | Follows oRTB spec. | Fully implemented | oRTB - Optional |
| imp[].video.w | imp[].video.w | integer | Follows oRTB spec. | Fully implemented. Do not send for audio bids | oRTB - Recommended |
| imp[].video.h | imp[].video.h | integer | Follows oRTB spec. | Fully implemented. Do not send for audio bids | oRTB - Recommended |
| imp[].video.pos | imp[].video.pos | integer | Follows oRTB spec. | Fully implemented. Launch A/B test to verify we can rely exclusively on upstream & do not send for audio bids | oRTB - Optional |
| imp[].video.linearity | imp[].video.linearity | integer | Follows oRTB spec. | Fully implemented. Do not send for audio bids | oRTB - Optional |
| imp[].video.minbitrate | imp[].video.minbitrate | integer | The minimum bit rate in Kbps. We us this parameter to select a video creative that contains at least one media file that falls within the bit rate range. | Not implemented | oRTB - Optional |
| imp[].video.maxbitrate | imp[].video.maxbitrate | integer | The maximum bit rate in Kbps. We us this parameter to select a video creative that contains at least one media file that falls within the bit rate range. | Not implemented | oRTB - Optional |
| imp[].video.skip | imp[].video.skip | integer 0 or 1 | Follows oRTB spec. If no value is defined, we fallback to our skip values. | Fully implemented. Do not send for audio bids | oRTB - Optional |
| imp[].video.skipafter | imp[].video.skipafter | integer | Follows oRTB spec. If no value is defined in oRTB, we fallback to our skip values. | Fully implemented. Do not send for audio bids | oRTB - Optional |
| imp[].video.playbackmethod | imp[].video.playbackmethod | integer[] | Follows oRTB spec. | Fully implementedDo not send for audio bids | oRTB - Optional |
| imp[].video.ext |  |  | Can be extended through bidder feature imp.video.ext |  | - |
| imp[].video.ext.videoindex | - | integer | Indicates the video view count of current user session. | Fully implemented | - |
| imp[].video.ext.realautoplay | - | integer 0 or 1 | Indicates if the video player is in autoplay mode. | Fully implemented | - |
| {site\|app} |  |  |  |  | oRTB - Recommended |
| - | {site\|app}.id | string | As per oRTB spec, these represent Exchange specific identifiers | Fully implemented | oRTB - Recommended |
| {site\|app}.name | {site\|app}.name | string | -- | Fully implemented | oRTB - Optional |
| {site\|app}.domain | {site\|app}.domain | string | -- | Fully implemented | oRTB - Optional |
| site.page | site.page | string | -- | Fully implemented | oRTB - Optional |
| app.storeurl | Yes | string | For IOS, ios app store id, prefixed with https://apps.apple.com/us/app/idapp.bundle prefixed with https://play.google.com/store/apps/details?id= | Fully implemented | oRTB - Optional (CTV) |
| app.bundle | app.bundle | string | -- | Fully implemented | oRTB - Recommended |
| {site\|app}.cat | {site\|app}.cat | string[] IAB v1 categories | Note that no matter the version of IAB cats we receive, we always give the IAB v1 equivalent to our bidders (if we can map >= v2 to v1) | Fully implemented | oRTB - Optional |
| {site\|app}.cattax | {site\|app}.cattax | integer | Follows oRTB specIf {site\|app}.cat doesn’t come from oRTB, we use cattax 1 | Fully implemented | oRTB - Optional |
| {site\|app}.keywords | {site\|app}.keywords | string Comma-separated string | -- | Fully implemented | oRTB - Optional |
| {site\|app}.ext.inventorypartnerdomain | {site\|app}.ext.inventorypartnerdomain | object | See https://support.google.com/admanager/answer/12077899?hl=en | Not Implemented | oRTB - Optional |
| {site\|app}.ext | {site\|app}.ext | object | Fully controlled through bidder feature {site\|app}.ext | Fully implemented | oRTB - Optional |
| {site\|app}.publisher |  |  |  |  | oRTB - Required (app) |
| {site\|app}.publisher.id | Yes | string | Comes from our system, fallbacks to oRTB request. | Fully implemented | oRTB - Recommended |
| {site\|app}.publisher.name | Yes | string |Comes from our system, fallbacks to oRTB. | Fully implemented | oRTB - Optional |
| {site\|app}.publisher.ext | {site\|app}.publisher.ext | object | Fully controlled through bidder feature publisher.ext | Fully implemented | - |
| {site\|app}.content |  |  |  |  | oRTB - Optional |
| {site\|app}.content.id | {site\|app}.content.id (if {site\|app}.content.ext.dm.xid has no value) | string | Follows oRTB spec | Fully implemented | oRTB - Optional |
| {site\|app}.content.title | {site\|app}.content.title | string | Follows oRTB spec | Fully implemented | oRTB - Optional |
| {site\|app}.content.url | {site\|app}.content.url | string | Follows oRTB spec | Fully implemented | oRTB - Optional |
| {site\|app}.content.cat | {site\|app}.content.cat | string[] | Note that no matter the version of IAB cats we receive, we always give the IAB v1 equivalent to our bidders (if we can map >= v2 to v1) | Fully implemented | oRTB - Optional (CTV) |
| {site\|app}.content.cattax | {site\|app}.content.cattax | integer We support 1, 2, 5 and 6 | Follows oRTB spec | Fully implemented | oRTB - Optional |
| {site\|app}.content.language | {site\|app}.content.language | string Example: fr | Follows oRTB spec | Fully implemented | oRTB - Optional |
| {site\|app}.content.context | {site\|app}.content.context | integer | Yes Hardcoded to 1 | Follows oRTB spec | Fully implemented | oRTB - Optional |
| {site\|app}.content.livestream | {site\|app}.content.livestream | integer 0 or 1 | Follows oRTB spec | Fully implemented | oRTB - Optional |
| {site\|app}.content.len | {site\|app}.content.len | integer | Follows oRTB spec | Fully implemented | oRTB - Optional |
| {site\|app}.content.keywords | {site\|app}.content.keywords | string Comma separated per keyword | Follows oRTB spec | Fully implemented | oRTB - Optional |
| {site\|app}.content.episode | {site\|app}.content.episode | integer | Follows oRTB spec | Fully implemented | oRTB - Optional (CTV) |
| {site\|app}.content.series | {site\|app}.content.series | string | Follows oRTB spec | Fully implemented | oRTB - Optional |
| {site\|app}.content.artist | {site\|app}.content.artist | string | Follows oRTB spec | Fully implemented | oRTB - Optional (CTV) |
| {site\|app}.content.genre | {site\|app}.content.genre | string | Follows oRTB spec | Fully implemented | oRTB - Optional |
| {site\|app}.content.season | {site\|app}.content.season | string | Follows oRTB spec | Fully implemented | oRTB - Optional (CTV) |
| {site\|app}.content.contentrating | {site\|app}.content.contentrating | string | Follows oRTB spec Note from DV360: Recommended for Audio & Video/CTV, as we will start decisioning on this attribute. | Fully implemented - __Not read / sent__ | oRTB - Optional |
| {site\|app}.content.network | {site\|app}.content.network | object | Follows oRTB spec | Fully implemented | oRTB - Optional (CTV) |
| {site\|app}.content.channel | {site\|app}.content.channel | object | Follows oRTB spec | Fully implemented | oRTB - Optional (CTV) |
| {site\|app}.content.prodq | {site\|app}.content.prodq | integer | Follows oRTB spec | Not Implemented | oRTB - Optional |
| {site\|app}.content.ext.dm |  |  |  |  | - |
| {site\|app}.content.ext.dm.iscreatedforkids | - | integer 0 or 1 | Used to evaluate likeliness of user being a child (for privacy purposes) | Fully implemented | - |
| {site\|app}.content.ext.dm.detectedlang | - | string Example: fr | Used in condition matching | Fully implemented | - |
| device |  |  |  |  | oRTB - Recommended |
| device.ua | device.ua | string | UA string comes from HTTP header in all cases | Fully implemented | oRTB - Recommended |
| device.ip | device.ip | string | IP comes from HTTP remote address (or x-forwarded-for) in all cases | Fully implemented | oRTB - Recommended |
| - | device.ipv6 | string | Not sending for now | Not implemented | oRTB - Optional |
| device.devicetype | device.devicetype | integer | -- | Fully implemented | oRTB - Optional |
| device.make | device.make | string Example: Apple | Derived from user agent or fallbacks to oRTB value if sent | Fully implemented | oRTB - Optional |
| device.model | device.model | string Example: Macbook Pro | Derived from user agent or fallbacks to oRTB value if sent | Fully implemented | oRTB - Optional |
| device.os | device.os | string Example: Mac OS X | Derived from user agent or fallbacks to oRTB value if sent | Fully implemented | oRTB - Optional |
| device.osv | device.osv | string Example: 10.15.7 | Derived from user agent or fallbacks to oRTB value if sent | Fully implemented | oRTB - Optional |
| device.language | device.language | string Example: fr | Follows oRTB spec | Fully implemented | oRTB - Optional |
| device.ifa | device.ifa | string | Follows oRTB spec | Fully implemented | oRTB - Optional |
| device.ext.ifa_typedevice.ifa_type | device.ext.ifa_typedevice.ifa_type | string | Follows oRTB spec | Fully implemented | oRTB - Recommended (Required CTV) |
| device.lmt | device.lmt | integer0 or 1 | Follows oRTB spec Defaults to 0 if no value is sent from upstream | Fully implemented | oRTB - Recommended |
| device.dnt | device.dnt | integer 0 or 1 | The standard "Do Not Track" flag set in the header by the browser:0 (tracking is unrestricted) 1 (do not track) | Not Implemented | oRTB - Recommended |
| device.geo | device.geo |  |  |  | oRTB - Recommended |
| device.geo.country | device.geo.country | string Example: FRA | Derived from IP or fallbacks to oRTB value if sent | Fully implemented | oRTB - Optional |
| device.geo.region | device.geo.region | string Example: IDF | Derived from IP or fallbacks to oRTB value if sent | Fully implemented | oRTB - Optional |
| device.geo.metro | device.geo.metro | string Google Geo metro codes Example: 1006094 for Paris | Derived from IP or fallbacks to oRTB value if sent | Fully implemented | oRTB - Optional |
| device.geo.city | device.geo.city | string Example: Paris | Derived from IP or fallbacks to oRTB value if sent | Fully implemented | oRTB - Optional |
| device.geo.zip | device.geo.zip | string Example: 75017 | Derived from IP or fallbacks to oRTB value if sent | Fully implemented | oRTB - Optional |
| device.geo.ext |  |  |  |  | - |
| device.geo.ext.asnum | - | string Example: AS41690 | Derived from IP or fallbacks to oRTB value if sent Unused field | Fully implemented | - |
| device.ext |  |  |  |  | oRTB - Optional |
| device.ext.atts | device.ext.atts | integer One of 0, 1, 2, 3 | Follows oRTB spec | Fully implemented | oRTB - Optional |
| user |  |  |  |  | oRTB - Recommended |
| user.buyeruid | user.buyeruid | string | -- | Fully implemented | oRTB - Recommended |
| user.yob | - | integer | Used to assess if viewer is likely a child. | Fully implemented | oRTB - Optional |
| user.consent | user.consentuser.ext.consent | string | GDPR consent string We transmit this signal to bidders no matter what | Fully implemented | oRTB - Optional |
| user.eidsuser.ext.eids | user.eidsuser.ext.eids | oRTB eids objects | -- | Fully implemented | oRTB - Optional |
| user.gender | user.gender | string | Follows oRTB specPersonal data | Not Implemented | oRTB - Optional |
| user.ext |  |  |  |  | oRTB - Optional |
| source |  |  |  |  | oRTB - Optional |
| source.fd | source.fd | integer | If we receive source.fd from upstream we apply it. In all cases, we fallback to 0. | Fully implemented | oRTB - Recommended |
| source.ext |  |  |  |  | oRTB - Required |
| source.ext.omidpn | source.ext.omidpn | string | OMID partner nameRequired to inject AdVerification script | Fully implemented | oRTB - Recommended |
| source.ext.omidpn | source.ext.omidpv | string | OMID partner version | Fully implemented | oRTB - Recommended |
| source.schainsource.ext.schain |  |  | We currently send out this hardcoded schain object to all our bidders. When receiving it from the upstream oRTB request, we will merge the nodes we receive with our own hardcoded one to represent the full supply chain. |  | oRTB - Recommended |
| source.ext.schain.ver | source.ext.schain.ver | string | Only read object if schain spec version is 1.0 | Fully implemented | oRTB - Required |
| source.ext.schain.complete | source.ext.schain.complete | integer 0 or 1 | The upstream determines schain completeness.Eg: If incomplete (0), even when DMX adds its own schain node, we keep it as incomplete. If noted as complete from upstream, we add our own node and mark as complete. | Fully implemented | oRTB - Required |
| source.ext.schain.nodes[].asi | source.ext.schain.nodes[].asi | string | Follows IAB spec | Fully implemented | oRTB - Required |
| source.ext.schain.nodes[].sid | source.ext.schain.nodes[].sid | string | Follows IAB spec | Fully implemented | oRTB - Required |
| source.ext.schain.nodes[].hp | source.ext.schain.nodes[].hp | integer | Follows IAB spec | Fully implemented | oRTB - Required |
| source.ext.schain.nodes[].pid | source.ext.schain.nodes[].pid | string | Follows IAB spec | Not Implemented | oRTB - Optional |
| source.ext.schain.nodes[].domain | source.ext.schain.nodes[].domain | string | Follows IAB spec | Not Implemented | oRTB - Optional |
| source.ext.schain.nodes[].name | source.ext.schain.nodes[].name | string | Follows IAB spec | Not Implemented | oRTB - Optional |
| source.ext.schain.nodes[].rid | source.ext.schain.nodes[].rid | string | Follows IAB spec | Not Implemented | oRTB - Optional |
| source.ext.sspname | - | string | Determines name of SSP calling us. | Fully implemented | N/A |
| regs |  |  |  |  | oRTB - Optional |
| regs.coppa | regs.coppa | integer 0 or 1 | Coppa is set to 1 when one of the following conditions is true:It is sent from the upstream Or for a user is younger than 16 (based on user.yob) Or when content is created for kids (see {site\|app}.content.ext.dm.iscreatedforkids) | Fully implemented | oRTB - Optional |
| regs.gpp | regs.gpp | string | -- | Fully implemented | oRTB - Optional |
| regs.gpp_sid | regs.gpp_sid | integer[] | -- | Fully implemented | oRTB - Optional |
| regs.gdpr | regs.gdprregs.ext.gdpr | integer 0 or 1 | Follows oRTB spec If we do not receive any value, we would check the country of the user (via device.geo.country). If the user is in a GDPR country, we will set this flag to 1. | Fully implemented | oRTB - Optional |
| regs.ext.dsa |  |  | This object is only sent when on gdpr context. |  | oRTB - Optional |
| regs.ext.dsa.dsarequired | regs.ext.dsa.dsarequired | integer One of 0, 1, 2, 3 | -- | Fully implemented | oRTB - Optional |
| regs.ext.dsa.pubrender | regs.ext.dsa.pubrender | integer One of 0, 1, 2 | -- | Fully implemented | oRTB - Optional |
| regs.ext.dsa.datatopub | regs.ext.dsa.datatopub | integer One of 0, 1, 2 | -- | Fully implemented | oRTB - Optional |
| regs.ext.dsa.transparency[].domain | regs.ext.dsa.transparency[].domain | string | -- | Fully implemented | oRTB - Optional |
| regs.ext.dsa.transparency[].dsaparams | regs.ext.dsa.transparency[].dsaparams | integer[] | -- | Fully implemented | oRTB - Optional |
| regs.ext.dm |  |  |  |  | - |
| ext |  |  | Unless specified, these fields are used exclusively in the context of Dailymotion requests. The oRTB spec is extended here to make sure each AdRequest field has an equivalent.These fields may be deprecated in the future if they are considered redundant or if they are not used. |  | - |
| ext.ivv | - | integer 0 or 1 | Determines player support of ivv (in video vertical) | Fully implemented | - |
| ext.utm |  |  |  |  |  |  |  |  | - |
| ext.utm.campaign | - | string | UTM parameter - designates marketing campaign | Fully implemented | - |
| ext.utm.medium | - | string | UTM parameter - designates channel the traffic comes from (eg: email campaign, display campaign) | Fully implemented | - |
| ext.utm.source | - | string | UTM parameter - designates source of traffic (eg: twitter) | Fully implemented | - |
| ext.utm.term | - | string | UTM parameter - designates keywords | Fully implemented | - |
| ext.player |  |  |  |  | - |
| ext.player.name | - | string | Player name, used to verify if we are within Dailymotion player context or not. | Fully implemented | - |
| ext.player.volume | - | integer Between 0 and 10 | Volume of the player at the moment of the request. | Fully implemented | - |