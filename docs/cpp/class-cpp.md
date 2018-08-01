---
title: třídy (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- class_cpp
dev_langs:
- CPP
helpviewer_keywords:
- class types [C++], class statements
- class keyword [C++]
ms.assetid: dd23c09f-6598-4069-8bff-69c7f2518b9f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8a3c3defdfb882db69f7789c97feba11d346e540
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405583"
---
# <a name="class-c"></a>třída (C++)
**Třídy** – klíčové slovo deklaruje typ třídy nebo definuje objekt typu třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[template-spec]  
class [ms-decl-spec] [tag [: base-list ]]  
{  
   member-list  
} [declarators];  
[ class ] tag declarators;  
```  
  
#### <a name="parameters"></a>Parametry  
 *specifikace šablony*  
 Volitelné specifikace šablony. Další informace najdete v [šablony](templates-cpp.md).  
  
 *class*  
 **Třídy** – klíčové slovo.  
  
 *MS-decl-spec*  
 Volitelná specifikace paměťové třídy. Další informace najdete [__declspec](../cpp/declspec.md) – klíčové slovo.  
  
 *Značka*  
 Název typu daný pro třídu. Značka se změní vyhrazené slovo v rámci oboru třídy. Značka je volitelná. Pokud tento parametr vynechán, je definována anonymní třídy. Další informace najdete v tématu [anonymní typy třídy](../cpp/anonymous-class-types.md).  
  
 *Base-list*  
 Volitelný seznam tříd nebo struktur, které tato třída odvodí svoje členy z. Zobrazit [základní třídy](../cpp/base-classes.md) Další informace. Každý název základní třídy nebo struktury může být uvozen specifikátorem přístupu ([veřejné](../cpp/public-cpp.md), [privátní](../cpp/private-cpp.md), [chráněné](../cpp/protected-cpp.md)) a [virtuální](../cpp/virtual-cpp.md) klíčové slovo. Viz tabulka pro přístup ke členu [řízení přístupu ke členům třídy](member-access-control-cpp.md) Další informace.  
  
 *seznam členů*  
 Seznam členů třídy. Odkazovat na [přehled členů třídy](../cpp/class-member-overview.md) Další informace.  
  
 *deklarátory*  
 Seznam deklarátoru určující názvy jednu nebo více instancí typu třídy. Deklarátory mohou obsahovat inicializační seznamy, pokud jsou všechny datové členy třídy **veřejné**. To je běžné ve strukturách, jehož datové členy **veřejné** ve výchozím nastavení, než v třídách. Zobrazit [přehled Deklarátorů](../cpp/overview-of-declarators.md) Další informace.  
  
## <a name="remarks"></a>Poznámky  
 Další informace o třídách obecně odkazovat na jeden z následujících témat:  
  
-   [struct](../cpp/struct-cpp.md)  
  
-   [sjednocení](../cpp/unions.md)  
  
-   [__multiple_inheritance](../cpp/inheritance-keywords.md)  
  
-   [__single_inheritance](../cpp/inheritance-keywords.md)  
  
-   [__virtual_inheritance](../cpp/inheritance-keywords.md)  
  
 Informace o spravovaných třídách a strukturách naleznete v tématu [třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md)  
  
## <a name="example"></a>Příklad  
  
```cpp 
// class.cpp  
// compile with: /EHsc  
// Example of the class keyword  
// Exhibits polymorphism/virtual functions.  
  
#include <iostream>  
#include <string>  
#define TRUE = 1  
using namespace std;  
  
class dog  
{  
public:  
   dog()  
   {  
      _legs = 4;  
      _bark = true;  
   }  
  
   void setDogSize(string dogSize)  
   {  
      _dogSize = dogSize;  
   }  
   virtual void setEars(string type)      // virtual function  
   {  
      _earType = type;  
   }  
  
private:  
   string _dogSize, _earType;  
   int _legs;  
   bool _bark;  
  
};  
  
class breed : public dog  
{  
public:  
   breed( string color, string size)  
   {  
      _color = color;  
      setDogSize(size);  
   }  
  
   string getColor()  
   {  
      return _color;  
   }  
  
   // virtual function redefined  
   void setEars(string length, string type)  
   {  
      _earLength = length;  
      _earType = type;  
   }  
  
protected:  
   string _color, _earLength, _earType;  
};  
  
int main()  
{  
   dog mongrel;  
   breed labrador("yellow", "large");  
   mongrel.setEars("pointy");  
   labrador.setEars("long", "floppy");  
   cout << "Cody is a " << labrador.getColor() << " labrador" << endl;  
}  
```  
  
## <a name="see-also"></a>Viz také:  
 [klíčová slova](../cpp/keywords-cpp.md)   
 [Třídy a struktury](../cpp/classes-and-structs-cpp.md)