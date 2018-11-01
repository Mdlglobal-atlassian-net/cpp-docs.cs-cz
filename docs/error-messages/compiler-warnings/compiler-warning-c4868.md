---
title: Upozornění kompilátoru C4868
ms.date: 10/26/2017
f1_keywords:
- C4868
ms.assetid: fc6aa7e5-34dd-4ec2-88bd-16e430361dc7
ms.openlocfilehash: d0bc8716e53e71c52f6a31036a95d0b4cefedd79
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481314"
---
# <a name="compiler-warning-level-4-c4868"></a>Upozornění (úroveň 4) kompilátoru C4868

> "_souboru_(*line_number*)' kompilátor nemůže vynutit pořadí vyhodnocování zleva doprava v seznamu inicializátorů v závorkách

Prvky seznamu inicializátorů v závorkách jsou vyhodnocovány v pořadí zleva doprava. Existují dva případy, ve kterých kompilátor nedokáže zaručit toto pořadí: první je při některé prvky jsou objekty, které jsou předávány hodnotou; Druhým je při kompilaci s `/clr` a některé prvky jsou pole objektů nebo prvků pole. Pokud kompilátor nemůže zaručit vyhodnocování zleva doprava vydá upozornění C4868.

Toto upozornění mohou být generovány jako důsledek kompilátoru prací, které bylo provedeno Visual C++ 2015 Update 2. Kód, který zkompiluje před Visual C++ 2015 Update 2 teď můžete vygenerovat C4868.

Toto upozornění je vypnuto ve výchozím nastavení. Použití `/Wall` k aktivaci tohoto upozornění.

Pokud chcete vyřešit toto upozornění, nejprve vezměte v úvahu, jestli je nezbytné, například při hodnocení prvků může vrátit vedlejší účinky závislé na pořadí vyhodnocování zleva doprava prvků seznamu inicializátorů. V mnoha případech nemá pořadí, ve kterém jsou vyhodnoceny prvky pozorovatelných vliv.

Pokud musí pořadí vyhodnocování zleva doprava, zvažte, pokud je možné předat prvky `const` odkazovat na místo. Změna takovou situaci eliminuje upozornění v následujícím příkladu kódu.

## <a name="example"></a>Příklad

Tato ukázka generuje C4868 a ukazuje způsob, jak ho opravit:

```cpp
// C4868.cpp
// compile with: /c /Wall
#include <cstdio>

class HasCopyConstructor
{
public:
    int x;

    HasCopyConstructor(int x): x(x) {}

    HasCopyConstructor(const HasCopyConstructor& h): x(h.x)
    {
        printf("Constructing %d\n", h.x);
    }
};

class TripWarning4868
{
public:
    // note that taking "HasCopyConstructor" parameters by-value will trigger copy-construction.
    TripWarning4868(HasCopyConstructor a, HasCopyConstructor b) {}

    // This variation will not trigger the warning:
    // TripWarning4868(const HasCopyConstructor& a, const HasCopyConstructor& b) {}
};

int main()
{
    HasCopyConstructor a{1};
    HasCopyConstructor b{2};

    // the warning will indicate the below line, the usage of the braced initializer list.
    TripWarning4868 warningOnThisLine{a, b};
};
```