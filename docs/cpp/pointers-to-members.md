---
title: "Ukazatelé na členy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declarations, pointers
- class members [C++], pointers to
- pointers, to members
- members [C++], pointers to
- pointers, declarations
ms.assetid: f42ddb79-9721-4e39-95b1-c56b55591f68
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 60ad14627abb5438526e97d6aea82127d107cfde
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="pointers-to-members"></a>Ukazatelé na členy
Deklarace ukazatelů členů jsou zvláštní případy deklarace ukazatelů.  Jsou deklarovány následujícím způsobem:  
  
```  
[storage-class-specifiers] [cv-qualifiers] type-specifiers [ms-modifier]qualified-name ::* [cv-qualifiers] identifier  
[= & qualified-name :: member-name];  
```  
  
1.  Specifikátor deklarace:  
  
    -   Specifikátor třídy úložiště volitelné.  
  
    -   Volitelné **const** nebo `volatile` specifikátory.  
  
    -   Specifikátor typu: název typu.  Jedná se o typ člena pro odkazovat, ne na třídu.  
  
2.  Deklarátor:  
  
    -   Volitelné Microsoft konkrétní modifikátor. Další informace najdete v tématu [Modifikátory specifické pro společnost Microsoft](../cpp/microsoft-specific-modifiers.md).  
  
    -   Kvalifikovaný název třídy obsahující členy odkazovat.   
  
    -   :: Operátor.  
  
    -    **\***  Operátor.  
  
    -   Volitelné **const** nebo `volatile` specifikátory.  
  
    -   Identifikátor pojmenování ukazatele na člena.  
  
    -   Inicializátoru volitelné:  
  
  **=**  Operátor.  
  
  **&**  Operátor.  
  
 Kvalifikovaný název třídy.  
  
 Operátor `::`.  
  
 Název nestatické členské třídy příslušného typu.  
  
 Jako vždy více deklarátor (a všechny přidružené inicializátory) jsou povoleny v jediné deklaraci.  
  
 Ukazatel na člena třídy se liší od normální ukazatel, protože obsahuje informace o typu pro typ člena a třídy, do které patří člen. Identifikuje normální ukazatel (má adresu) jenom jeden objekt v paměti. Ukazatel na člena třídy identifikuje tohoto člena v žádné instanci třídy. Následující příklad uvádí třídu, `Window`a některé ukazatele na člena data.  
  
```  
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
  
 V předchozím příkladu `pwCaption` ukazatel do kteréhokoli člena třídy `Window` který má typ **char\***. Typ `pwCaption` je `char * Window::*`. Deklaruje ukazatele na další fragment kódu `SetCaption` a `GetCaption` členské funkce.  
  
```  
const char * (Window::*pfnwGC)() = &Window::GetCaption;  
bool (Window::*pfnwSC)( const char * ) = &Window::SetCaption;  
```  
  
 Následující ukazatele `pfnwGC` a `pfnwSC` přejděte na příkaz `GetCaption` a `SetCaption` z `Window` třídy, v uvedeném pořadí. Kód zkopíruje informace na titulek okno přímo pomocí ukazatele na člena `pwCaption`:  
  
```  
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
  
 Rozdíl mezi **.\***  a  **-> \***  operátory (operátory ukazatelů na členy) je, že **.\***  operátor vybere členy zadaný objekt, nebo odkaz na objekt, při  **-> \***  operátor vybere členy prostřednictvím ukazatele. (Další informace o těchto operátorů najdete v tématu [výrazy s operátory ukazatelů na členy](../cpp/pointer-to-member-operators-dot-star-and-star.md).)  
  
 Typ člena je výsledek operátory ukazatelů na členy – v takovém případě **char \*** .  
  
 Následující fragment kódu vyvolá členské funkce `GetCaption` a `SetCaption` pomocí ukazatelé na členy:  
  
```  
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
 Adresa statického členu není ukazatelem na člen. Je běžným ukazatelem na jednu instanci statického členu. Vzhledem k tomu, že pro všechny objekty dané třídy, běžné adres of existuje pouze jedna instance je statický člen **(&)** a dereference **(\*)** operátory lze použít.  
  
## <a name="pointers-to-members-and-virtual-functions"></a>Ukazatelé na členy a virtuální funkce  
 Volání virtuální funkce pomocí funkce ukazatele na člen funguje, jako by byla tato funkce volána přímo. Správná funkce je vyhledána v tabulce a zavolána.  
  
 Klíč k fungování virtuálních funkcí je jako vždy volá prostřednictvím ukazatele na základní třídu. (Další informace o virtuálních funkcí najdete v tématu [virtuální funkce](../cpp/virtual-functions.md).)  
  
 Následující kód ukazuje, jak zavolat virtuální funkci pomocí funkce ukazatele na člen:  
  
```  
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
  
## <a name="see-also"></a>Viz také  
 