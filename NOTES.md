# Problem:

## State Synchronization with a "Single Source of Truth":

HTMX relies on the server as the “source of truth” for state, sending HTML snippets to update the page. If the server’s state (e.g., in a database) doesn’t match what the browser expects, or if the client has temporary data, you might see inconsistencies, like a form showing old values after an update.

For the [first personal project 1 on boot.dev](https://www.boot.dev/courses/build-personal-project-1) I will implement my a demo of a [backend dashboard](https://github.com/romshark/demo-islands/tree/main) which will involve server-side events using Go, HTMX, Hyperscript (Typescript) and Templ without a javascript build step.

## Dashboard Design:

1. Layout:
 
 - Use a grid or flexbox layout to arrange sections logically.
 - Place critical metrics—like server health and error logs—prominently at the top or center for quick access.

2. Visualizations:

- Server Health: [Gauge charts](https://github.com/haiiaaa/chartjs-gauge) to show CPU, memory, and disk usage.
- Error Logs: A [scrolling list](https://htmx.docs-hub.com/examples/infinite-scroll/) of recent errors.
- API Performance: [Line charts](https://www.chartjs.org/docs/latest/charts/line.html) for response times and request rates.
- Database Metrics: [Bar charts](https://www.chartjs.org/docs/latest/charts/bar.html) for query performance and connections.
- Security Alerts: [A notification](https://medium.com/@oggy/building-a-simple-notification-system-with-golang-and-nats-bd8b0a5bf5bc) [panel for real-time alerts](https://themurph.hashnode.dev/go-beyond-the-basics-mastering-toast-notifications-with-go-and-htmx).
- Deployment Status: [A status indicator](https://github.com/mdwn/ghstatus) (e.g., ["In Progress" or "Success"](https://www.githubstatus.com/api/)).

3. Modularity:
- Each section operates independently, fetching and displaying its own data without affecting others.

## Real-Time Updates:

Real-time updates are essential for keeping the dashboard relevant and actionable. Here’s how each component could update dynamically:
- Server Health Metrics:
  - Update: CPU, memory, and disk usage adjust as system load changes.

  - Example: A gauge chart shifts as CPU usage spikes during high traffic.

- Error and Exception Logs:
  - Update: New errors appear as they occur.

  - Example: A list updates with a new critical error entry, highlighted for visibility.

- API Performance:
  - Update: Response times and request rates refresh periodically.

  - Example: A line chart adds a point every minute showing average latency.

- Database Metrics:
  - Update: Query performance and connection counts refresh as activity changes.

  - Example: A bar chart updates to reflect a surge in active connections.

- Security Alerts:
  - Update: New security events are flagged instantly.

  - Example: A notification pops up for a detected unauthorized login attempt.

- Deployment Status:
  - Update: Pipeline or deployment status changes as processes complete.

  - Example: An indicator shifts from "In Progress" to "Success" after a deployment finishes.

## Curiosity/Further Reading/etc:
- Events-Driven Architecture:
> https://github.com/PacktPublishing/Event-Driven-Architecture-in-Golang
> https://sse.dev/
- HTMX/Datastar:
> https://hypermedia.systems/
> https://htmx.org/server-examples/
> https://github.com/bigskysoftware/htmx/issues/3083
> https://github.com/starfederation/datastar/issues/482
> https://github.com/blinkinglight/chat-data-star
> https://github.com/blinkinglight/go-experiment-eventsourcing/tree/main
> https://www.youtube.com/watch?v=HbTFlUqELVc
> https://github.com/wimdeblauwe/blog-example-code/tree/master
> https://htmx.org/essays/why-gumroad-didnt-choose-htmx/
> https://www.youtube.com/watch?v=x7v6SNIgJpE
> https://youtu.be/9AtijVV11SA?si=c3ERB9v1Vpm0KqIY
> https://youtu.be/9AtijVV11SA?si=tV3Bb7_tRr0v7GmU
- Error Handling:
> https://fsharpforfunandprofit.com/rop/
> https://fsharpforfunandprofit.com/posts/recipe-part2/
> https://github.com/workshop-depot/rop
> https://hashset.dev/article/20_derailing_gracefully_with_railway_oriented_programming
- Go:
> https://gobyexample.com/
> https://github.com/haatos/goshipit
> https://github.com/go-andiamo/aitch
> https://github.com/donseba/go-htmx
> https://github.com/gofr-dev/gofr
> https://github.com/gofs-cli/gofs
> https://www.alexedwards.net/blog/the-fat-service-pattern
> https://olegkrivtsov.github.io/using-zend-framework-3-book/html/en/Model_View_Controller/Skinny_Controllers__Fat_Models__Simple_Views.html
> https://www.alexedwards.net/blog/working-with-cookies-in-go
> https://www.alexedwards.net/blog/when-is-it-ok-to-panic-in-go
> https://github.com/sonjek/go-templ-gorm-htmx-picocss-example
> https://github.com/mbaraa/dankmuzikk
> https://github.com/mbaraa/mbaraa.com
> https://github.com/nicholas-fedor/eui64-calculator
> https://rezakhademix.medium.com/how-i-scaled-a-golang-app-to-handle-1-5m-requests-per-minute-7fb706d9119d
> https://github.com/palash25/best-practices-checklist?tab=readme-ov-file#go
- Templ:
> https://templ.guide/
- SQL:
> https://github.com/sqlc-dev/sqlc
- PocketBase:
> https://pocketbase.io/
- AST for CSS Selector:
> https://prataprc.github.io/astquery.io/
> https://github.com/prataprc/goparsec
> https://blog.cloudflare.com/html-parsing-2/
> https://github.com/cloudflare/lol-html?tab=readme-ov-file
> https://github.com/coolspring8/go-lolhtml
> https://github.com/fb55/css-what
> https://www.youtube.com/watch?v=fIPO4G42wYE