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
ms.openlocfilehash: adffacc3ddc08679d7db4e17e027d8a7dbe8a92b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320321"
---
# <a name="pointers-to-members"></a>Ukazatelé na členy

Deklarace ukazatelů na členy jsou zvláštní případy deklarace ukazatele.  Jsou deklarovány pomocí následující sekvence:

> *specifikátory třídy úložiště*<sub>opt</sub> *cv-qualifiers*<sub>opt</sub> *type-specifier* *ms-modifikátor*<sub>opt</sub> *qualified-name* **`::*`** *cv-qualifiers*<sub>opt</sub> *identifier* *pm-initializer*<sub>opt</sub>**`;`**

1. Specifikátor deklarace:

   - Volitelný specifikátor třídy úložiště.

   - Volitelné **specifikátory const** a **volatile.**

   - Specifikátor typu: název typu. Je to typ člena, na který se má upozornit, ne na třídu.

1. Deklarátor:

   - Volitelný modifikátor specifický pro microsoft. Další informace naleznete [v tématu Modifikátory specifické pro společnost Microsoft](../cpp/microsoft-specific-modifiers.md).

   - Kvalifikovaný název třídy obsahující členy, na které se má upozornit.

   - Operátor. __`::`__

   - Operátor. __`*`__

   - Volitelné **specifikátory const** a **volatile.**

   - Identifikátor pojmenování ukazatele na člena.

1. Volitelný inicializátor ukazatele na člen:

   - Operátor. **`=`**

   - Operátor. **`&`**

   - Kvalifikovaný název třídy.

   - Operátor. __`::`__

   - Název nestatického člena třídy příslušného typu.

Jako vždy více deklarátory (a všechny přidružené inicializátory) jsou povoleny v jedné deklaraci. Ukazatel na člen nesmí odkazovat na statický člen třídy, člen **`void`** typu odkazu nebo .

Ukazatel na člen třídy se liší od normální ukazatel: má informace o typu pro typ člena a pro třídu, do které patří člen. Normální ukazatel identifikuje (má adresu) pouze jeden objekt v paměti. Ukazatel na člena třídy identifikuje tohoto člena v libovolné instanci třídy. Následující příklad deklaruje třídu `Window`a některé ukazatele na data členů.

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

V předchozím příkladu `pwCaption` je ukazatel na všechny `Window` členy třídy, který je typu `char*`. Typ `pwCaption` je `char * Window::*`. Další fragment kódu deklaruje ukazatele na `SetCaption` členské funkce a. `GetCaption`

```cpp
const char * (Window::*pfnwGC)() = &Window::GetCaption;
bool (Window::*pfnwSC)( const char * ) = &Window::SetCaption;
```

`pfnwGC` Ukazatele a `pfnwSC` přejděte `GetCaption` `SetCaption` na `Window` a třídy, v uvedeném pořadí. Kód zkopíruje informace do titulku okna `pwCaption`přímo pomocí ukazatele na člen :

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

Rozdíl mezi **`.*`** operátory a **`->*`** (operátory ukazatele na členy) spočá, že **`.*`** operátor vybere **`->*`** členy dané odkaz na objekt nebo objekt, zatímco operátor vybere členy prostřednictvím ukazatele. Další informace o těchto operátorech naleznete v [tématu Výrazy s operátory ukazatele na člen](../cpp/pointer-to-member-operators-dot-star-and-star.md).

Výsledkem operátorů ukazatele na člen je typ člena. V tomto případě je `char *`to .

Následující fragment kódu vyvolá členské `GetCaption` `SetCaption` funkce a pomocí ukazatelů na členy:

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

Adresa statického člena není ukazatelem na člena. Je to pravidelný ukazatel na jednu instanci statického člena. Pouze jedna instance statického člena existuje pro všechny objekty dané třídy. To znamená, že můžete použít**&** běžné operátory<strong>\*</strong>address-of ( ) a dereference ( ).

## <a name="pointers-to-members-and-virtual-functions"></a>Ukazatelé na členy a virtuální funkce

Vyvolání virtuální funkce prostřednictvím funkce ukazatele na člen funguje, jako by funkce byla volána přímo. Správná funkce je vyhledána v tabulce v a vyvolána.

Klíč k fungování virtuálních funkcí je jako vždy volá prostřednictvím ukazatele na základní třídu. (Další informace o virtuálních funkcích naleznete [v tématu Virtuální funkce](../cpp/virtual-functions.md).)

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
