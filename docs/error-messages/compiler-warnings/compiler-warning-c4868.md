---
title: Upozornění kompilátoru C4868
ms.date: 10/26/2017
f1_keywords:
- C4868
helpviewer_keywords:
- C4868
ms.assetid: fc6aa7e5-34dd-4ec2-88bd-16e430361dc7
ms.openlocfilehash: c1d49eb61a5c7c47fa83dacb39ed50f42e0fb147
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810482"
---
# <a name="compiler-warning-level-4-c4868"></a>Upozornění kompilátoru (úroveň 4) C4868

> kompilátor_File_(*Line_Number*) nemůže v seznamu inicializátorů v závorkách vyhovět pořadí vyhodnocování zleva doprava.

Prvky seznamu inicializátorů v závorkách se mají vyhodnotit v pořadí zleva doprava. Existují dva případy, kdy kompilátor nemůže zaručit toto pořadí: první z nich je v případě, že některé prvky jsou objekty předané hodnotou. druhý je při kompilaci s `/clr` a některé z prvků jsou pole objektů nebo prvky pole. Pokud kompilátor nemůže zaručit hodnocení zleva doprava, vygeneruje upozornění C4868.

Toto upozornění může být vygenerováno v důsledku práce s vyhovujícími kompilátory, které byly provedeny pro sadu Visual Studio 2015 Update 2. Kód, který se zkompiluje před aktualizací Visual Studio 2015 Update 2, teď může generovat C4868.

Toto upozornění je ve výchozím nastavení vypnuté. Toto upozornění můžete aktivovat pomocí `/Wall`.

Chcete-li vyřešit toto upozornění, nejprve zvažte, zda je nutné vyhodnotit zleva doprava prvků seznamu inicializátorů, například při vyhodnocování prvků mohou vzniknout vedlejší účinky závislé na objednávkách. V mnoha případech je pořadí, ve kterém jsou prvky vyhodnocovány, mít pozorovatelný efekt.

Pokud pořadí vyhodnocování musí být zleva doprava, zvažte, zda je možné předat prvky pomocí `const` odkazem. Tato změna například eliminuje upozornění v následující ukázce kódu.

## <a name="example"></a>Příklad

Tato ukázka generuje C4868 a ukazuje způsob, jak ji opravit:

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