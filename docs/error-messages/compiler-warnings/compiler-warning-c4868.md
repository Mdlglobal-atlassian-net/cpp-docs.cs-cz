---
title: C4868 upozornění kompilátoru | Microsoft Docs
ms.date: 10/26/2017
ms.topic: error-reference
f1_keywords:
- C4868
ms.assetid: fc6aa7e5-34dd-4ec2-88bd-16e430361dc7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 922a1a8434da8449758b9d55ebe89ace2f262cd5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275239"
---
# <a name="compiler-warning-level-4-c4868"></a>C4868 kompilátoru upozornění (úroveň 4)

> '_soubor_(*line_number*), kompilátor nemusí vynutit pořadí vyhodnocení zleva doprava v seznamu braced inicializátoru

Prvky braced inicializátoru seznamu mají vyhodnoceny v pořadí zleva doprava. Existují dva případy, ve kterých je kompilátor nemůže zaručit, toto pořadí: první je při některé prvky jsou objekty předaná hodnota; Druhá je při kompilaci s `/clr` a některé prvky jsou pole objektů nebo prvků pole. Když kompilátor nemůže zaručit zleva doprava vyhodnocení vydá upozornění C4868.

Toto upozornění můžete vygenerovaného jako výsledek kompilátoru shoda práci, kterou bylo provedeno pro Visual C++ 2015 Update 2. Kód, který zkompiluje před Visual C++ 2015 Update 2 nyní můžete generovat C4868.

Toto upozornění je ve výchozím nastavení vypnutý. Použití `/Wall` aktivovat toto upozornění.

Chcete-li vyřešit toto upozornění, nejprve zvažte, jestli je to nutné, například při vyhodnocení elementů může být vedlejší účinky závislé na pořadí vyhodnocení zleva doprava inicializátoru seznamu elementů. V mnoha případech pořadí, ve kterém jsou vyhodnocovány elementy nemá pozorovatelné vliv.

Pokud pořadí vyhodnocování musí být zleva doprava, zvažte, pokud je možné předat elementy `const` referenční místo. Ke změně, například to eliminuje upozornění následující ukázka kódu.

## <a name="example"></a>Příklad

Tato ukázka generuje C4868 a ukazuje způsob, jak opravit:

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