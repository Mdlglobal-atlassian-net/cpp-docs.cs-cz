---
title: třída (C++)
ms.date: 11/04/2016
f1_keywords:
- class_cpp
helpviewer_keywords:
- class types [C++], class statements
- class keyword [C++]
ms.assetid: dd23c09f-6598-4069-8bff-69c7f2518b9f
ms.openlocfilehash: c1b9d8f6510dfe15644f0e47cad7e0aecbac36c9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180973"
---
# <a name="class-c"></a>třída (C++)

Klíčové slovo **Class** deklaruje typ třídy nebo definuje objekt typu třídy.

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

*Šablona – specifikace*<br/>
Volitelné specifikace šablony. Další informace najdete v tématu [šablony](templates-cpp.md).

*class*<br/>
Klíčové slovo **Class**

*MS-příspecifikaci – specifikace*<br/>
Volitelná specifikace paměťové třídy. Další informace najdete v klíčovém slově [__declspec](../cpp/declspec.md) .

*Inteligentní*<br/>
Název typu předaný třídě. Značka se stal rezervovaným slovem v oboru třídy. Značka je volitelná. Je-li tento parametr vynechán, je definována anonymní třída. Další informace naleznete v tématu [anonymní typy tříd](../cpp/anonymous-class-types.md).

*seznam Base-list*<br/>
Volitelný seznam tříd nebo struktur, ze kterých tato třída bude odvodit členy. Další informace najdete v tématu [základní třídy](../cpp/base-classes.md) . Každý název základní třídy nebo struktury může předcházet specifikátorem přístupu ([Public](../cpp/public-cpp.md), [Private](../cpp/private-cpp.md), [Protected](../cpp/protected-cpp.md)) a klíčovým slovem [Virtual](../cpp/virtual-cpp.md) . Další informace naleznete v tabulce pro přístup členů v tématu [řízení přístupu ke členům třídy](member-access-control-cpp.md) .

*seznam členů*<br/>
Seznam členů třídy. Další informace najdete v tématu [Přehled členů třídy](../cpp/class-member-overview.md) .

*deklarátory*<br/>
Seznam deklarátor určující názvy jedné nebo více instancí typu třídy. Deklarátory mohou obsahovat inicializační seznamy, pokud jsou všechny datové členy třídy **veřejné**. To je běžnější ve strukturách, jejichž datové členy jsou ve výchozím nastavení **veřejné** , než v třídách. Další informace najdete v tématu [Přehled deklarátory](../cpp/overview-of-declarators.md) .

## <a name="remarks"></a>Poznámky

Další informace o třídách obecně naleznete v jednom z následujících témat:

- [struct](../cpp/struct-cpp.md)

- [sjednocovací](../cpp/unions.md)

- [__multiple_inheritance](../cpp/inheritance-keywords.md)

- [__single_inheritance](../cpp/inheritance-keywords.md)

- [__virtual_inheritance](../cpp/inheritance-keywords.md)

Informace o spravovaných třídách a strukturách C++v/CLI C++a/CX naleznete v tématu [třídy a struktury](../extensions/classes-and-structs-cpp-component-extensions.md) .

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

## <a name="see-also"></a>Viz také

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Třídy a struktury](../cpp/classes-and-structs-cpp.md)
