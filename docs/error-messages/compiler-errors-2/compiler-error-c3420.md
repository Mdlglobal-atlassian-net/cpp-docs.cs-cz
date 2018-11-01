---
title: Chyba kompilátoru C3420
ms.date: 11/04/2016
f1_keywords:
- C3420
helpviewer_keywords:
- C3420
ms.assetid: 99b53c77-f36b-4574-9199-b53111becccb
ms.openlocfilehash: 3db109598ce0741ca34a230d8925994543bcb5ea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50645936"
---
# <a name="compiler-error-c3420"></a>Chyba kompilátoru C3420

"finalizační metody": finalizační metoda nemůže být virtuální

Finalizační metody lze volat pouze jiné prakticky z jeho nadřazeného typu. Proto jedná se o chybu deklarovat virtuální finalizační metodu.

Další informace najdete v tématu [destruktory a finalizační metody v tom, jak: definice a používání tříd a struktur (C + +/ CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

## <a name="example"></a>Příklad

Následující ukázka generuje C3420.

```
// C3420.cpp
// compile with: /clr /c
ref class R {
   virtual !R() {}   // C3420
};
```