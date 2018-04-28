---
title: Kompilátoru (úroveň 1) upozornění C4052 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- C4055
dev_langs:
- C++
helpviewer_keywords:
- C4055
ms.assetid: f9955421-16ab-46e5-8f9d-bf1639a519ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 29b1c8bcc836e35f7b8b81954ef247527d8ec35e
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="compiler-warning-level-1-c4055"></a>C4055 kompilátoru upozornění (úroveň 1)

> '*převod*': z dat ukazatel '*type1*'to ukazatel na funkci'*type2*.

## <a name="remarks"></a>Poznámky

**Zastaralé:** není toto upozornění vygenerovaných Visual Studio 2017 a novější verze.

Ukazatel dat (pravděpodobně nesprávně) vložena do ukazatel na funkci. Toto je upozornění úrovně 1 v části /Za a úroveň 4 upozornění v části /Ze.

## <a name="example"></a>Příklad

Následující ukázka generuje C4055:

```C
// C4055.c
// compile with: /Za /W1 /c
typedef int (*PFUNC)();
int *pi;
PFUNC f() {
   return (PFUNC)pi;   // C4055
}
```

V části /Ze Toto je upozornění úroveň 4.

```C
// C4055b.c
// compile with: /W4 /c
typedef int (*PFUNC)();
int *pi;
PFUNC f() {
return (PFUNC)pi;   // C4055
}
```
