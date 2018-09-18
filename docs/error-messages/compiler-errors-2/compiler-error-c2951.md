---
title: Chyba kompilátoru C2951 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2951
dev_langs:
- C++
helpviewer_keywords:
- C2951
ms.assetid: c6f95aa2-c894-425b-a51c-d40d70c8daa1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6757256f08c5c1ed0a35fbf1c2a70776a4f2936
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074666"
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