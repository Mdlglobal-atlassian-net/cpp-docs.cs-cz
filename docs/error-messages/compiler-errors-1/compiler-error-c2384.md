---
title: Chyba kompilátoru C2384
ms.date: 11/04/2016
f1_keywords:
- C2384
helpviewer_keywords:
- C2384
ms.assetid: 8145f7ad-31b1-406d-ac43-0d557feab635
ms.openlocfilehash: 2ce5c2f2540fbd2aca3509fa1dac55073a002abb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745259"
---
# <a name="compiler-error-c2384"></a>Chyba kompilátoru C2384

member: nejde použít __declspec (thread) na člen spravované třídy nebo třídy WinRT.

Modifikátor `__declspec` [vlákna](../../cpp/thread.md) nelze použít na členu spravované nebo prostředí Windows Runtime třídy.

Statické thread local úložiště ve spravovaném kódu lze použít pouze pro staticky načtené knihovny DLL – knihovna DLL musí být staticky načtena při spuštění procesu. Prostředí Windows Runtime nepodporuje úložiště thread local.

Následující řádek generuje C2384 a ukazuje, jak ho opravit v C++kódu/CLI:

```cpp
// C2384.cpp
// compile with: /clr /c
public ref class B {
public:
   __declspec( thread ) static int tls_i = 1;   // C2384

   // OK - declare with attribute instead
   [System::ThreadStaticAttribute]
   static int tls_j;
};
```
