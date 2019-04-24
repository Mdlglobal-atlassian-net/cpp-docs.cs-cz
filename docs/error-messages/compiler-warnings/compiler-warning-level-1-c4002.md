---
title: Kompilátor upozornění (úroveň 1) C4002
ms.date: 11/04/2016
f1_keywords:
- C4002
helpviewer_keywords:
- C4002
ms.assetid: 6bda1dfe-e2e4-4771-9794-5a404c466dd5
ms.openlocfilehash: f2d2166a1370c02cfbc2346a63a424239ccb2b92
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187258"
---
# <a name="compiler-warning-level-1-c4002"></a>Kompilátor upozornění (úroveň 1) C4002

moc velký počet skutečných parametrů pro – makro 'identifier'

Počet skutečných parametrů v makru překračuje počet formálních parametrů v definici makra. Preprocesoru shromažďuje nadbytečné parametry ale bude je ignorovat při rozšíření makra.

C4002 může dojít, pokud nesprávně pomocí [Variadických maker](../../preprocessor/variadic-macros.md).

Následující ukázka generuje C4002:

```
// C4002.cpp
// compile with: /W1
#define test(a) (a)

int main() {
   int a = 1;
   int b = 2;
   a = test(a,b);   // C4002
   // try..
   a = test(a);
}
```

Tato chyba může být také generovány jako důsledek kompilátoru prací, které bylo provedeno pro Visual Studio .NET 2003: navíc čárkami v makru již nejsou přijata.

Kompilátor nebude přijímat další čárkami v makru. Kód je platný v aplikaci Visual Studio .NET 2003 a Visual Studio .NET verzí jazyka Visual C++ odeberte nadbytečné středníky.

```
// C4002b.cpp
// compile with: /W1
#define F(x,y)
int main()
{
   F(2,,,,,,3,,,,,,)   // C4002
   // Try the following line instead:
   // F(2,3)
}
```