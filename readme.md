# 구조 1 : JSON {parant}

현재 내위치 : “1_3_2”

`find` 1_3_2 →  있으면 `{id:’1_3_2’, parent:’1_3’}`

`find` 1_3 → 있으면 `{id:’1_3’, parent:’1’}`

`find` 1 → 있으면 `{id:’1’ parent: null}`
```ts
interface NodeType{
    id: string;
    name: string;
    type: string;
    parent: {id: string} | null;
}
function setBreadCrumb():NodeType[]{
    const arr:NodeType[] = [];
    const myId = "1_3_1";
    let targetItem = Test.find( currentNode => currentNode.id === myId);
    if(targetItem){
        if(targetItem.parent){
            while(targetItem?.parent){
                arr.push(targetItem)
                let temp = targetItem
                targetItem = Test.find( currentNode => currentNode.id === temp.parent.id)
            }
        } else {
            if(targetItem) arr.push(targetItem)
        }
        if(targetItem) arr.push(targetItem)
        else throw new Error('아이템이 없음');
    }

    return arr.reverse();
}
```
# 구조2 :JSON{child}

현재 내 위치 : ”1_3_2”

`find` 1 → 없으면 현재위치 1 children

재귀 : `find` 1_1 → 없으면 현재위치 1_1 children 

children없으면 반환

`find` 1_2 → 없으면 현재위치 1_2 children 

`find` 1_2_1 → .....

```ts
export interface NodeType {
    id: string;
    name: string;
    type: string;
    child: NodeType[] | null;
}


function setBreadCrumb(Nodes, targetNode, arr: NodeType[] = []) {
    for (var node of Nodes) {
        if (node.id === targetNode) {
            arr.push(node)
            return arr;
        }
        if (node.child) {
            arr.push(node)
            if (!setBreadCrumb(node.child, targetNode, arr)) arr.pop();
            else return arr;
        }
    }
}
```

# 구조3

```md
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
```

| DataGrid 접속시 | Breadcrumb |
|---|---|
| 접속 직후 | DataGrid > `MULTINODE: index.mdx` |
| L1 MULTINODE 선택 전 | DataGrid > `[Initialize, Column, AutoComplete, DataSource]`|
| L1 MULTINODE 선택 후 |DataGrid > Column > `MULTINODE: Column/index.mdx` |
| L2 MULTINODE 선택 전 |DataGrid > Column > `[Data, Text, AutoComplete, Number, DropDown, MaskedText]`  |
| L2 MULTINODE 선택 후 |DataGrid > Column > Data > `NODE: Column/Data/index.mdx`  |


# 공통
## MULTINODE : index.mdx
- TOC <화면사이즈에 따라 `colum` or `row`>
- 하위 노드들 목차와 간략한 설명으로 구성

## NODE : index.mdx
- TOC <화면사이즈에 따라 `colum` or `row`>
- 가장 pure한 예제 코드
- 컴포넌트 예제
- 컴포넌트 전체 코드
- 추가 설명
- (활용 예제)
- (활용 예제 코드)

## 문서 활용
- LINK 활용 문서에서 문서로 넘어가기 쉬워야함






참고 
- https://developer.mozilla.org/ko/docs/Web/JavaScript
- https://beta.reactjs.org/
- https://getbootstrap.com/docs/5.1/getting-started/introduction/

