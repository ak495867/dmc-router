# dmc-router

High-Throughput HTTP REST API Router & Middleware Framework for Demonic C.

## Installation

Add this package to your Demonic C project:

``bash
dmc pkg add https://github.com/ak495867/dmc-router.git
``

## Features

- **Core Structures**: \Router\, \Route\, \Request\, and \Response\ data structures.
- **Parametric Route Matching**: Support for parameterized paths such as \/api/users/:id\ and \/posts/:post_id/comments/:comment_id\.
- **HTTP Method Dispatch**: Fast dispatching across \GET\, \POST\, \PUT\, \DELETE\, \PATCH\, and \OPTIONS\.
- **Middleware Pipeline**: Built-in support for CORS header management, authorization checking, and access logging.
- **Query Parser**: Parse query strings with \outer_parse_query\ and lookup values with \outer_query_get\.
- **Serialization & Formatting**: Helpers for JSON status responses, formatted error responses, and HTTP/1.1 wire serialization.

## Quick Start

``dmc
import dmc_router;

fn main() -> int {
    var app: Router = router_new();
    router_use_cors(&app, "*", "GET,POST,OPTIONS", "Content-Type,Authorization");
    router_use_logging(&app);

    router_get(&app, "/api/users/:id", 1);
    router_post(&app, "/api/users", 2);

    let req: Request = request_new("GET", "/api/users/42", "", "");
    let res: Response = router_dispatch(&app, req);

    return res.status;
}
``

## Running Tests

``bash
dmc test tests
``

## License

MIT
