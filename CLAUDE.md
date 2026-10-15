# Personal preferences

## General Guidelines

- When reporting information to me, be extremely concise and sacrifice grammar for the sake of concision.
- Always talk in ASD-STE100 Simplified Technical English. Always read CONTEXT.md files, and use their ubiquitous language.
- Mannered prose substitutes metaphor and flourish for direct statement. Instead of "a parameter worth varying," the mannered writer produces "a dial worth turning." Instead of "this point still matters," they write "this point earns its keep." The phrases exist to display the writer, not to convey the idea, and readers can tell. That is why mannered prose irritates: it makes the reader work harder so the writer can perform. It is also imprecise. Metaphors drag in connotations the writer did not choose and cannot control. The fix is to say what you mean. When a literal phrase is available, use it.

## General Coding Guidelines:

- Make regular commits when making updates to code.
- Do not leave excessive comments over the code that give detail what you have done on the current task. Instead, tell me in chat and then leave the code presentable, with only comments that would be helpful to a skilled reviewer looking at the code for the first time.

## Python Coding Guidelines:

- **ALWAYS** use `uv` over regular `pip`.
- Do not add overly verbose docstrings except where instructed. A succinct string detailing what the function or class does is sufficient.
- Do not use `from __future__ import annotations`. This is not required post Python 3.10+. Instead, postponed annotations are enabled by default when type hints are surrounded by "" marks.
- Unless there is a very good reason to do so, always import at the top of the script. Standard libraries should come first, followed by a double return, then installed libraries, then local modules, e.g.

```import json
from typing import Any

from openai import AzureOpenAI

from app.evals.schemas import JudgeScore, to_float_01
```

- Prefer pathlib.Path over string paths.
- When developing with uv, avoid using `uv run python *` or `uv pip *`. Prefer uv best practice like `uv run *` and `uv add/remove *`.
- Prefer a single config file that uses pydantic's `BaseModel` over global constants at the top of scripts, e.g. `DEFAULT_URL = ...`. This centralises configuration and type checks constants for free.
