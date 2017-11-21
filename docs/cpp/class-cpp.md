---
title: "třídy (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: class_cpp
dev_langs: C++
helpviewer_keywords:
- class types [C++], class statements
- class keyword [C++]
ms.assetid: dd23c09f-6598-4069-8bff-69c7f2518b9f
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 43ceb1a6f2f2830f042ab2989839763cdf581ade
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="class-c"></a>třída (C++)
`class` – Klíčové slovo deklaruje typu třídy nebo definuje objekt typu třídy.  
  
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
 `template-spec`  
 Volitelné specifikace šablony. Další informace najdete v části [šablony](templates-cpp.md).  
  
 `class`  
 `class` – Klíčové slovo.  
  
 `ms-decl-spec`  
 Volitelná specifikace paměťové třídy. Další informace najdete v části [__declspec](../cpp/declspec.md) – klíčové slovo.  
  
 `tag`  
 Název typu pro třídu. Značka se stane vyhrazené slovo v rámci oboru třídy. Značka je volitelná. Pokud tento parametr vynechán, je definována třídu anonymní. Další informace najdete v tématu [anonymní typy třídy](../cpp/anonymous-class-types.md).  
  
 `base-list`  
 Tato třída volitelný seznam tříd nebo struktury odvodí její členy z. V tématu [základní třídy](../cpp/base-classes.md) Další informace. Každý název základní třídu nebo strukturu lze předcházet specifikátor přístupu ([veřejné](../cpp/public-cpp.md), [privátní](../cpp/private-cpp.md), [chráněné](../cpp/protected-cpp.md)) a [virtuální](../cpp/virtual-cpp.md) – klíčové slovo. Podívejte se na tabulku přístup ke členu v [řízení přístupu ke členům třídy](member-access-control-cpp.md) Další informace.  
  
 `member-list`  
 Seznam členy třídy. Odkazovat na [přehled členů třídy](../cpp/class-member-overview.md) Další informace.  
  
 `declarators`  
 Deklarátor seznam určující názvy jednu nebo více instancí typu třídy. Deklarátory můžou obsahovat inicializační seznamy, pokud jsou všechny datové členy třídy `public`. To je více běžné v struktury, jejíž členové data jsou `public` ve výchozím nastavení, než třídy. V tématu [přehled Deklarátory](../cpp/overview-of-declarators.md) Další informace.  
  
## <a name="remarks"></a>Poznámky  
 Další informace o třídy obecně platí, podívejte se na jeden z následujících témat:  
  
-   [Struktura](../cpp/struct-cpp.md)  
  
-   [sjednocení](../cpp/unions.md)  
  
-   [__multiple_inheritance](../cpp/inheritance-keywords.md)  
  
-   [__single_inheritance](../cpp/inheritance-keywords.md)  
  
-   [__virtual_inheritance](../cpp/inheritance-keywords.md)  
  
 Informace na spravované třídy a struktury najdete v tématu [třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md)  
  
## <a name="example"></a>Příklad  
  
```  
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
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [Třídy a struktury](../cpp/classes-and-structs-cpp.md)