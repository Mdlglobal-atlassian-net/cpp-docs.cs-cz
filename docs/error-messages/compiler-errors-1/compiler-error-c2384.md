---
title: Chyba kompilátoru C2384 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2384
dev_langs:
- C++
helpviewer_keywords:
- C2384
ms.assetid: 8145f7ad-31b1-406d-ac43-0d557feab635
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f3aa9ec8a6a94f53123c443a1149df7cdbc95c83
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020456"
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