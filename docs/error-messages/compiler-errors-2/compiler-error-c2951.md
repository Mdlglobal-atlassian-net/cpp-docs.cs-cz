---
title: Chyba kompilátoru C2951
ms.date: 11/04/2016
f1_keywords:
- C2951
helpviewer_keywords:
- C2951
ms.assetid: c6f95aa2-c894-425b-a51c-d40d70c8daa1
ms.openlocfilehash: dbc7186edfce6cc12a38fb2fc1dda08ac4a181c7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638695"
---
# <a name="compiler-error-c2951"></a>Chyba kompilátoru C2951

Typ deklarace jsou povolené jenom v globálním, oboru názvů nebo třídy

Nelze deklarovat obecného nebo šablony třídy mimo globální nebo obor názvů. Pokud v zahrnutém souboru deklaracích rozvrhy generic nebo šablonu, ujistěte se, že tento soubor je v globálním oboru.

Následující ukázka generuje C2951:

```
// C2951.cpp
template <class T>
class A {};

int main() {
   template <class T>   // C2951
   class B {};
}
```

C2951 může dojít také při použití obecných typů:

```
// C2951b.cpp
// compile with: /clr /c

// OK
generic <class T>
ref class GC { };

int main() {
   generic <class T> ref class GC2 {};   // C2951
}
```