---
title: Chyba kompilátoru C2384
ms.date: 11/04/2016
f1_keywords:
- C2384
helpviewer_keywords:
- C2384
ms.assetid: 8145f7ad-31b1-406d-ac43-0d557feab635
ms.openlocfilehash: 1909fb999dd0f60224029b726f773c11fa69ee40
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460317"
---
# <a name="compiler-error-c2384"></a>Chyba kompilátoru C2384

'member': nelze použít __declspec(thread) na člen spravované nebo třídy WinRT

[Vlákno](../../cpp/thread.md) `__declspec` modifikátor nejde použít u člena spravované nebo třídy Windows Runtime.

Statické vlákno místní úložiště ve spravovaném kódu lze použít pouze pro staticky načtené knihovny DLL, knihovnu DLL musí být staticky načteny při spuštění procesu. Modul Windows Runtime nepodporuje úložiště thread local.

Následující příkaz generuje C2384 a ukazuje, jak ho opravit v jazyce C + +/ CLI kódu:

```
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