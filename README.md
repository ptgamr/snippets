# snippets
Some great code snippets found along to road


### Convert an array of items to a hierarchical structure

```js
function toHierarchyStructure(items: any[]) {
    const map = {};

    for (let i = 0; i < items.length; i++) {
        const item = items[i];
        item.children = [];

        map[item._id] = item;

        const parent = item.parent || '-';

        if (!map[parent]) {
            map[parent] = {
                children: [],
            };
        }

        map[parent].children.push(item);
    }

    return map['-'].children;
}

const arr = [
  {id: 1, name: 'Any name 1', parent: null},
  {id: 2, name: 'Any name 2', parent: 1},
  {id: 3, name: 'Any name 3', parent: 1},
  {id: 4, name: 'Any name 4', parent: 2},
]

console.log(toHierarchyStructure(arr))
/*
[
  {
    id: 1, 
    name: 'Any name 1', 
    children: [
      {id: 2, name: 'Any name 2', children: [{id: 4, name: 'Any name 4'}]},
      {id: 3, name: 'Any name 3'},
    ]
  }
]
*/
```
