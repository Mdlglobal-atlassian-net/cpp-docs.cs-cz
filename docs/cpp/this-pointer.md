---
title: this – ukazatel
ms.date: 11/04/2016
f1_keywords:
- this_cpp
helpviewer_keywords:
- nonstatic member functions [C++]
- pointers, to class instance
- this pointer
ms.assetid: 92e3256a-4ad9-4d46-8be1-d77fad90791f
ms.openlocfilehash: fb7198b22491a94eb2f00fecec83ec296ce03450
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535002"
---
# <a name="this-pointer"></a>this – ukazatel

**To** ukazatel je ukazatel přístupný pouze v rámci nestatické členské funkce **třídy**, **struktura**, nebo **sjednocení** typu. Odkazuje na objekt, pro který je členská funkce volána. Statické členské funkce nemají **to** ukazatele.

## <a name="syntax"></a>Syntaxe

```
this 
this->member-identifier
```

## <a name="remarks"></a>Poznámky

Objektu **to** ukazatel není součástí objektu samotného, není zohledněn ve výsledku **sizeof** příkaz v objektu. Při volání nestatické členské funkce objektu je namísto toho adresa objektu kompilátorem předána funkci jako skrytý argument. Například následující volání funkce:

```cpp
myDate.setMonth( 3 );
```

lze interpretovat takto:

```cpp
setMonth( &myDate, 3 );
```

Adresa objektu je dostupné v rámci členská funkce, jako **to** ukazatele. Většina použití **to** jsou implicitní. Je možné, i když je to nezbytné, explicitně **to** k odkazování na členy třídy. Příklad:

```cpp
void Date::setMonth( int mn )
{
   month = mn;            // These three statements
   this->month = mn;      // are equivalent
   (*this).month = mn;
}
```

Výraz `*this` se běžně používá k vrácení aktuálního objektu z členské funkce:

```cpp
return *this;
```

**To** ukazatel slouží také pro ochranu proti odkazů na sebe sama:

```cpp
if (&Object != this) {
// do not execute in cases of self-reference
```

> [!NOTE]
>  Protože **to** ukazatel je neupravitelnými, přiřazení **to** nejsou povoleny. Starší implementace jazyka C++ umožňovaly přiřazení k **to**.

V některých případech **to** ukazatel je přímo použít – například k manipulaci s daty odkazující na sebe struktury, ve kterém jsou vyžadována adresa aktuálního objektu.

## <a name="example"></a>Příklad

```cpp
// this_pointer.cpp
// compile with: /EHsc

#include <iostream>
#include <string.h>

using namespace std;

class Buf
{
public:
    Buf( char* szBuffer, size_t sizeOfBuffer );
    Buf& operator=( const Buf & );
    void Display() { cout << buffer << endl; }

private:
    char*   buffer;
    size_t  sizeOfBuffer;
};

Buf::Buf( char* szBuffer, size_t sizeOfBuffer )
{
    sizeOfBuffer++; // account for a NULL terminator

    buffer = new char[ sizeOfBuffer ];
    if (buffer)
    {
        strcpy_s( buffer, sizeOfBuffer, szBuffer );
        sizeOfBuffer = sizeOfBuffer;
    }
}

Buf& Buf::operator=( const Buf &otherbuf )
{
    if( &otherbuf != this )
    {
        if (buffer)
            delete [] buffer;

        sizeOfBuffer =  strlen( otherbuf.buffer ) + 1;
        buffer = new char[sizeOfBuffer];
        strcpy_s( buffer, sizeOfBuffer, otherbuf.buffer );
    }
    return *this;
}

int main()
{
    Buf myBuf( "my buffer", 10 );
    Buf yourBuf( "your buffer", 12 );

    // Display 'my buffer'
    myBuf.Display();

    // assignment opperator
    myBuf = yourBuf;

    // Display 'your buffer'
    myBuf.Display();
}
```

```Output
my buffer
your buffer
```

## <a name="type-of-the-this-pointer"></a>Typ tohoto ukazatele

**To** typ ukazatele, lze upravit v deklaraci funkce **const** a **volatile** klíčová slova. Chcete-li deklarovat funkci tak, aby měla atributy jednoho nebo více těchto klíčových slov, přidejte tato klíčová slova za seznam argumentů funkce.

Podívejte se například:

```cpp
// type_of_this_pointer1.cpp
class Point
{
    unsigned X() const;
};
int main()
{
}
```

Předchozí kód deklaruje členskou funkci, `X`, ve kterém **to** je považován za ukazatel **const** ukazatel na **const** objektu. Kombinace *cv-mod-list* možnosti se dají použít, ale ty vždy upravují objekt, na které odkazuje **to**, nikoli **to** ukazatel sám. Proto následující deklarace deklaruje funkci `X`; **to** je ukazatel **const** ukazatel na **const** objektu:

```cpp
// type_of_this_pointer2.cpp
class Point
{
    unsigned X() const;
};
int main()
{
}
```

Typ **to** v členské funkci je popsán následující syntaxí, kde *cv-qualifier-list* je určen z deklarátorů členských funkcí a může být **const**nebo **volatile** (nebo obojí), a *typu třídy* je název třídy:

*[cv-qualifier-list] typu třídy* **&#42; const to**

Jinými slovy **to** je vždy konstantním ukazatelem; nelze přiřadit.  **Const** nebo **volatile** kvalifikátory použít v deklaracích členských funkcí platí pro instanci třídy, na které odkazuje **to** v rozsahu dané funkce.

Následující tabulka obsahuje další informace o tom, jak tyto modifikátory fungují.

### <a name="semantics-of-this-modifiers"></a>Sémantika modifikátorů this

|Modifikátor|Význam|
|--------------|-------------|
|**const**|Nelze změnit členská data; Nelze vyvolat členskou funkci, která nejsou **const**.|
|**volatile**|Členská data jsou načtena z paměti při každém přístupu k nim. Zakáže některé optimalizace.|

Jedná se o chybu k předání **const** objektu na členskou funkci, která není **const**. Obdobně je chybou předání **volatile** objektu na členskou funkci, která není **volatile**.

Členské funkce deklarované jako **const** nemohou změnit členská data – v takových funkcích **to** je ukazatel na ukazatel **const** objektu.

> [!NOTE]
>  Konstruktory a destruktory nelze deklarovat jako **const** nebo **volatile**. Může však být vyvolána při **const** nebo **volatile** objekty.

## <a name="see-also"></a>Viz také:

[Klíčová slova](../cpp/keywords-cpp.md)