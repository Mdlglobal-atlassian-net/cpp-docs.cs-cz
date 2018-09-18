---
title: Chyba kompilátoru C3492 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3492
dev_langs:
- C++
helpviewer_keywords:
- C3492
ms.assetid: b1dc6342-9133-4b1f-a9c3-e8c65d20d121
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 54b3689a6ee565788e2a469a8321727a9fdd822f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46089213"
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