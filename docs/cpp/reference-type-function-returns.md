---
title: Vrácení funkce typu odkazu
ms.date: 11/04/2016
helpviewer_keywords:
- function return types [C++], reference type
- data types [C++], function return types
- functions [C++], return types
ms.assetid: 5b73be1d-2dc7-41df-ab0a-adcba36f2ad1
ms.openlocfilehash: a2d7fa9ddbc1d4a2f922b5a20930e150ae991f38
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461318"
---
# <a name="reference-type-function-returns"></a>Vrácení funkce typu odkazu

Funkce mohou být deklarovány, aby vracely typ odkazu. Existují dva důvody pro tuto deklaraci:

- Vrácené informace jsou dostatečně velkým objektem, takže vrácení odkazu je efektivnější než vrácení kopie.

- Typ funkce musí být l-hodnota.

- Odkazovaný objekt nebude dostanou mimo rozsah, když funkce vrátí.

Stejně jako může být efektivnější předat velké objekty *k* funkcí odkazem, také může být efektivnější velké objekty vrátit *z* funkcí odkazem. Protokol vrácení odkazu eliminuje nutnost kopírování objektu do dočasného umístění před vrácením.

Typy vracející odkaz mohou být také užitečné, když se funkce musí vyhodnotit na l-hodnotu. Nejvíce přetížených operátorů patří do této kategorie, zejména operátor přiřazení. Přetížené operátory jsou uvedeny v [přetížené operátory](../cpp/operator-overloading.md).

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

Všimněte si také, že ve funkci main, objekt ThePoint zůstává v oboru, a proto jeho členy odkazu jsou stále aktivní a mohli uživatelé bezpečně.

Deklarace odkazů musí obsahovat inicializátory s výjimkou těchto případů:

- Explicitní **extern** deklarace

- Deklarace členu třídy

- Deklarace v rámci třídy

- Deklarace argumentu funkce nebo návratového typu funkce

## <a name="caution-returning-address-of-local"></a>Upozornění: vrací adresu místní

Pokud deklarujete objekt v místním oboru, bude tento objekt zničen. když se funkce vrátí. Pokud funkce vrátí odkaz na tento objekt, tento odkaz pravděpodobně způsobit narušení přístupu za běhu, pokud volající pokusí použít nulový odkaz.

```cpp
// C4172 means Don’t do this!!!
Foo& GetFoo()
{
    Foo f;
    ...
    return f;
} // f is destroyed here
```

Kompilátor vyvolá upozornění v tomto případě: `warning C4172: returning address of local variable or temporary`. V jednoduchých aplikacích je možné, že v některých bez narušení přístupu dojde, pokud odkaz přistupuje volající předtím, než se přepíše umístění v paměti. Toto je kvůli velkému štěstí. Věnujte pozornost upozornění.

## <a name="see-also"></a>Viz také:

[Odkazy](../cpp/references-cpp.md)