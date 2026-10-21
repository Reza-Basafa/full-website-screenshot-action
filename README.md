# Full Website Screenshot Action

Capture a full-page screenshot of a public website with Puppeteer. The action configures Node.js 20 automatically, so callers do not need to install Node.js or set up Puppeteer themselves.

## Use this action

```yaml
- name: Capture website
  uses: Reza-Basafa/full-website-screenshot-action@main
  with:
    url: https://example.com
    destination: ./artifacts/screenshot.png
```

The action creates the screenshot at the path you provide. To keep it after the workflow ends, upload it as an artifact:

```yaml
- uses: actions/upload-artifact@v4
  with:
    name: website-screenshot
    path: ./artifacts/screenshot.png
```

## Run it manually and enter a URL

GitHub Actions steps do not prompt for input interactively. To enter a URL when starting a workflow, add a workflow with `workflow_dispatch` inputs. This repository includes one at `.github/workflows/screenshot.yml`. Open **Actions → Website Screenshot → Run workflow**, enter the URL, and start the run.

## Inputs

| Input | Required | Default | Description |
|---|---|---|---|
| `url` | Yes | — | Public website URL, including `https://` |
| `destination` | No | `./screenshot.png` | Output screenshot path |

## Notes

- Supports `http://` and `https://` URLs.
- Runs on GitHub-hosted Linux runners.
- Websites that require authentication or block automated browsers may not be capturable.
