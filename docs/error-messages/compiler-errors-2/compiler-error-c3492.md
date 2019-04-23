---
title: Chyba kompilátoru C3492
ms.date: 11/04/2016
f1_keywords:
- C3492
helpviewer_keywords:
- C3492
ms.assetid: b1dc6342-9133-4b1f-a9c3-e8c65d20d121
ms.openlocfilehash: facd8c78e775945924d77b09f9dc754bdc301ddd
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59038816"
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

## <a name="see-also"></a>Viz také:

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)