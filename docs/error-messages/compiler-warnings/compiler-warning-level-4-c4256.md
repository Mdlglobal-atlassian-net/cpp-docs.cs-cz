---
title: Kompilátor upozornění (úroveň 4) C4256
ms.date: 11/04/2016
f1_keywords:
- C4256
helpviewer_keywords:
- C4256
ms.assetid: a755a32e-895a-4837-a2b5-4ea06b736798
ms.openlocfilehash: 3e8a3ab1b11c719730016e6a0cd248770cd89af8
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447771"
---
# <a name="compiler-warning-level-4-c4256"></a>Kompilátor upozornění (úroveň 4) C4256

'function': konstruktor pro třídu s virtuálními základy má '...'; volání nemusí být kompatibilní se staršími verzemi Visual C++

Je to možné nekompatibility.

Zvažte následující příklad kódu. Pokud definice konstruktoru S2::S2 (int i,...) byl zkompilován pomocí verze sady Microsoft C++ kompilátor před verze 7, ale následující příklad je zkompilován pomocí aktuální verze, volání konstruktoru pro S3 nebude správně fungovat. kvůli změně konvence volání zvláštní případy. Pokud obě byly zkompilovány pomocí Visual C++ 6.0, volání nebude fungovat v pořádku, pokud byly předány žádné parametry pro tři tečky.

Chcete-li opravit toto upozornění

1. Nepoužívejte tlačítko se třemi tečkami v konstruktoru.

1. Ujistěte se, že všechny součásti ve svém projektu jsou vytvořeny s aktuální verzí (včetně všech knihoven, které mohou definovat nebo odkazovat na tuto třídu) a potom zakázat pomocí upozornění [upozornění](../../preprocessor/warning.md) direktivy pragma.

Následující ukázka generuje C4256:

```
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