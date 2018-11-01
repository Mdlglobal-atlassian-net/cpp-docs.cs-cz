---
title: Chyba kompilátoru C3532
ms.date: 11/04/2016
f1_keywords:
- C3532
helpviewer_keywords:
- C3532
ms.assetid: 51067853-eda8-4f59-86e8-8924e16d3a95
ms.openlocfilehash: 91d8e28e053d8ce1b307f9345ab3249386bdf1ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568883"
---
# <a name="compiler-error-c3532"></a>Chyba kompilátoru C3532

'type': nesprávné použití 'auto'

Zadaný typ se nedá deklarovat pomocí `auto` – klíčové slovo. Například nelze použít `auto` – klíčové slovo Chcete-li deklarovat pole nebo metoda návratového typu.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Ujistěte se, že vrací výraz inicializace platného typu.

1. Ujistěte se, že není třeba deklarovat pole nebo návratový typ metody.

## <a name="example"></a>Příklad

Následující příklad provede C3532 vzhledem k tomu, `auto` – klíčové slovo nemůže deklarovat návratový typ metody.

```
// C3532a.cpp
// Compile with /Zc:auto
auto f(){}   // C3532
```

## <a name="example"></a>Příklad

Následující příklad provede C3532 vzhledem k tomu, `auto` – klíčové slovo nemůže deklarovat pole.

```
// C3532b.cpp
// Compile with /Zc:auto
int main()
{
   int x[5];
   auto a[5];            // C3532
   auto b[1][2];         // C3532
   auto y[5] = x;        // C3532
   auto z[] = {1, 2, 3}; // C3532
   auto w[] = x;         // C3532
   return 0;
}
```

## <a name="see-also"></a>Viz také

[Auto – klíčové slovo](../../cpp/auto-keyword.md)