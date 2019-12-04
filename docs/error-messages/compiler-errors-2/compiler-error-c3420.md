---
title: Chyba kompilátoru C3420
ms.date: 11/04/2016
f1_keywords:
- C3420
helpviewer_keywords:
- C3420
ms.assetid: 99b53c77-f36b-4574-9199-b53111becccb
ms.openlocfilehash: 5e165a0c181bc27adebe75111050f49130305693
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756250"
---
# <a name="compiler-error-c3420"></a>Chyba kompilátoru C3420

"finalizační metoda": finalizační metoda nemůže být virtuální.

Finalizační metodu lze volat pouze v nadřazeném typu, který není prakticky prakticky. Proto je chyba deklarovat virtuální finalizační metodu.

Další informace naleznete v tématu [destruktory a finalizační metody v tématu How to: Define and spotřebovávají Classes andC++Structs (/CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

## <a name="example"></a>Příklad

Následující ukázka generuje C3420.

```cpp
// C3420.cpp
// compile with: /clr /c
ref class R {
   virtual !R() {}   // C3420
};
```
