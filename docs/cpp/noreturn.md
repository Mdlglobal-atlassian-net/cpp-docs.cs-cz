---
title: noreturn
ms.date: 11/04/2016
f1_keywords:
- noreturn_cpp
helpviewer_keywords:
- __declspec keyword [C++], noreturn
- noreturn __declspec keyword
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
ms.openlocfilehash: f9ca61c9d734ccdd6b8d8374ed3a7c4128ee3d5e
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857369"
---
# <a name="noreturn"></a>noreturn

**Specifické pro společnost Microsoft**

Tento atribut **__declspec** instruuje kompilátor, že funkce nevrací. V důsledku toho kompilátor ví, že kód po volání funkce **__declspec (vrácení zpět)** je nedosažitelný.

Pokud kompilátor najde funkci s cestou řízení, která nevrací hodnotu, vygeneruje upozornění (C4715) nebo chybovou zprávu (C2202). Pokud cesta k ovládacímu prvku není dostupná z důvodu funkce, která se nikdy nevrátí, můžete pomocí **__declspec (Return)** zabránit tomuto upozornění nebo chybě.

> [!NOTE]
>  Přidání **__declspec (návrat)** do funkce, jejíž vrácení se očekává, může způsobit nedefinované chování.

## <a name="example"></a>Příklad

V následující ukázce klauzule **Else** neobsahuje příkaz return.  Deklarace `fatal` jako **__declspec (návratová)** zabraňuje chybové zprávě nebo upozornění.

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

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[__declspec](../cpp/declspec.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)