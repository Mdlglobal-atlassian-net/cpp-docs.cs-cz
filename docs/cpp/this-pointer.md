---
title: this ukazatel
description: Ukazatel this je ukazatel generovaný kompilátorem na aktuální objekt v nestatických členských funkcích.
ms.date: 01/22/2020
f1_keywords:
- this_cpp
helpviewer_keywords:
- nonstatic member functions [C++]
- pointers, to class instance
- this pointer
ms.assetid: 92e3256a-4ad9-4d46-8be1-d77fad90791f
no-loc:
- this
- class
- struct
- union
- sizeof
- const
- volatile
ms.openlocfilehash: 58bba2edd7a457c624b747b5a65d209995852848
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518332"
---
# <a name="opno-locthis-pointer"></a>this ukazatel

Ukazatel **this** je ukazatel přístupný pouze v rámci nestatických členských funkcí **class** , **struct** nebo **union** typu. Odkazuje na objekt, pro který je členská funkce volána. Statické členské funkce nemají ukazatel **this** .

## <a name="syntax"></a>Syntaxe

```cpp
this
this->member-identifier
```

## <a name="remarks"></a>Poznámky

Ukazatel **this** objektu není součástí samotného objektu. Nereflektuje se v důsledku příkazu **sizeof** objektu. Když je pro objekt volána nestatická členská funkce, kompilátor předá adresu objektu funkci jako skrytý argument. Například následující volání funkce:

```cpp
myDate.setMonth( 3 );
```

lze interpretovat jako:

```cpp
setMonth( &myDate, 3 );
```

Adresa objektu je v rámci členské funkce k dispozici jako ukazatel **this** . Většina použití ukazatele **this** je implicitní. Je právní, ale zbytečný, aby při odkazování na členy classpoužíval explicitní **this** . Příklad:

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

**this** ukazatel se používá také k ochraně proti odkazování na sebe:

```cpp
if (&Object != this) {
// do not execute in cases of self-reference
```

> [!NOTE]
> Protože ukazatel **this** není upravitelný, přiřazení k ukazateli **this** nejsou povolena. Dřívější implementace C++ povoleného přiřazení do **this** .

V některých případech se **this** ukazatel používá přímo – například pro manipulaci s referenčními strukturami, kde je vyžadována adresa aktuálního objektu.

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

    // assignment operator
    myBuf = yourBuf;

    // Display 'your buffer'
    myBuf.Display();
}
```

```Output
my buffer
your buffer
```

## <a name="type-of-the-opno-locthis-pointer"></a>Typ ukazatele this

Typ ukazatele **this** lze upravit v deklaraci funkce pomocí klíčových slov **const** a **volatile** . Chcete-li deklarovat funkci, která má některý z těchto atributů, přidejte klíčová slova za seznam argumentů funkce.

Vezměte v úvahu příklad:

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

Předchozí kód deklaruje členskou funkci `X`, ve které je ukazatel **this** považován za **const** ukazatel na objekt **const** . Lze použít kombinace možností *CV-mod-list* , ale vždy upraví objekt, na který odkazuje ukazatel **this** , nikoli ukazatel sám na sebe. Následující deklarace deklaruje `X`funkcí, kde je ukazatel **this** **const** ukazatel na objekt **const** :

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

Typ **this** v členské funkci je popsán následující syntaxí. *Seznam kvalifikátorů CV-list* je určen z deklarátor členské funkce. Může být **const** nebo **volatile** (nebo obojí). *class-Type* je název class:

[*CV-kvalifikátor-list*] *class\* typu* **const this**

Jinými slovy, **this** ukazatel je vždy const ukazatel. Nedá se znovu přiřadit.  Kvalifikátory **const** nebo **volatile** používané v deklaraci členské funkce se vztahují na instanci class **this** ukazatel myši v rozsahu této funkce.

Následující tabulka obsahuje další informace o tom, jak tyto modifikátory fungují.

### <a name="semantics-of-opno-locthis-modifiers"></a>Sémantika this modifikátory

|Modifikátor|Význam|
|--------------|-------------|
|**const**|Nelze změnit Členská data; nelze vyvolat členské funkce, které nejsou **const** .|
|**volatile**|Data členů jsou načtena z paměti pokaždé, když k ní dojde; zakáže určité optimalizace.|

Je to chyba při předání objektu **const** do členské funkce, která není **const** .

Podobně je také chyba předat objekt **volatile** členské funkci, která není **volatile** .

Členské funkce deklarované jako **const** nemohou měnit data členů – v takových funkcích je ukazatel **this** ukazatelem na objekt **const** .

> [!NOTE]
> Konstruktory a destruktory nelze deklarovat jako **const** nebo **volatile** . Lze je však vyvolat pro objekty **const** nebo **volatile** .

## <a name="see-also"></a>Viz také:

[Klíčová slova](../cpp/keywords-cpp.md)
