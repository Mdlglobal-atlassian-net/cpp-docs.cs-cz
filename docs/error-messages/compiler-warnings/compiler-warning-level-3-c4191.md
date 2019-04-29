---
title: Kompilátor upozornění (úroveň 3) C4191
ms.date: 11/04/2016
f1_keywords:
- C4191
helpviewer_keywords:
- C4191
ms.assetid: 576d3bc6-95b7-448a-af31-5d798452df09
ms.openlocfilehash: 72a485811647911207b6d048c686acdadd142b65
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402252"
---
# <a name="compiler-warning-level-3-c4191"></a>Kompilátor upozornění (úroveň 3) C4191

' operator/operation': nebezpečný převod z 'type of expression' na 'type required'

Několik operací zahrnující ukazatele na funkce považovány za nebezpečné:

- Typy funkcí pomocí různých konvencí volání.

- Typy funkcí s různými vrácení konvence.

- Argument nebo návratových typů pomocí různých velikostí, typ kategorie a klasifikace.

- Rozdílné délky seznamu argumentů (na `__cdecl`pouze na přetypování z delší seznam do seznamu kratší, i pokud kratší je vararg).

- Ukazatel na data (jiné než **void**<strong>\*</strong>) alias na ukazatel na funkci.

- Další rozdíl typ, který povede k chybě nebo upozornění na `reinterpret_cast`.

Volání této funkce přes ukazatel výsledku může způsobit pád programu.

Toto upozornění je vypnuto ve výchozím nastavení. Zobrazit [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.

Následující ukázka generuje C4191:

```
// C4191.cpp
// compile with: /W3 /clr
#pragma warning(default: 4191)

void __clrcall f1() { }
void __cdecl   f2() { }

typedef void (__clrcall * fnptr1)();
typedef void (__cdecl   * fnptr2)();

int main() {
   fnptr1 fp1 = static_cast<fnptr1>(&f1);
   fnptr2 fp2 = (fnptr2) &f2;

   fnptr1 fp3 = (fnptr1) &f2;   // C4191
   fnptr2 fp4 = (fnptr2) &f1;   // C4191
};
```