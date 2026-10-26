# sails-hook-mcp

Version 0.0.0 is a placeholder for a future MCP server hook for Sails.

```sh
npm install sails-hook-mcp@0.0.0
```

The package loads as a no-op Sails hook. It does not implement MCP, expose endpoints or tools, or provide authentication or authorization. Installing this version does not turn a Sails application into an MCP server.

There are no runtime dependencies or install scripts.

## Planned action exposure

The intended design is default-deny: only explicitly allowlisted Sails actions
may appear as MCP tools or be invoked through MCP. Write actions require
explicit opt-in. Existing application authentication, policies, validation,
and authorization remain authoritative on the server.

These are design requirements for future implementation, not functionality in
version 0.0.0. See [the action exposure requirements](docs/action-exposure.md).

## License

MIT
