---
title: Chyba kompilátoru C3492
ms.date: 11/04/2016
f1_keywords:
- C3492
helpviewer_keywords:
- C3492
ms.assetid: b1dc6342-9133-4b1f-a9c3-e8c65d20d121
ms.openlocfilehash: 53dd22368aee5e0de9eca1349eb4d7dd3ed1c570
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50485004"
---
# <a name="compiler-error-c3492"></a>Chyba kompilátoru C3492

'příkaz var': nejde zachytit člen anonymního sjednocení

Nejde zachytit člen Nepojmenovaná sjednocení.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Pojmenujte sjednocení a předat kompletní sjednocení struktura seznamu zachycení výrazu lambda.

## <a name="example"></a>Příklad

Následující příklad generuje C3492 vzhledem k tomu zachytí člena anonymního sjednocení:

```
// C3492a.cpp

int main()
{
   union
   {
      char ch;
      int x;
   };

   ch = 'y';
   [&x](char ch) { x = ch; }(ch); // C3492
}
```

## <a name="example"></a>Příklad

V následujícím příkladu řeší C3492 zadáním názvu unie a předáním kompletní sjednocení struktura seznamu zachycení výrazu lambda:

```
// C3492b.cpp

int main()
{
   union
   {
      char ch;
      int x;
   } u;

   u.ch = 'y';
   [&u](char ch) { u.x = ch; }(u.ch);
}
```

## <a name="see-also"></a>Viz také

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)