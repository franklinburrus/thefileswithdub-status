# The Files with Dub feed monitor

<!--live status--> **🟩 All systems operational**

[Feed health](https://www.thefileswithdub.com/api/feed-health) checks X metadata, X playback and YouTube together. A healthy response requires HTTP 200 and the exact `"status":"healthy"` marker.

[GitHub Actions](https://github.com/franklinburrus/thefileswithdub-status/actions/workflows/uptime.yml) runs the pinned [Upptime](https://github.com/upptime/uptime-monitor) monitor. Incidents are assigned to `franklinburrus` and recovery closes the incident with a comment. GitHub notification delivery follows the owner's GitHub settings.

GitHub's native schedule remains enabled at `3-59/5 * * * *`. Its first automatic execution is pending verification. The GitHub API showed no scheduled runs when checked on November 8, 2026 at 00:28 UTC.

The separate Cloudflare automatic trigger is designed to dispatch `uptime.yml` in production and `trigger-smoke.yml` in preview. It passes a UUID `trigger_id` and `delivery_test=none`. The run name carries the correlation ID. Activation requires the deployed trigger Worker and its scoped GitHub credential. The preview workflow records correlation with read-only permissions.

Manual dispatch offers `none`, `outage`, `degraded` and `recovery`. The outage test checks a fixed missing URL to verify HTTP failure detection. The degraded test checks the committed [semantic-failure fixture](fixtures/degraded-health.json), which returns HTTP 200 with top-level `status=degraded` and nested healthy `state` fields. The exact healthy-body marker rejects that response. Recovery and normal checks use the production health endpoint. Delivery-test incidents carry the `delivery-test` label and remain in the incident history.

Configuration lives in [.upptimerc.yml](.upptimerc.yml). Check history lives in [history/dub-feeds.yml](history/dub-feeds.yml) after the first run. The MIT license and upstream copyright are retained in [LICENSE](LICENSE).
