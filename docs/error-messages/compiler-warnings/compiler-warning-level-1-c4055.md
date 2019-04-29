---
title: Kompilátor upozornění (úroveň 1) C4052
ms.date: 11/04/2016
f1_keywords:
- C4055
helpviewer_keywords:
- C4055
ms.assetid: f9955421-16ab-46e5-8f9d-bf1639a519ef
ms.openlocfilehash: e9fcb4356d993d86b622fd49c4a75d587554f7c2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388602"
---
# <a name="compiler-warning-level-1-c4055"></a>Kompilátor upozornění (úroveň 1) C4055

> "*převod*': z ukazatele dat"*type1*"na ukazatel funkce"*type2*"

## <a name="remarks"></a>Poznámky

**Zastaralé:** Toto upozornění negenerují tak, že Visual Studio 2017 a novějších verzích.

Ukazatel na data (pravděpodobně nesprávně) přetypováno na ukazatel na funkci. Toto je upozornění úrovně 1 v části /Za a upozornění úrovně 4 v rámci/ze.

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

V rámci/ze Toto je upozornění úrovně 4.

```C
// C4055b.c
// compile with: /W4 /c
typedef int (*PFUNC)();
int *pi;
PFUNC f() {
return (PFUNC)pi;   // C4055
}
```
