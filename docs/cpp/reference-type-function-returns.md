---
title: Vrácení funkce typu odkazu
ms.date: 11/04/2016
helpviewer_keywords:
- function return types [C++], reference type
- data types [C++], function return types
- functions [C++], return types
ms.assetid: 5b73be1d-2dc7-41df-ab0a-adcba36f2ad1
ms.openlocfilehash: 5e84643713dcbcb278fe7ce07c5d55f3593ec2ef
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188295"
---
# <a name="reference-type-function-returns"></a>Vrácení funkce typu odkazu

Funkce mohou být deklarovány, aby vracely typ odkazu. Existují dva důvody pro tuto deklaraci:

- Vrácené informace jsou dostatečně velkým objektem, takže vrácení odkazu je efektivnější než vrácení kopie.

- Typ funkce musí být l-hodnota.

- Odkazovaný objekt nebude při návratu funkce z oboru přecházet.

Stejně tak, jak může být efektivnější předat velké *objekty funkcím* odkazem, může být efektivnější vracet velké objekty *z* funkcí odkazem. Protokol vrácení odkazu eliminuje nutnost kopírování objektu do dočasného umístění před vrácením.

Typy vracející odkaz mohou být také užitečné, když se funkce musí vyhodnotit na l-hodnotu. Nejvíce přetížených operátorů patří do této kategorie, zejména operátor přiřazení. Přetížené operátory jsou pokryty v [přetížených operátorech](../cpp/operator-overloading.md).

## <a name="example"></a>Příklad

Vezměte v úvahu příklad typu `Point`:

```cpp
// refType_function_returns.cpp
// compile with: /EHsc

#include <iostream>
using namespace std;

class Point
{
public:
// Define "accessor" functions as
//  reference types.
unsigned& x();
unsigned& y();
private:
// Note that these are declared at class scope:
unsigned obj_x;
unsigned obj_y;
};

unsigned& Point :: x()
{
return obj_x;
}
unsigned& Point :: y()
{
return obj_y;
}

int main()
{
Point ThePoint;
// Use x() and y() as l-values.
ThePoint.x() = 7;
ThePoint.y() = 9;

// Use x() and y() as r-values.
cout << "x = " << ThePoint.x() << "\n"
<< "y = " << ThePoint.y() << "\n";
}
```

## <a name="output"></a>Výstup

```Output
x = 7
y = 9
```

Všimněte si, že funkce `x` a `y` jsou deklarovány, aby vracely odkazy. Tyto funkce lze použít na obou stranách příkazu přiřazení.

Všimněte si také, že v hlavním objektu ThePoint zůstane v oboru, a proto jsou jeho referenční členové stále aktivní a lze k nim bezpečně přistoupit.

Deklarace odkazů musí obsahovat inicializátory s výjimkou těchto případů:

- Explicitní **externí** deklarace

- Deklarace členu třídy

- Deklarace v rámci třídy

- Deklarace argumentu funkce nebo návratového typu funkce

## <a name="caution-returning-address-of-local"></a>Upozornění vracející adresu místního

Pokud deklarujete objekt v místním oboru, tento objekt bude zničen při návratu funkce. Vrátí-li funkce odkaz na tento objekt, bude tento odkaz pravděpodobně způsobovat porušení přístupu za běhu, pokud se volající pokusí použít odkaz s hodnotou null.

```cpp
// C4172 means Don’t do this!!!
Foo& GetFoo()
{
    Foo f;
    ...
    return f;
} // f is destroyed here
```

Kompilátor vydá upozornění v tomto případě: `warning C4172: returning address of local variable or temporary`. V jednoduchých programech je možné, že v případě, že volající je přístup k referenci před přepsáním umístění v paměti, dojde k chybě. Důvodem je Sheer štěstí. Heed upozornění.

## <a name="see-also"></a>Viz také

[Odkazy](../cpp/references-cpp.md)
