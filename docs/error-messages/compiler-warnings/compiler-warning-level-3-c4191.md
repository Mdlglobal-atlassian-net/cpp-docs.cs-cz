---
title: Upozornění kompilátoru (úroveň 3) C4191
ms.date: 11/04/2016
f1_keywords:
- C4191
helpviewer_keywords:
- C4191
ms.assetid: 576d3bc6-95b7-448a-af31-5d798452df09
ms.openlocfilehash: cd0d7dc57c8d3c94a52f72b536657bb3ea1c6b3a
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051881"
---
# <a name="compiler-warning-level-3-c4191"></a>Upozornění kompilátoru (úroveň 3) C4191

operátor/operace: nezabezpečený převod z typu výrazu na typ Required

Několik operací, které se týkají ukazatelů na funkce, se považují za nebezpečné:

- Typy funkcí s různými konvencemi volání.

- Typy funkcí s různými konvencemi vracení.

- Argumenty nebo návratové typy s různými velikostmi, kategorie typu nebo klasifikace.

- Lišící se délka seznamu argumentů (na `__cdecl`, pouze při přetypování z delšího seznamu na kratší seznam, i když je kratší, je vararg).

- Ukazatel na data (jiné než **void** <strong>\*</strong>) s aliasem na funkci.

- Jakýkoli jiný typ rozdílu, který by vrátil chybu nebo upozornění na `reinterpret_cast`.

Volání této funkce prostřednictvím ukazatele výsledku může způsobit zhroucení programu.

Toto upozornění je ve výchozím nastavení vypnuté. Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

Následující ukázka generuje C4191:

```cpp
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