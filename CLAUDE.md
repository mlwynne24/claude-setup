# Personal preferences

## General Coding Guidelines:
- Make regular commits when working autonomously on a plan.
- Do not leave excessive comments over the code that give detail what you have done on the current task. Instead, tell me in chat and then leave the code presentable, with only comments that would be helpful to a skilled reviewer looking at the code for the first time.
- Keep scripts ideally <200 lines long. If scripts are longer, unless there is a very good reason for this, prefer splitting the script into smaller scripts and importing classes, functions and objects. This is so code is more human-readable and -understandable.

## Python Coding Guidelines:
- **ALWAYS** use `uv` over regular `pip`.
- Do not add overly verbose docstrings except where instructed. A succinct string detailing what the function or class does is sufficient.
- Do NOT add strings at the top of each script, describing what they do. Unless this is providing functionality, e.g. facilitating argparse --help tag.
- Do not use `from __future__ import annotations`. This is not required post Python 3.10+. Instead, postponed annotations are enabled by default when type hints are surrounded by "" marks.
- Unless there is a very good reason to do so, always import at the top of the script. Standard libraries should come first, followed by a double return, then installed libraries, then local modules, e.g.
```import json
from typing import Any

from openai import AzureOpenAI

from app.evals.schemas import JudgeScore, to_float_01
```
- Prefer pathlib.Path over string paths.
- When developing with uv, avoid using `uv run python *` or `uv pip *`. Prefer uv best practice like `uv run *` and `uv add/remove *`.
- Avoid global constants, e.g. `DEFAULT_URL=...`, at the top of scripts. Prefer a single config file that uses pydantic's `BaseModel`. This centralises configuration and type checks constants for free.
- Where appropriate, try to centralise models in one place, rather than defining at their implementation site. E.g. for a dataclass:
```@dataclass
class AddOptions:
    names: list[str]
    agents: list[str]
    use_global: bool
    yes: bool
    no_overwrite: bool
    force: bool
    source: Source
```
Instead of storing in `add.py`, store in `models.py` alongside other options dataclasses.
