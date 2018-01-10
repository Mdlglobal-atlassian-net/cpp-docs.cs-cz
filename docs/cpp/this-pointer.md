---
title: Ukazatel this | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: this_cpp
dev_langs: C++
helpviewer_keywords:
- nonstatic member functions [C++]
- pointers, to class instance
- this pointer
ms.assetid: 92e3256a-4ad9-4d46-8be1-d77fad90791f
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 814e7518c6ed7052abc93b9e4705be93172b1e7f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="this-pointer"></a>this – ukazatel
**To** ukazatel je přístupné pouze v rámci nestatické členské funkce ukazatel **třída**, `struct`, nebo **– typ union** typu. Odkazuje na objekt, pro který je členská funkce volána. Statické členské funkce nemají **to** ukazatel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      this   
this->member-identifier  
```  
  
## <a name="remarks"></a>Poznámky  
 Objektu **to** ukazatel není součástí samotného; objektu se nereflektují v výsledek `sizeof` příkaz na objekt. Při volání nestatické členské funkce objektu je namísto toho adresa objektu kompilátorem předána funkci jako skrytý argument. Například následující volání funkce:  
  
```  
myDate.setMonth( 3 );  
```  
  
 lze interpretovat takto:  
  
```  
setMonth( &myDate, 3 );  
```  
  
 Adresa objektu je k dispozici v rámci členská funkce jako **to** ukazatel. Většiny použití **to** jsou implicitní. Je právní, i když je zbytečné, explicitně povoleno používat **to** k odkazování na členy třídy. Příklad:  
  
```  
void Date::setMonth( int mn )  
{  
   month = mn;            // These three statements  
   this->month = mn;      // are equivalent  
   (*this).month = mn;  
}  
```  
  
 Výraz `*this` se běžně používá k vrácení aktuálního objektu z členské funkce:  
  
```  
return *this;  
```  
  
 **To** ukazatel slouží také k ochraně před odkaz na sebe sama:  
  
```  
if (&Object != this) {  
// do not execute in cases of self-reference  
```  
  
> [!NOTE]
>  Protože **to** ukazatel je neupravitelnými, přiřazení **to** nejsou povoleny. Starší implementace C++ povolené přiřazení **to**.  
  
 V některých případech **to** ukazatel slouží přímo – například k manipulaci s daty odkazující na sebe struktur, kde je požadována adresa aktuálního objektu.  
  
## <a name="example"></a>Příklad  
  
```  
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
 **To** typ ukazatele můžete upravit v deklaraci funkce pomocí **const** a `volatile` klíčová slova. Chcete-li deklarovat funkci tak, aby měla atributy jednoho nebo více těchto klíčových slov, přidejte tato klíčová slova za seznam argumentů funkce.  
  
 Vezměte v úvahu v tomto příkladu:  
  
```  
// type_of_this_pointer1.cpp  
class Point  
{  
    unsigned X() const;  
};  
int main()  
{  
}  
```  
  
 Předchozí kód deklaruje členské funkce `X`, ve kterém **to** ukazatel je považován za **const** ukazatel na **const** objektu. Kombinace *odchylka nákladů mod – seznam* možnosti mohou být použity, ale vždy upravovat objektu, na kterou odkazuje **to**, nikoli **to** ukazatel sám sebe. Proto následující prohlášení deklaruje funkce `X`; **to** ukazatel **const** ukazatel na **const** objektu:  
  
```  
// type_of_this_pointer2.cpp  
class Point  
{  
    unsigned X() const;  
};  
int main()  
{  
}  
```  
  
 Typ **to** v členem funkce je popsán v následující syntaxi, kde *odchylka nákladů. kvalifikátor seznamu* se určí na základě deklarátor funkce člen a může být **const**nebo **volatile** (nebo oba), a *typu třídy* je název třídy:  
  
 *Třída – typ [odchylka nákladů kvalifikátor seznamu]*  **\* const to**   
  
 Jinými slovy **to** je vždy const ukazatel; nelze přiřadit.  **Const** nebo `volatile` kvalifikátory použít v deklaraci funkce člen použít instance třídy, na kterou odkazuje **to** v rámci oboru této funkce.  
  
 Následující tabulka obsahuje další informace o tom, jak tyto modifikátory fungují.  
  
### <a name="semantics-of-this-modifiers"></a>Sémantika modifikátorů this  
  
|Modifikátor|Význam|  
|--------------|-------------|  
|**const**|Nelze změnit data člena; Nelze vyvolat členské funkce, které nejsou **const**.|  
|`volatile`|Členská data jsou načtena z paměti při každém přístupu k nim. Zakáže některé optimalizace.|  
  
 Jedná se o chybu, předávání **const** objekt členské funkce, která není **const**. Obdobně je chybou předání objektu `volatile` členské funkci, která neobsahuje modifikátor `volatile`.  
  
 Členské funkce deklarován jako **const** nelze změnit data člena – v takové funkce **to** ukazatel je ukazatel na **const** objektu.  
  
> [!NOTE]
>  Konstruktory a destruktory nelze deklarovat jako **const** nebo `volatile`. Může ale být vyvolána na **const** nebo `volatile` objekty.  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova](../cpp/keywords-cpp.md)   
 