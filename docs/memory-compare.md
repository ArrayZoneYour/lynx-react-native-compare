## Test Environment

### Version

#### Lynx 3.1

https://github.com/ArrayZoneYour/integrating-lynx-demo-projects

#### React Native 0.78.0

https://github.com/ArrayZoneYour/integrating_react_native_demo_projects

### Result

| Scenario            | React Native             | Lynx                     |
| ------------------- | ------------------------ | ------------------------ |
| Empty Component     | 48M ~ 50.3M              | 58.5M ~ 62.6M            |
| List (First Screen) | 133.1M ~ 140M (+ ~90M)   | 101.9M ~ 107.9M (+ ~40M) |
| List (ScrollToEnd)  | 247.7 ~ 250.4M (+ ~110M) | ~155.8M (+ ~50M)         |

### Testcase

#### Empty Component

##### React Native

```tsx
import { AppRegistry } from "react-native";

AppRegistry.registerComponent(appName, () => () => null);
```

##### Lynx

```tsx
import { root } from "@lynx-js/react";

root.render(() => null);
```

##### Result

> I only run these cases once on Pixel 8.

> Lynx can reuse item component when component node is the direct children of `<list-item>`

React Native: 48M ~ 50.3M

![](https://github.com/ArrayZoneYour/integrating_react_native_demo_projects/blob/main/images/empty-component.png?raw=true)

Lynx: 58.5M ~ 62.6M

![](https://github.com/ArrayZoneYour/integrating-lynx-demo-projects/blob/benchmark-use-rn-similar-cases/images/empty-component.png?raw=true)

#### First Screen (with 204 item loaded)

Simplify from https://github.com/facebook/react-native/blob/main/packages/rn-tester/js/examples/FlatList/FlatList-multiColumn.js

![](../images/start.png)

React Native: 133.1M ~ 140M (+ ~90M)

![](https://github.com/ArrayZoneYour/integrating_react_native_demo_projects/blob/main/images/flatlist-first-screen-lower.png?raw=true)

Lynx: 101.9M ~ 107.9M (+ ~40M)

![](https://github.com/ArrayZoneYour/integrating-lynx-demo-projects/blob/benchmark-use-rn-similar-cases/images/list-204-start.png?raw=true)

#### Scroll To List Last Item

![](../images/end.png)

React Native: 247.7 ~ 250.4M (+ ~110M)

![](https://github.com/ArrayZoneYour/integrating_react_native_demo_projects/blob/main/images/flatlist-scroll-end.png?raw=true)

Lynx: ~155.8M (+ ~50M)

![](https://github.com/ArrayZoneYour/integrating-lynx-demo-projects/blob/benchmark-use-rn-similar-cases/images/image-204to1000-end.png?raw=true)
