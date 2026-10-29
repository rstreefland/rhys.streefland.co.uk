# Site performance report

Measured against the committed homepage before the redesign. Hugo 0.101.0 production build, `--minify --cleanDestinationDir`.

| Metric | Previous | Redesigned |
| --- | ---: | ---: |
| Homepage HTML | 3,550 bytes | 1,524 bytes |
| Local homepage assets, including HTML | 60,120 bytes | 4,426 bytes |
| Gzip-compressed new HTML + CSS (level 6) | Not measured | 1,896 bytes |
| New homepage requests | — | 2 |
| New external resource requests | — | 0 |
| New JavaScript bytes | — | 0 |

Local asset payload reduced by 92.6%. The previous total excludes third-party font/icon CSS and font downloads, so it understates the previous full payload. The new homepage uses system fonts and requires only HTML and a cacheable fingerprinted stylesheet. The portrait remains available but is not downloaded by pages.

## Timing measurement

30 sequential cold HTTP fetch pairs (homepage + stylesheet), Python HTTP server over loopback, no artificial throttling: median 1.87 ms; minimum 1.53 ms; maximum 19.13 ms. This measures local response/body transfer, not browser rendering or public network load time. Uncompressed response bodies total 4,426 bytes; HTTP/TLS headers are excluded. The gzip figure is a compression measurement, not a claim about deployment compression settings.

Public load time, actual compressed bytes over the wire, FCP and LCP remain unmeasured until deployment and browser profiling. No browser runtime was available in this workspace. These local results should not be interpreted as visitor load times.

## Validation

Production build passed. All root-relative links and assets in generated HTML resolve. Custom layouts cover the homepage, future writing and articles, taxonomy lists and 404. About content is on the homepage; the About page and placeholder blog post are removed. CSS includes mobile layouts, visible keyboard focus, a skip link and no animation. Visual/browser validation remains outstanding.
