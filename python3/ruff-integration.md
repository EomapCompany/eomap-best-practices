# PyCharm Integration with Ruff

1. Install ruff within project
```bash
uv add ruff --group dev
```

2. Copy [ruff.toml](./templates/ruff.toml) into project
3. Setup PyCharm correctly
    - Settings -> Python -> Tools -> Ruff -> Enable 
    - Execution mode: Interpreter