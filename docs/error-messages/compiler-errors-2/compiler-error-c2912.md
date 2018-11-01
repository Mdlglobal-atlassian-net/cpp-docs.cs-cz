---
title: Chyba kompilátoru C2912
ms.date: 11/04/2016
f1_keywords:
- C2912
helpviewer_keywords:
- C2912
ms.assetid: bd55cecd-ab1a-4636-ab8a-a00393fe7b3d
ms.openlocfilehash: b7f87ae2df5350fcfb2b7a662f517d8d7bd51ef8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50540072"
---
# <a name="compiler-error-c2912"></a>Chyba kompilátoru C2912

explicitní specializace "deklarace" není specializací šablony funkcí

Nejde specializovat nešablonové funkce.

Následující ukázka generuje C2912:

```
// C2912.cpp
// compile with: /c
void f(char);
template<> void f(char);   // C2912
template<class T> void f(T);   // OK
```

K této chybě také se vygeneruje jako výsledek kompilátoru prací, které bylo provedeno v aplikaci Visual Studio .NET 2003: pro každý explicitní specializace, je nutné vybrat parametry explicitní specializace tak, aby odpovídaly parametrům primární Šablona.

```
// C2912b.cpp
class CF {
public:
   template <class A> CF(const A& a) {}   // primary template

   // attempted explicit specialization
   template <> CF(const char* p) {}   // C2912

   // try the following line instead
   // template <> CF(const char& p) {}
};
```