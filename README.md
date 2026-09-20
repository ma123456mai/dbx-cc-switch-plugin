# CC-SWITCH Config Import

The plugin uses the official CC-SWITCH application icon from the public
[CC-SWITCH repository](https://github.com/farion1231/cc-switch).

This public DBX plugin imports AI provider configurations from the local
CC-SWITCH SQLite database. The source is public because the plugin handles API
keys while reading the database.

The DBX host supplies the database path through the `ai-config-import`
capability. The importer opens the database read-only and returns the DBX AI
configuration JSON protocol. It does not write to CC-SWITCH or send
credentials over the network.

The native candidate is built for the DBX Store targets currently supported by
the official release workflow: `darwin-arm64`, `darwin-x64`, `windows-x64`,
`linux-x64`, and `linux-arm64`. Windows ARM64 is not claimed because the
official workflow does not currently provide a Windows ARM64 runner.

## Development

Install the DBX plugin CLI, then run:

```bash
dbx-plugin package .
```

This creates an unsigned, target-specific `.dbxp` candidate and matching
`.artifact.json` in `dist/`. Native candidates must be built separately on
each supported DBX target. The official DBX Store signs reviewed candidates
before users install them.

The source repository contains no plugin packages. Release automation builds
the candidates from the tagged source and publishes them to the GitHub
Release that triggered the workflow.
