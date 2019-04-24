---
title: Ukazatelé na členy
ms.date: 11/04/2016
helpviewer_keywords:
- declarations, pointers
- class members [C++], pointers to
- pointers, to members
- members [C++], pointers to
- pointers, declarations
ms.assetid: f42ddb79-9721-4e39-95b1-c56b55591f68
ms.openlocfilehash: a15e519be14d9a05cb30a8c9282baccc87a5f35e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62267686"
---
# <a name="pointers-to-members"></a>Ukazatelé na členy

Deklarace ukazatelů na členy jsou zvláštní případy deklarace ukazatelů.  Jsou deklarovány následujícím způsobem:

```
[storage-class-specifiers] [cv-qualifiers] type-specifiers [ms-modifier]qualified-name ::* [cv-qualifiers] identifier
[= & qualified-name :: member-name];
```

1. Specifikátor deklarace:

   - Volitelný specifikátor paměťové třídy.

   - Volitelné **const** a/nebo **volatile** specifikátorů.

   - Specifikátor typu: název typu.  Jedná se o typ členu, který chcete zdůraznit, ne na třídu.

1. Deklarátor:

   - Volitelný specifický modifikátor Microsoft. Další informace najdete v tématu [Modifikátory specifické pro společnost Microsoft](../cpp/microsoft-specific-modifiers.md).

   - Kvalifikovaný název třídy obsahující odkazovala na členy.

   - __::__ Operátor.

   - __\*__ Operátor.

   - Volitelné **const** a/nebo **volatile** specifikátorů.

   - Identifikátor pojmenování ukazatel na člen.

1. Volitelný inicializátor:

   - **=** Operátor.

   - **&** Operátor.

   - Kvalifikovaný název třídy.

   - __::__ Operátor.

   - Název Nestatický člen třídy příslušného typu.

Jako vždy víc deklarátorů. (a všechny přidružené inicializátory) jsou povoleny v jedné deklaraci.

Ukazatel na člen třídy, se liší od normální ukazatel, protože obsahuje informace o typu pro typ člena a třídy, do které patří člena. Identifikuje normální ukazatel (má adresu) pouze jeden objekt v paměti. Ukazatel na člen třídy identifikuje člena v jakékoli instance třídy. Následující příklad deklaruje třídu, `Window`a některé ukazatele na člen data.

```cpp
// pointers_to_members1.cpp
class Window
{
public:
   Window();                               // Default constructor.
   Window( int x1, int y1,                 // Constructor specifying
   int x2, int y2 );                       //  window size.
bool SetCaption( const char *szTitle ); // Set window caption.
   const char *GetCaption();               // Get window caption.
   char *szWinCaption;                     // Window caption.
};

// Declare a pointer to the data member szWinCaption.
char * Window::* pwCaption = &Window::szWinCaption;
int main()
{
}
```

V předchozím příkladu `pwCaption` je ukazatel na člena třídy `Window` , který má typ `char*`. Typ `pwCaption` je `char * Window::* `. Další fragment kódu deklaruje ukazatele na `SetCaption` a `GetCaption` členské funkce.

```cpp
const char * (Window::*pfnwGC)() = &Window::GetCaption;
bool (Window::*pfnwSC)( const char * ) = &Window::SetCaption;
```

Ukazatelů `pfnwGC` a `pfnwSC` přejděte `GetCaption` a `SetCaption` z `Window` třídy, v uvedeném pořadí. Kód zkopíruje informace do titulek okna přímo pomocí ukazatele na člen `pwCaption`:

```cpp
Window wMainWindow;
Window *pwChildWindow = new Window;
char   *szUntitled    = "Untitled -  ";
int    cUntitledLen   = strlen( szUntitled );

strcpy_s( wMainWindow.*pwCaption, cUntitledLen, szUntitled );
(wMainWindow.*pwCaption)[cUntitledLen - 1] = '1';     //same as
//wMainWindow.SzWinCaption [cUntitledLen - 1] = '1';
strcpy_s( pwChildWindow->*pwCaption, cUntitledLen, szUntitled );
(pwChildWindow->*pwCaption)[cUntitledLen - 1] = '2'; //same as //pwChildWindow->szWinCaption[cUntitledLen - 1] = '2';
```

Rozdíl mezi **.** <strong>\*</strong> a **->** <strong>\*</strong> operátory (operátory pointer-to-member) je, že **.** <strong>\*</strong> operátor vybere členů zadaný objekt nebo odkaz na objekt, zatímco **->** <strong>\*</strong> – operátor vybere členy prostřednictvím ukazatele. (Další informace o těchto operátorech naleznete v tématu [výrazy s operátory Pointer-to-Member](../cpp/pointer-to-member-operators-dot-star-and-star.md).)

Typ člena je výsledek operátory pointer-to-member – v takovém případě `char *`.

Následující fragment kódu vyvolává členské funkce `GetCaption` a `SetCaption` pomocí ukazatele na členy:

```cpp
// Allocate a buffer.
enum {
    sizeOfBuffer = 100
};
char szCaptionBase[sizeOfBuffer];

// Copy the main window caption into the buffer
//  and append " [View 1]".
strcpy_s( szCaptionBase, sizeOfBuffer, (wMainWindow.*pfnwGC)() );
strcat_s( szCaptionBase, sizeOfBuffer, " [View 1]" );
// Set the child window's caption.
(pwChildWindow->*pfnwSC)( szCaptionBase );
```

## <a name="restrictions-on-pointers-to-members"></a>Omezení ukazatelů členů

Adresa statického členu není ukazatelem na člen. Je běžným ukazatelem na jednu instanci statického členu. Vzhledem k tomu, že existuje pouze jedna instance statického členu pro všechny objekty dané třídy, běžné adresa of (**&**) a přístupu přes ukazatel (<strong>\*</strong>) operátory lze používat.

## <a name="pointers-to-members-and-virtual-functions"></a>Ukazatelé na členy a virtuální funkce

Volání virtuální funkce pomocí funkce ukazatele na člen funguje, jako by byla tato funkce volána přímo. Správná funkce je vyhledána v tabulce a zavolána.

Klíč k fungování virtuálních funkcí je jako vždy volá prostřednictvím ukazatele na základní třídu. (Další informace o virtuálních funkcích naleznete v tématu [virtuální funkce](../cpp/virtual-functions.md).)

Následující kód ukazuje, jak zavolat virtuální funkci pomocí funkce ukazatele na člen:

```cpp
// virtual_functions.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

class Base
{
    public:
    virtual void Print();
};
void (Base ::* bfnPrint)() = &Base :: Print;
void Base :: Print()
{
    cout << "Print function for class Base\n";
}

class Derived : public Base
{
    public:
    void Print();  // Print is still a virtual function.
};

void Derived :: Print()
{
    cout << "Print function for class Derived\n";
}

int main()
{
    Base   *bPtr;
    Base    bObject;
    Derived dObject;
    bPtr = &bObject;    // Set pointer to address of bObject.
    (bPtr->*bfnPrint)();
    bPtr = &dObject;    // Set pointer to address of dObject.
    (bPtr->*bfnPrint)();
}

//Output: Print function for class Base
Print function for class Derived
```