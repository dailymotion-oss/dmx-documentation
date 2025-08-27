| oRTB field coming from upstream request | Type / Example | Specs | Recommendation |
| --- | --- | --- | --- |
| id | string | Unique ID of the bid request. | Required |
| tmax  | integer | Maximum time in milliseconds the exchange allows for bids to be received including Internet latency to avoid timeout. Minimum value is 100ms, maximum 500ms. | Optional |
| bcat | string[] | Blocked advertiser categories using the IAB content categories. | Optional |
| cattax | integer | The taxonomy in use for bcat. Refer to the AdCOM List: Category Taxonomies for values. | Optional |
| badv | string[] - List of domains (eg: brand.com) | Specify the blocked advertiser based on the domain provided by the advertiser. | Optional |
| imp | object[] | Ad placement or impression being auctioned. | Required |
| imp[].id | string | A unique identifier for this impression within the content of the bid request (typically, starts with 1 and increments). | Required |
| imp[].tagid | string | Identifier for specific ad placement or ad tag that was used to initiate the auction. This can be useful for debugging of any issues, or for optimization by the buyer. | Optional |
| imp[].displaymanager | string | Name of ad mediation partner, SDK technology, or player responsible for rendering ad (typically video or mobile). Used by some ad servers to customize ad code by partner. Recommended for video and/or apps. | Recommended |
| imp[].displaymanagerver | string | Version of ad mediation partner, SDK technology, or player responsible for rendering ad (typically video or mobile). Used by some ad servers to customize ad code by partner. Recommended for video and/or apps. | Recommended |
| imp[].bidfloor | float | Minimum bid for this impression expressed in CPM. | Optional |
| imp[].bidfloorcur | string | Currency specified using ISO-4217 alpha codes. We support USD, EUR, GBP, AUD, CAD, JPY. | Optional |
| imp[].clickbrowser | integer - 0 for embedded 1 for native | Indicates the type of browser opened upon clicking the creative in an app. | Optional |
| imp[].secure | integer - 0 for non-secure or 1 for secure | Flag to indicate if the impression requires secure HTTPS URL creative assets and markup. | Optional |
| imp[].{audio\|video} | object | We can bid for video or audio inventory. In the event where we receive an audio placement through oRTB to bid on, only audio bidders would be eligible. In the event where we receive a video placement through oRTB, we would look at mimetypes to see if audio bidders can be included. | Required |
| imp[].{video\|audio}.mimes | string[] | Content MIME types supported. | Required |
| imp[].{video\|audio}.minduration | integer | Minimum video ad duration in seconds. Fallbacks to 0 if not defined.| Recommended |
| imp[].{video\|audio}.maxduration | integer | Maximum video ad duration in seconds. | Recommended |
| imp[].{video\|audio}.protocols | integer[] | Array of supported video protocols. Refer to List: Creative Substypes - Audio/Video in AdCOM 1.0. | Recommended |
| imp[].{video\|audio}.startdelay | integer | Indicates the start delay in seconds for pre-roll, mid-roll, or post-roll ad placements. Refer to List: Start Delay Modes in AdCOM 1.0. | Recommended |
| imp[].{video\|audio}.battr | integer[] | Blocked creative attributes. Refer to List: Creative Attributes in AdCOM 1.0. | Optional |
| imp[].{video\|audio}.delivery | integer[] | Supported delivery methods (e.g., streaming, progressive). If none specified, assume all are supported. Refer to List: Delivery Methods in AdCOM 1.0. Note that we will only support 1 or 2 as our creatives are not downloadable. | Optional |
| imp[].{video\|audio}.api | integer[] | List of supported API frameworks for this impression. Refer to List: API Frameworks in AdCOM 1.0. If an API is not explicitly listed, it is assumed not to be supported. | Optional |
| imp[].video.placement | integer | Placement type for the impression. Considering deprecation as of OpenRTB 2.6-202303, please use plcmt instead. | Optional |
| imp[].video.plcmt | integer | Video placement type for the impression. Refer to List: Plcmt Subtypes - Video in AdCOM 1.0. | Optional |
| imp[].video.w | integer | Width of the video player in device-independent pixels (DIPS). | Recommended |
| imp[].video.h | integer | Height of the video player in device-independent pixels (DIPS). | Recommended |
| imp[].video.pos | integer | Ad position on screen. Refer to List: Placement Positions in AdCOM 1.0. | Optional |
| imp[].video.linearity | integer | Indicates if the impression must be linear (in-stream) or nonlinear (overlay). Refer to List: Video Linearity Modes in AdCOM 1.0. | Optional |
| imp[].video.minbitrate | integer | Minimum bit rate in Kbps. | Optional |
| imp[].video.maxbitrate | integer | Maximum bit rate in Kbps. | Optional |
| imp[].video.skip | integer | Indicates if the player will allow the video to be skipped (0 = no, 1 = yes). | Optional |
| imp[].video.skipafter | integer | Number of seconds a video must play before skipping is enabled. Only applicable if `skip = 1`. | Optional |
| imp[].video.playbackmethod | integer[] | Supported playback methods. If none specified, assume all are supported. Refer to List: Playback Methods in AdCOM 1.0. | Optional |
| imp[].video.ext | object | Exchange-specific extensions. | Optional |
| imp[].video.ext.videoindex | integer | Indicates the video view count of current user session. | Recommended |
| imp[].video.ext.realautoplay | integer | Indicates if the video player is in autoplay mode. | Recommended |
| {site\|app} | object | Site or App object describing the publisher’s content. Exactly one of Site or App must be included. | Recommended |
| {site\|app}.name | string | Site or app name (may be aliased). | Optional |
| {site\|app}.domain | string | Domain of the site (e.g., “mysite.foo.com”). | Optional |
| site.page | string | URL of the page where the impression will be shown. | Optional |
| app.storeurl | string | App store URL for an installed app (Google Play, iTunes). | Optional |
| app.bundle | string | Application bundle or package name (e.g., “com.foo.mygame”). | Recommended |
| {site\|app}.cat | string[] | Array of IAB content categories for the site or app. | Optional |
| {site\|app}.cattax | integer | The taxonomy in use for cat. Refer to AdCOM list Category Taxonomies. | Optional |
| {site\|app}.keywords | string | Comma separated list of keywords describing the site or app. | Optional |
| {site\|app}.publisher | object | Publisher object representing the publisher of the site or app. | Required (app) |
| {site\|app}.publisher.name | string | Publisher name (may be aliased). | Optional |
| {site\|app}.content | object | Details about the content in which the impression will appear. | Optional |
| {site\|app}.content.id | string | Unique identifier for the content. | Optional |
| {site\|app}.content.title | string | Content title (e.g., movie name). | Optional |
| {site\|app}.content.url | string | URL of the content, for buy-side contextualization or review. | Optional |
| {site\|app}.content.cat | string[] | Array of IAB categories describing the content. | Optional |
| {site\|app}.content.cattax | integer | The taxonomy in use for cat. Refer to AdCOM list Category Taxonomies. | Optional |
| {site\|app}.content.language | string | Content language using ISO-639-1-alpha-2. | Optional |
| {site\|app}.content.context | integer | Type of content (game, video, text, etc.). Refer to List: Content Contexts in AdCOM 1.0. | Optional |
| {site\|app}.content.livestream | integer | Indicator of live content (0 = not live, 1 = live). | Optional |
| {site\|app}.content.len | integer | Length of content in seconds. | Optional |
| {site\|app}.content.keywords | string | Comma separated list of keywords describing the content. | Optional |
| {site\|app}.content.episode | integer | Episode number. | Optional |
| {site\|app}.content.series | string | Content series. | Optional |
| {site\|app}.content.artist | string | Artist credited. | Optional |
| {site\|app}.content.genre | string | Genre that best describes content. | Optional |
| {site\|app}.content.season | string | Season in which content is released. | Optional |
| {site\|app}.content.contentrating | string | Content rating (e.g., PG, R). | Optional |
| {site\|app}.content.network | object | Network to which content belongs. | Optional |
| {site\|app}.content.channel | object | Channel to which content belongs. | Optional |
| {site\|app}.content.ext | object | Exchange-specific extensions. | Optional |
| {site\|app}.content.ext.description | string | Content description | Optional |
| {site\|app}.content.ext.dm.iscreatedforkids | integer - `0` or `1` | Set to `1` if the content has been created for kids as a primary audience. | Recommended |
| device | object | Device object providing information about the device through which the user is interacting. | Recommended |
| device.ua | string | Browser user agent string. | Recommended |
| device.ip | string | IPv4 address closest to device. | Recommended |
| device.devicetype | integer | Device type. Refer to List: Device Types in AdCOM 1.0. | Recommended |
| device.make | string | Device make (e.g., “Apple”). | Optional |
| device.model | string | Device model (e.g., “iPhone”). | Optional |
| device.os | string | Device operating system (e.g., “iOS”). | Optional |
| device.osv | string | Device operating system version (e.g., “3.1.2”). | Optional |
| device.language | string | Browser language using ISO-639-1-alpha-2. | Optional |
| device.ifa | string | Platform-specific identifier for advertising (if applicable). | Optional |
| device.ifa_type | string | Indicates the origin of the device.ifa field, whether it was provided from the device itself or generated by a publisher or Supplier in the supply chain. Takes the following values from the Guidelines for Identifier for Advertising (IFA) on CTV/OTT platforms. | Optional |
| device.lmt | integer | Limit Ad Tracking signal (0 = tracking is unrestricted, 1 = tracking must be limited). | Recommended |
| device.geo | object | Location of the device. | Recommended |
| device.geo.country | string | Country code using ISO-3166-1-alpha-3. | Optional |
| device.geo.region | string | Region code using ISO-3166-2. | Optional |
| device.geo.metro | string | Google metro code. | Optional |
| device.geo.city | string | City name. | Optional |
| device.geo.zip | string | Zip/postal code. | Optional |
| device.ext | object | Exchange-specific extensions. | Optional |
| device.ext.atts | integer | (iOS Only) An integer passed to represent the app's app tracking authorization status. (0 = not determined, 1 = restricted, 2 = denied, 3 = authorized) | Optional |
| user | object | User object contains known or derived information about the human user. | Recommended |
| user.buyeruid | string | Buyer-specific user ID for mapping. | Recommended |
| user.yob | integer | Year of birth as a 4-digit integer. | Optional |
| user.consent | string | GDPR consent string if applicable. | Optional |
| user.ext | object | Exchange-specific extensions. | Optional |
| user.ext.eids | object[] | Extended identifiers support in the OpenRTB specification allows buyers to use audience data in real-time bidding. This object can contain one or more UIDs from a single source or a technology provider. | Optional |
| source | object | Entity that is the source of the bid request upstream from the exchange. | Optional |
| source.fd | integer | Entity responsible for the final impression sale decision, where 0 = exchange, 1 = upstream source. | Recommended |
| source.ext | object | Exchange-specific extensions. | Required |
| source.ext.omidpn | string | Open Measurement partner name. | Recommended |
| source.ext.omidpv | string | Open Measurement SDK version. | Recommended |
| source.ext.schain | object | Supply chain object. | Recommended |
| source.ext.schain.ver | string | Version of the supply chain specification in use. We only support `1.0` | Required |
| source.ext.schain.complete | integer | Indicates whether the chain contains all nodes (1 = complete, 0 = incomplete). | Required |
| source.ext.schain.nodes[].asi | string | The canonical domain name of the SSP, Exchange, Header Wrapper, etc system that bidders connect to. | Required |
| source.ext.schain.nodes[].sid | string | The identifier associated with the seller or reseller account within the advertising system. | Required |
| source.ext.schain.nodes[].hp | integer | Indicates whether this node will be involved in the flow of payment for the inventory. | Required |
| source.ext.sspname | string | Supply source name. This must be unique and identifies your inventory within our system. | Required |
| regs | object | Regulatory environment in which the impression will be served. | Optional |
| regs.coppa | integer | Flag indicating if this request is subject to COPPA regulations (0 = no, 1 = yes). This flag is set to 1 if a user is younger than 16 (based on user.yob) or when content is created for kids (see {site\|app}.content.ext.dm.iscreatedforkids). | Optional |
| regs.gpp | string | Global Privacy Platform (GPP) string. | Optional |
| regs.gpp_sid | integer[] | Array of applicable GPP section IDs. | Optional |
| regs.gdpr | integer | Flag indicating if this request is subject to GDPR (0 = no, 1 = yes). | Optional |
| regs.ext | object | Exchange-specific extensions. | Required |
| regs.ext.dsa | object | This object is only sent when on gdpr context. | Optional |
| regs.ext.dsa.dsarequired | integer - One of 0, 1, 2, 3 | Flag to indicate if DSA information should be made available. | Optional |
| regs.ext.dsa.pubrender | integer - One of 0, 1, 2 | Flag to indicate if the publisher will render the DSA Transparency info. | Optional |
| regs.ext.dsa.datatopub | integer - One of 0, 1, 2 | Independent of pubrender, the publisher may need the transparency data for audit purposes. | Optional |
| regs.ext.dsa.transparency[].domain | string | Domain of the entity that applied user parameters. | Optional |
| regs.ext.dsa.transparency[].dsaparams | integer[] | Array for platform or sell-side use of any user parameters (using the list provided by DSA Transparency Taskforce). | Optional |
| ext | object | Exchange-specific extensions. | Required |
| ext.player.name | string | Name of your player. | Required |
| ext.player.volume | integer - Between `0` and `10` | Volume of the player at the moment of the request. | Recommended |
