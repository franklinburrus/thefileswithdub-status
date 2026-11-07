# The Files with Dub feed monitor

<!--live status--> **🟩 All systems operational**

[Feed health](https://www.thefileswithdub.com/api/feed-health) checks X metadata, X playback and YouTube together. A healthy response requires HTTP 200 and the exact `"status":"healthy"` marker.

[GitHub Actions](https://github.com/franklinburrus/thefileswithdub-status/actions/workflows/uptime.yml) runs the pinned [Upptime](https://github.com/upptime/uptime-monitor) monitor. Incidents are assigned to `franklinburrus` and recovery closes the incident with a comment. GitHub notification delivery follows the owner's GitHub settings.

Checks are scheduled every five minutes.

Manual dispatch offers `none`, `outage` and `recovery`. The outage test checks a fixed missing URL to verify alert delivery. Recovery and normal checks use the production health endpoint. Delivery-test incidents carry the `delivery-test` label and remain in the incident history.

Configuration lives in [.upptimerc.yml](.upptimerc.yml). Check history lives in [history/dub-feeds.yml](history/dub-feeds.yml) after the first run. The MIT license and upstream copyright are retained in [LICENSE](LICENSE).
