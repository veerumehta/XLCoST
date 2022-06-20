
### Code Search

The code search task is divided into two subtasks: Cross-Lingual(XL) Code Search and Natural Language(NL) Code Search. The data for XL Code Search can be found in the ```code2code_search``` directory and the data for NL Code Search can be found in the ```nl2code_search``` directory. Both are further sub divide into ```program_level``` and ```snippet_level``` tasks, each of which contains the data corresponding to each language.

For XL Code Search, the directory names (languages) represent the query language. For NL Code Search, the directory names represent the search result language. Queries in this case are ofcourse the natural language comments(```snippet_level```) or descriptions(```program_level```).

```
code2code_search
├── program_level
│   ├── C
│   ├── C#
│   ├── C++
│   ├── Java
│   ├── Javascript
│   ├── PHP
│   ├── Python
│   └── collective_data
└── snippet_level
    ├── C
    ├── C#
    ├── C++
    ├── Java
    ├── Javascript
    ├── PHP
    ├── Python
    └── collective_data
    
nl2code_search
├── program_level
│   ├── C
│   ├── C#
│   ├── C++
│   ├── Java
│   ├── Javascript
│   ├── PHP
│   └── Python
└── snippet_level
    ├── C
    ├── C#
    ├── C++
    ├── Java
    ├── Javascript
    ├── PHP
    └── Python
```
Shown below is the data structure for one language for the XL Code Search task. It is the same for all other languages.
```
code2code_search
├── program_level
│   ├── C
│       ├── test.jsonl
│       ├── train.jsonl
│       └── valid.jsonl
└── snippet_level
    ├── C
        ├── test.jsonl
        ├── train.jsonl
        └── val.jsonl
```

Example format of the ```.jsonl``` files for ```program_level``` data is shown below. The ```idx``` key denotes ```{query_pid}-{query_lang}/{target_pid}-{target_lang}``` to uniquely identify each data point. ```docstring_tokens``` maps to the list of code tokens for the query language. ```code_tokens``` maps to the list of code tokens for the target language. 
```json
{ "idx": "9359-C/9359-Python", 
  "docstring_tokens": ["list of query language code tokens"], 
  "code_tokens": ["list of target language code tokens"],
  "url": "9359-C/9359-Python"}
```

The ```.jsonl``` files for ```snippet_level``` data have the following format. The example shown below corresponds to data with C as the query language.
The ```idx``` key denotes ```{query_pid}-{query_lang}-{snippet_id}/{target_pid}-{target_lang}-{snippet_id}``` to uniquely identify each data point. ```docstring_tokens``` maps to the list of snippet code tokens for the query language. ```code_tokens``` maps to the list of snippet code tokens for the target language. 
```json
{"idx": "9359-C-1/9359-Python-1",
 "docstring_tokens": ["#include", "<stdio.h>", "NEW_LINE", "#include", "<math.h>"],
 "code_tokens": ["import", "math", "NEW_LINE"],
 "url": "9359-C-1/9359-Python-1"}
```
Shown below is the data structure for one language for the NL Code Search task. It is the same for all other languages.
```
nl2code_search
├── program_level
│   ├── C
│       ├── test.jsonl
│       ├── train.jsonl
│       └── valid.jsonl
└── snippet_level
    ├── C
        ├── test.jsonl
        ├── train.jsonl
        └── val.jsonl
```