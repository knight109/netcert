# Design Notes

These notes guide future changes to `netcert`. Keep the tool lightweight, focused on authorized website inventory and maintenance, and dependency-free where practical.

## CLI Changes

- Keep target selection (`-u` / `-l`) mutually exclusive and require exactly one function per command.
- When adding a user-facing function, option, or alias, register it in the command-line help with a concise description. Help must describe every supported function and option.
- Update the parser, function dispatch, result formatting, and saving behavior together when adding a function. Preserve text, JSON, and CSV output where applicable.
- The general `Examples` section in `--help` can stay selective; it does not need a new example for every small change.
- When an invalid argument or input prevents a function from running, show a brief, valid example for that function alongside the error so the user can correct the command.
- Show progress for operations that may take time. Send progress messages to stderr so stdout remains usable for text, JSON, and CSV results.

## Output and Scope

- Keep IPv4 and IPv6 results distinct. `--ip` shows both; family-specific options should only show the requested family.
- Keep `--save` for formatted command output and `--store` for collected files.
- Do not turn the tool into a vulnerability scanner. Only support authorized website inventory and maintenance workflows.
- Note external data sources and limitations when a feature depends on them.
