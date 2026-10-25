# pip install requests
import requests

TOKEN, OWNER, REPO = "ghp_xxx", "your-name", "your-repo"
LABELS = {"bug": "DA3633", "feature": "2F81F7", "docs": "8957E5", "help wanted": "238636"}

for name, color in LABELS.items():
    r = requests.post(
        f"https://api.github.com/repos/{OWNER}/{REPO}/labels",
        headers={"Authorization": f"Bearer {TOKEN}"},
        json={"name": name, "color": color},
    )
    print(name, r.status_code)  # 201 created, 422 already exists# Repo-label-colour-tool
