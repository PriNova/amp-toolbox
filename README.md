# amp-toolbox

A curated collection of ready-to-drop-in tools for [Amp](https://ampcode.com)'s **Bring-Your-Own-Tools** feature.

## Quick start

1. Clone or download this repo:  
   ```bash
   git clone https://github.com/<your-org>/amp-toolbox.git ~/amp-toolbox
   ```

2. Point Amp at the folder:  
   ```bash
   export AMP_TOOLBOX="$HOME/amp-toolbox"
   ```

3. Launch Amp.  
   Every script in this file in the repo is automatically discovered and becomes available to the AI.

## Tool list

| Tool          | Purpose                                                | Arguments |
|---------------|--------------------------------------------------------|-----------|
| `run-tests`   | Run project tests with pnpm (Node, Bun, Deno supported) | `dir` (workspace directory) |
| `fmt-rust`    | Format Rust code with `cargo fmt`                      | `dir` |
| `lint-ts`     | Lint TypeScript with `eslint`                          | `dir`, `fix` (bool) |
| `git-status`  | Return concise git status for the workspace            | — |
| `curl-json`   | Perform HTTP GET and return JSON                       | `url`, `headers` (optional) |

(The list above is illustrative; see the repo for the actual tools provided.)

## Contributing

1. Fork the repo.  
2. Place your executable (script or binary) in the root.  
3. Ensure it responds correctly to `TOOLBOX_ACTION=describe` and `TOOLBOX_ACTION=execute`.  
4. Open a PR with a short description and usage example.

### Required interface

Describe phase (stdout, single-line JSON):

```json
{"name":"my-tool","description":"What it does","args":{"arg1":["string","hint"]}}
```

Execute phase (stdin, JSON matching `args`):

```json
{"arg1":"value"}
```

Stdout/stderr from the execute phase is returned to the user.

## License

MIT — see [LICENSE](LICENSE).
