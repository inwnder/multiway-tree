# JAVA实现的多叉树

## 介绍

本项目提供了JAVA中多叉树的一种实现

## 依赖

1. JDK1.7以上

## 使用说明

### 总览

#### 构建阶段
+ 使用`com.inwnder.util.tree.Tree.getBuilder(Class<V> IDType, Class<E> valueType)`函数实例化一个`ID`类型为`IDType`、`value`类型为`valueType`的`<V, E extends Comparable<E>> com.inwnder.util.tree.TreeBuilder<V, E>`，下文称为`treeBuilder`。
- `treeBuilder`对象为多叉树的构建器。其中`value`是构成多叉树各个节点的值，会被存储在生成的多叉树中; `ID`为对象唯一标识，用来在树的构建阶段标识节点间的关系，不存储在生成的多叉树中。
- `treeBuilder`通过`addValue(V ID, E value, V parentID)`方法收集节点ID、值和该节点对应父节点的ID，对于根节点，`parentID`应设为`null`。节点**不需要**按照某种顺序添加。
- 可通过`treeBuilder.setNoCover(boolean noCover)`配置`ID`重复时构建器的行为，设为`false`（默认）时，后添加的相同ID节点将会覆盖先添加的；设为`true`时，`addValue()`将会在重复时抛出一个`com.inwnder.util.tree.exception.DuplicatedIDException`。
- 添加完构成多叉树的全部节点后，执行`treeBuilder.build()`以基于输入的节点信息和结构构建一个`<E extends Comparable<E>> com.inwnder.util.tree.Tree`的实例，下文称为`tree`。
- 构建中会检查输入的节点关系能否构成一个合法的多叉树，根据不合法的情况类型，`treeBuilder.build()`会抛出以下异常
  1. `com.inwnder.util.tree.exception.UndescribedParentNodeException`表示某个输入的节点声明其有一个父节点但实际不存在
  2. `com.inwnder.util.tree.exception.CircledTreeException`表示节点关系图中存在环路，无法构成一个树
  3. `com.inwnder.util.tree.exception.DisconnectedNodesException`表示节点关系图中有节点和其他节点不联通
- 可以通过`catch`这些异常对象来获取更具体的信息

#### 树的结构

（待续）
