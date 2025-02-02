# Meri

Your loyal companion, helping you stay organized and remember what truly matters.

## Install locally

First, you need [uv](https://github.com/astral-sh/uv) to be installed.

If you are on NixOs, you need a FHS compliant environment, so run this command each time you need to use uv.
(Zlib is needed for some python packages that does not work very well with nix dynamic binaries)
```shell
nix-shell -E 'with import <nixpkgs> {}; (pkgs.buildFHSUserEnv { name = "fhs"; targetPkgs = pkgs: ([ pkgs.zlib ]); runScript = "zsh"; }).env'
```
note: replace `zsh` by the shell you use. (It helps you to keep your shell env with aliases and config inside fhs)

This project uses python 3.11.
```shell
uv python install 3.11
```

Then, setup venv and activate it :
```shell
uv venv
source .venv/bin/activate
```

Finally, install dependencies :
```shell
uv sync
```

## Environment variables
Create a `.env` file with these variables:
```
OPENAI_API_KEY=<your-openai-api-key>
OPENAI_MODEL=<openai-model>
```

## Run locally
Run postgresql database:
```shell
docker compose up -d
```

Run the app:
```shell
python meri/app.py
```

## Run the tests
```shell
pytest tests
```

## Run Coverage
```shell
coverage run -m pytest tests
coverage report -m
```

## Contribute
This will install pre-commit hook to run multiple checks, ruff and pyright before committing.
```shell
pre-commit install
```

## License
This project is licensed under the GNU General Public License v3.0 (GPL v3).
You are free to use, modify, and distribute this software, as long as any distributed version is also licensed under GPLv3.
This software is provided "as is", without warranty of any kind.
See the [LICENSE](LICENSE) file for more details.
