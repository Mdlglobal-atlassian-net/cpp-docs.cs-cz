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
ms.openlocfilehash: 3238cd801763c72e96ccd93eee9640e672a5fbf5
ms.sourcegitcommit: eff68e4e82be292a5664616b16a526df3e9d1cda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80150775"
---
# <a name="pointers-to-members"></a>Ukazatelé na členy

Deklarace ukazatelů na členy jsou zvláštními případy deklarací ukazatelů.  Jsou deklarovány pomocí následujícího pořadí:

> *specifikátory třídy úložiště*si pojmenují *kvalifikátory*<sub>opt</sub> *specifikátoru typu* <sub>opt-</sub> specifikátor *MS-modifikátor*<sub>opt</sub> *-Name* **`::*`** *kvalifikátory cv-* <sub>opt</sub> *ID* opt- *inicializátoru*<sub>opt</sub> **`;`**

1. Specifikátor deklarace:

   - Volitelný specifikátor třídy úložiště.

   - Volitelné specifikátory **const** a **volatile** .

   - Specifikátor typu: název typu. Je to typ člena, na který se má odkazovat, nikoli třída.

1. Deklarátor:

   - Volitelný modifikátor specifický pro společnost Microsoft. Další informace najdete v tématu [Modifikátory specifické pro společnost Microsoft](../cpp/microsoft-specific-modifiers.md).

   - Kvalifikovaný název třídy, která obsahuje členy, na které se má odkazovat.

   - Operátor __`::`__ .

   - Operátor __`*`__ .

   - Volitelné specifikátory **const** a **volatile** .

   - Identifikátor, který pojmenovává ukazatel na člen.

1. Volitelný inicializátor ukazatele na člena:

   - Operátor **`=`** .

   - Operátor **`&`** .

   - Kvalifikovaný název třídy.

   - Operátor __`::`__ .

   - Název nestatického člena třídy příslušného typu.

Jako vždy je v jedné deklaraci povoleno více deklarátory (a všech přidružených inicializátorů). Ukazatel na člen nemůže ukazovat na statický člen třídy, člen typu odkazu nebo **`void`** .

Ukazatel na člen třídy se liší od normálního ukazatele: má oba informace typu pro typ člena a třídu, ke které člen patří. Normální ukazatel identifikuje (má adresu) pouze jeden objekt v paměti. Ukazatel na člen třídy identifikuje tohoto člena v jakékoli instanci třídy. Následující příklad deklaruje třídu, `Window`a některé ukazatele na Členská data.

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

V předchozím příkladu je `pwCaption` ukazatel na libovolný člen třídy `Window`, který je typu `char*`. Typ `pwCaption` je `char * Window::* `. Další fragment kódu deklaruje ukazatele na `SetCaption` a `GetCaption` členské funkce.

```cpp
const char * (Window::*pfnwGC)() = &Window::GetCaption;
bool (Window::*pfnwSC)( const char * ) = &Window::SetCaption;
```

Ukazatele `pfnwGC` a `pfnwSC` ukazují na `GetCaption` a `SetCaption` třídy `Window` v uvedeném pořadí. Kód kopíruje informace do titulku okna přímo pomocí ukazatele na člen `pwCaption`:

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

Rozdíl mezi operátory **`.*`** a **`->*`** (operátory pointer-to-Member) je, že operátor **`.*`** vybere členy s odkazem na objekt nebo objekt, zatímco operátor **`->*`** vybere členy prostřednictvím ukazatele. Další informace o těchto operátorech naleznete v tématu [výrazy s operátory pointer-to-Member](../cpp/pointer-to-member-operators-dot-star-and-star.md).

Výsledek operátorů ukazatele na člena je typ člena. V tomto případě je to `char *`.

Následující fragment kódu vyvolá členské funkce `GetCaption` a `SetCaption` použití ukazatelů na členy:

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

Adresa statického člena není ukazatel na člen. Je to běžný ukazatel na jednu instanci statického člena. Pro všechny objekty dané třídy existuje pouze jedna instance statického člena. To znamená, že můžete používat běžné operátory adresy ( **&** ) a přereference (<strong>\*</strong>).

## <a name="pointers-to-members-and-virtual-functions"></a>Ukazatelé na členy a virtuální funkce

Volání virtuální funkce prostřednictvím funkce ukazatele na člen funguje, jako by byla funkce přímo volána. Správná funkce je vyhledána v tabulce v a vyvolána.

Klíč k fungování virtuálních funkcí je jako vždy volá prostřednictvím ukazatele na základní třídu. (Další informace o virtuálních funkcích najdete v tématu [virtuální funkce](../cpp/virtual-functions.md).)

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
