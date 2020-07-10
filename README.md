# drag\_and\_drop\_lists
Two-level drag and drop reorderable lists.

## Features
- Reorder elements within a single list
- Reorder lists
- Drag and drop new elements from outside of the lists
- Vertical or horizontal layout
- Expandable lists
- Can be used in slivers
- Easy to extend with custom layouts

![](https://raw.githubusercontent.com/philip-brink/DragAndDropLists/master/readme_images/basic.gif)
![](https://raw.githubusercontent.com/philip-brink/DragAndDropLists/master/readme_images/list_tiles.gif)
![](https://raw.githubusercontent.com/philip-brink/DragAndDropLists/master/readme_images/slivers.gif)
![](https://raw.githubusercontent.com/philip-brink/DragAndDropLists/master/readme_images/expansion_tiles.gif)
![](https://raw.githubusercontent.com/philip-brink/DragAndDropLists/master/readme_images/horizontal.gif)

## Usage
To use this plugin, add `drag_and_drop_lists` as a [dependency in your pubspec.yaml file.](https://flutter.dev/docs/development/packages-and-plugins/using-packages)
For example:

```
dependencies:
  drag_and_drop_lists: ^1.0.0
``` 

Now in your Dart code, you can use: `import 'package:drag_and_drop_lists/drag_and_drop_lists.dart';`

To add the lists, add a `DragAndDropLists` widget. Set its children to a list of `DragAndDropList`. Likewise, set the children of `DragAndDropList` to a list of `DragAndDropItem`.
For example:

```
...

  DragAndDropLists(
    children: List.generate(_lists.length, (index) => _buildList(index)),
    onItemReorder: _onItemReorder,
    onListReorder: _onListReorder,
  ),

...

_buildList(int outerIndex) {
  var innerList = _lists[outerIndex];
  return DragAndDropList(
    title: Text('List ${innerList.name}'),
    children: List.generate(innerList.children.length, (index) => _buildItem(innerList.children[index])),
  );
}

_buildItem(String item) {
  return DragAndDropItem(
    child: ListTile(
      title: Text(item),
    ),
  );
}
```
