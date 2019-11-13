---
title: Upozornění kompilátoru (úroveň 1) C4584
ms.date: 11/04/2016
f1_keywords:
- C4584
helpviewer_keywords:
- C4584
ms.assetid: ad86582f-cb8c-4d21-8c4c-a6c800059e25
ms.openlocfilehash: 831789f5295fcf91e83de3bd0bba12c8429e9fa3
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966239"
---
# <a name="compiler-warning-level-1-c4584"></a>Upozornění kompilátoru (úroveň 1) C4584

' Class1 ': základní třída ' Class2 ' je již základní třídou ' class3 '

Třída, kterou jste definovali, dědí ze dvou tříd, z nichž jeden dědí z druhé. Příklad:

```cpp
// C4584.cpp
// compile with: /W1 /LD
class A {
};

class B : public A {
};

class C : public A, public B { // C4584
};
```

V tomto případě by se upozornění vystavilo pro třídu C, protože dědí jak z třídy A, tak z třídy B, která také dědí ze třídy A. Toto upozornění slouží jako připomenutí, že musíte plně kvalifikovat použití členů z těchto základních tříd nebo dojde k vygenerování chyby kompilátoru z důvodu nejednoznačnosti, jakou člena třídy odkazujete.