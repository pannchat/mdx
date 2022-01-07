# 구조 1 : JSON {parant}

현재 내위치 : “1_3_2”

`find` 1_3_2 →  있으면 `{id:’1_3_2’, parent:’1_3’}`

`find` 1_3 → 있으면 `{id:’1_3’, parent:’1’}`

`find` 1 → 있으면 `{id:’1’ parent: null}`

# 구조2 :JSON{child}

현재 내 위치 : ”1_3_2”

`find` 1 → 없으면 현재위치 1 children

재귀 : `find` 1_1 → 없으면 현재위치 1_1 children 

children없으면 반환

`find` 1_2 → 없으면 현재위치 1_2 children 

`find` 1_2_1 → .....

# 구조3


가능하다면 

    DataGrid
    ├── index.mdx
    │   ├── Initialize
    │   │   └── index.mdx
    │   ├── Column
    │   │   ├── index.mdx
    │   │   ├── Data
    │   │   │   └── index.mdx
    │   │   ├── Text
    │   │   │   └── index.mdx
    │   │   ├── AutoComplete
    │   │   │   └── index.mdx
    │   │   ├── Number
    │   │   │   └── index.mdx
    │   │   ├── DropDown
    │   │   │   └── index.mdx
    │   │   ├── MaskedText
    │   │   │   └── index.mdx
    │   ├── AutoComplete
    │   │   └── index.mdx
    │   ├── DataSource
    │   │   └── index.mdx
    ...
    ...
    ...

    
이런 구조
