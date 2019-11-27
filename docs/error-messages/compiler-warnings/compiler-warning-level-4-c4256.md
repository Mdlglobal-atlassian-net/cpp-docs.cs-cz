---
title: Upozornění kompilátoru (úroveň 4) C4256
ms.date: 11/04/2016
f1_keywords:
- C4256
helpviewer_keywords:
- C4256
ms.assetid: a755a32e-895a-4837-a2b5-4ea06b736798
ms.openlocfilehash: e087e3cd36ab85d6f3f6b5cfed1b55cac66ea142
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541699"
---
# <a name="compiler-warning-level-4-c4256"></a>Upozornění kompilátoru (úroveň 4) C4256

' function ': konstruktor pro třídu s virtuálními základy má '... '; volání nemusí být kompatibilní se staršími verzemi VisualC++

Možná nekompatibilita.

Vezměte v úvahu následující příklad kódu. Pokud byla definice konstruktoru S2:: S2 (int i,...) zkompilována pomocí verze kompilátoru od společnosti Microsoft C++ před verzí 7, ale následující příklad je zkompilován pomocí aktuální verze, volání konstruktoru pro S3 nebude správně fungovat z důvodu změny konvence volání speciálního případu. Pokud byly obě zkompilovány pomocí sady C++ Visual 6,0, volání nebudou fungovat úplně vpravo, pokud žádné parametry nebyly předány pro tři tečky.

Chcete-li toto upozornění opravit,

1. V konstruktoru nepoužívejte tři tečky.

1. Zajistěte, aby všechny komponenty v jejich projektu byly sestaveny s aktuální verzí (včetně všech knihoven, které mohou definovat nebo odkazovat na tuto třídu), a pak upozornění zakažte pomocí direktivy pragma [Warning](../../preprocessor/warning.md) .

Následující ukázka generuje C4256:

```cpp
// C4256.cpp
// compile with: /W4
// #pragma warning(disable : 4256)
struct S1
{
};

struct S2: virtual public S1
{
   S2( int i, ... )    // C4256
   {
      i = 0;
   }
   /*
   // try the following line instead
   S2( int i)
   {
      i = 0;
   }
   */
};

void func1()
{
   S2 S3( 2, 1, 2 );   // C4256
   // try the following line instead
   // S2 S3( 2 );
}

int main()
{
}
```