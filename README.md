# GitHub RepoMonster

This script automates the process of creating multiple GitHub repositories from a predefined list of templates. Each new repository is named uniquely using a combination of random adjectives, animals, and timestamps to avoid duplication. The script logs the created repository names to a timestamped file for future reference or cleanup purposes.

## Requirements

- Python 3.x
- `requests` library (install via `pip install requests`)

## Configuration

Before running the script, set the following environment variables:

- `GITHUB_TOKEN`: Your GitHub personal access token (for authentication).
- `ORG_NAME`: The name of your GitHub organization.
  
You can also adjust the script settings by modifying the following variables:

- `TEMPLATE_REPOS`: A list of template repositories available in your organization to base new repos on.
- `NUM_REPOS`: The number of repositories you want to create (default is 10).
  
## How It Works

1. The script selects a random template repository from `TEMPLATE_REPOS`.
2. It generates a unique repository name by combining a random adjective, animal, and a timestamp.
3. A new repository is created using the selected template.
4. The repository name is logged to a file named `github-repomonster-created-YYYYMMDD-HHMMSS.txt`.
5. This process repeats for the number of times defined by `NUM_REPOS`.

## Example Usage

```bash
export GITHUB_TOKEN="your_personal_access_token"
export ORG_NAME="your_org_name"
python github_repomonster.py
```

## Sample Output

```text
===============================================
📢 Starting Repository Creation
📌 Organization: your_org_name
📌 Number of Repositories: 10
📌 Available Templates: Enterprise_Template-1, Enterprise_Template-2, Enterprise_Template-3
📌 Logging created repos to: github-repomonster-created-20250409-120015.txt
===============================================

✅ Successfully created repo: agile_puma_505078 from Enterprise_Template-1
✅ Successfully created repo: brave_penguin_202243 from Enterprise_Template-2
...

===============================================
✅ Repository creation complete!
📂 Created repositories logged in: github-repomonster-created-20250409-120015.txt
📌 This file can be used for automated deletion process.
===============================================
```

## Notes

- Ensure you have the necessary permissions to create repositories within the specified GitHub organization.
- The script includes a 1-second delay between repository creation attempts to avoid hitting GitHub's rate limits.
- The created repositories are private by default; you can modify this by adjusting the `private` flag in the `create_repo` function.

## Disclaimer

Be careful when running this script in production environments, as it will create repositories based on the templates you specify. Ensure that your GitHub organization is prepared for the number of repositories being created.

## License

MIT License

Copyright (c) 2024

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
