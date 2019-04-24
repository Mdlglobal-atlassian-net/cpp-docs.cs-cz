---
title: Chyba kompilátoru C3420
ms.date: 11/04/2016
f1_keywords:
- C3420
helpviewer_keywords:
- C3420
ms.assetid: 99b53c77-f36b-4574-9199-b53111becccb
ms.openlocfilehash: 3db109598ce0741ca34a230d8925994543bcb5ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182454"
---
# <a name="compiler-error-c3420"></a>Chyba kompilátoru C3420

"finalizační metody": finalizační metoda nemůže být virtuální

Finalizační metody lze volat pouze jiné prakticky z jeho nadřazeného typu. Proto jedná se o chybu deklarovat virtuální finalizační metodu.

Další informace najdete v tématu [destruktory a finalizační metody v tom, jak: Definice a používání tříd a struktur (C++vyhodnocovací)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

## <a name="example"></a>Příklad

Následující ukázka generuje C3420.

```
// C3420.cpp
// compile with: /clr /c
ref class R {
   virtual !R() {}   // C3420
};
```