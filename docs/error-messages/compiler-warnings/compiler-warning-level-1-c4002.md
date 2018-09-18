---
title: Upozornění (úroveň 1) C4002 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4002
dev_langs:
- C++
helpviewer_keywords:
- C4002
ms.assetid: 6bda1dfe-e2e4-4771-9794-5a404c466dd5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a3b3d51b4408e79236993d49f7ceba5fc9537b6d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050135"
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