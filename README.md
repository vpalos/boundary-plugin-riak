# Boundary Riak Plugin

The Boundary Riak plugin collects information on Riak clusters.

## Prerequisites

- Metrics are collected via HTTP requests, therefore **all OSes** should work (tested on **Debian-based Linux** distributions).
- Requires Riak [stats endpoint](http://docs.basho.com/riak/latest/dev/references/http/status/) to be enabled and accessible from the machine running the plugin.
- Written in pure Lua/Luvit (embedded in `boundary-meter`) therefore **no dependencies** are required.

### Meter V4.0 or greater (Lua based plugin)

To get the new meter:

    curl -fsS \
        -d "{\"token\":\"<your API token here>\"}" \
        -H "Content-Type: application/json" \
        "https://meter.boundary.com/setup_meter" > setup_meter.sh
    chmod +x setup_meter.sh
    ./setup_meter.sh

### Meter less than V4.0 (Python-based plugin)

- Python 2.6 or later is required.

## Plugin Setup

None required.

## Configurable Setings
|Setting Name        |Identifier     |Type    |Description                                                                              |
|:-------------------|---------------|--------|:----------------------------------------------------------------------------------------|
|Riak Statistics URI |statisticsUri  |string  |The URI to Riak's statistics REST API endpoint (default: 'http://127.0.0.1:8098/stats'). |
|Poll Retry Count    |pollRetryCount |integer |The number of times to retry failed HTTP requests (default: 5, infinite: -1).            |
|Poll Retry Delay    |pollRetryDelay |integer |The interval (in milliseconds) to wait before retrying a failed request (default: 3000). |
|Poll Interval       |pollInterval   |integer |How often (in milliseconds) to poll the Couchbase node for metrics (default: 5000).      |

## Metrics Collected

The information collected is a subset of the [stats endpoint data](http://docs.basho.com/riak/latest/dev/references/http/status/), which also includes some data from the [riak-admin status](http://docs.basho.com/riak/latest/ops/running/nodes/inspecting/) command.


