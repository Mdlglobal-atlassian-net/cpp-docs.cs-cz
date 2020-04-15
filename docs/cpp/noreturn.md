---
title: noreturn
ms.date: 11/04/2016
f1_keywords:
- noreturn_cpp
helpviewer_keywords:
- __declspec keyword [C++], noreturn
- noreturn __declspec keyword
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
ms.openlocfilehash: a30840aa0556a7324ba24c0f2aaec57dea88d082
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367854"
---
# <a name="noreturn"></a>noreturn

**Specifické pro Microsoft**

Tento **atribut __declspec** říká kompilátoru, že funkce nevrátí. V důsledku toho kompilátor ví, že kód následující volání **funkce __declspec(noreturn)** je nedostupný.

Pokud kompilátor najde funkci s cestou řízení, která nevrací hodnotu, vygeneruje upozornění (C4715) nebo chybovou zprávu (C2202). Pokud cesta ovládacího prvku nelze dosáhnout z důvodu funkce, která se nikdy nevrátí, můžete použít **__declspec(noreturn)** zabránit toto upozornění nebo chyba.

> [!NOTE]
> Přidání **__declspec(noreturn)** k funkci, která se očekává, že vrátí může mít za následek nedefinované chování.

## <a name="example"></a>Příklad

V následující ukázce klauzule **else** neobsahuje příkaz return.  Deklarování `fatal` jako **__declspec(noreturn)** zabrání chybě nebo varovné zprávy.

```cpp
// noreturn2.cpp
__declspec(noreturn) extern void fatal () {}

int main() {
   if(1)
     return 1;
   else if(0)
     return 0;
   else
     fatal();
}
```

**END Microsoft Specifické**

## <a name="see-also"></a>Viz také

[__declspec](../cpp/declspec.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
