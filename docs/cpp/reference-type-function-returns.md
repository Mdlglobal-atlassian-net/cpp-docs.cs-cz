---
title: Vrácení funkce typu odkazu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function return types [C++], reference type
- data types [C++], function return types
- functions [C++], return types
ms.assetid: 5b73be1d-2dc7-41df-ab0a-adcba36f2ad1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 867313625ccc90924eed0c0c9405970f2cb90f8a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="reference-type-function-returns"></a>Vrácení funkce typu odkazu
Funkce mohou být deklarovány, aby vracely typ odkazu. Existují dva důvody pro tuto deklaraci:  
  
-   Vrácené informace jsou dostatečně velkým objektem, takže vrácení odkazu je efektivnější než vrácení kopie.  
  
-   Typ funkce musí být l-hodnota.  
  
-   Když funkce vrátí hodnotu, nebude odkazuje na objekt dostala mimo rozsah.  
  
 Stejně jako může být efektivnější předat rozsáhlé objekty *k* funkce odkazem také může být efektivnější vrátit rozsáhlé objekty *z* funkce odkazem. Protokol vrácení odkazu eliminuje nutnost kopírování objektu do dočasného umístění před vrácením.  
  
 Typy vracející odkaz mohou být také užitečné, když se funkce musí vyhodnotit na l-hodnotu. Nejvíce přetížených operátorů patří do této kategorie, zejména operátor přiřazení. Operátory Přetěžované jsou popsané v [přetížený operátory](../cpp/operator-overloading.md).  
  
## <a name="example"></a>Příklad  
 Vezměte v úvahu příklad typu `Point`:  
  
```  
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
  
```  
x = 7  
y = 9  
```  
  
 Všimněte si, že funkce `x` a `y` jsou deklarovány, aby vracely odkazy. Tyto funkce lze použít na obou stranách příkazu přiřazení.  
  
 Všimněte si také, že v hlavní, ThePoint objekt zůstává v oboru, a proto její členy odkaz jsou stále aktivní byla bezpečně přístupná.  
  
 Deklarace odkazů musí obsahovat inicializátory s výjimkou těchto případů:  
  
-   Explicitní deklarace pomocí klíčového slova `extern`  
  
-   Deklarace členu třídy  
  
-   Deklarace v rámci třídy  
  
-   Deklarace argumentu funkce nebo návratového typu funkce  
  
## <a name="caution-returning-address-of-local"></a>Upozornění: vrácení adresu místní  
 Pokud jste deklarace objektu na místní obor, budou při funkce vrátí hodnotu zničena tento objekt. Pokud funkce vrátí odkaz na tento objekt, které odkazují pravděpodobně způsobit narušení přístupu za běhu, pokud volající pokusí použít odkaz na hodnotu null.  
  
```  
// C4172 means Don’t do this!!!  
Foo& GetFoo()  
{  
    Foo f;  
    ...  
    return f;  
} // f is destroyed here  
```  
  
 Vydá upozornění v tomto případě: `warning C4172: returning address of local variable or temporary`. V jednoduchých programy je možné, že příležitostně bez narušení přístupu dojde v případě odkaz přistupuje volající předtím, než se přepíše umístění v paměti. To je kvůli velkému štěstí. Věnujte pozornost upozornění.  
  
## <a name="see-also"></a>Viz také  
 [Odkazy](../cpp/references-cpp.md)