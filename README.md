# Mobile Big Data Projects

This repository contains projects completed for the
Mobile Big Data Analytics and Management course.

## Projects

- Project 1: Mobile Phone Activity Analysis (`Project-1-Mobile-Phone-Activity-Analysis/`)
- Project 2: Social Media Extremism Detection (`Project-2-Social-Media-Extremism-Detection/`)
- Project 3: Multi-Dimensional Extremist Content Analysis and Counter-Narrative Generation (`Project-3-Multi-Dimensional-Extremist-Content-Analysis-and-Counter-Narrative-Generation/`)

## Colab Local Runtime In VS Code

This repo includes a small launcher so you can:

- edit code in VS Code
- start a local Jupyter runtime from VS Code
- connect a Google Colab notebook in the browser to your local machine

### One-time setup

Install the local runtime dependency in your active Python environment:

```powershell
python -m pip install -r requirements-colab-local.txt
```

If you already use a virtual environment, activate it in VS Code before running the command.

### Start the local runtime

You can use either option:

```powershell
.\scripts\start_colab_local_runtime.ps1
```

Or in VS Code:

- `Terminal` -> `Run Task`
- choose `Start Colab Local Runtime`

The launcher starts Jupyter with the Colab-compatible settings from Google's local runtime guide:
https://research.google.com/colaboratory/local-runtimes.html

### Connect from Colab

1. Open your notebook in Colab.
2. Click `Connect`.
3. Choose `Connect to local runtime...`.
4. Copy the full `http://localhost:8888/?token=...` URL from the VS Code terminal.
5. Paste it into Colab and connect.

### Troubleshooting

- If `8888` is already in use, run:

```powershell
.\scripts\start_colab_local_runtime.ps1 -Port 8890
```

- If `jupyter` is not found, make sure you installed `requirements-colab-local.txt` in the same Python environment that VS Code is using.
- Keep the terminal open while Colab is connected.
