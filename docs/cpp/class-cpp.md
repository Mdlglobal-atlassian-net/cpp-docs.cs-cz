---
title: třída (C++)
ms.date: 11/04/2016
f1_keywords:
- class_cpp
helpviewer_keywords:
- class types [C++], class statements
- class keyword [C++]
ms.assetid: dd23c09f-6598-4069-8bff-69c7f2518b9f
ms.openlocfilehash: 5abd2ef73ff8af9ebc2f1827cb5403025d5383ee
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51330993"
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

*specifikace šablony*<br/>
Volitelné specifikace šablony. Další informace najdete v [šablony](templates-cpp.md).

*class*<br/>
**Třídy** – klíčové slovo.

*MS-decl-spec*<br/>
Volitelná specifikace paměťové třídy. Další informace najdete [__declspec](../cpp/declspec.md) – klíčové slovo.

*Značka*<br/>
Název typu daný pro třídu. Značka se změní vyhrazené slovo v rámci oboru třídy. Značka je volitelná. Pokud tento parametr vynechán, je definována anonymní třídy. Další informace najdete v tématu [anonymní typy třídy](../cpp/anonymous-class-types.md).

*Base-list*<br/>
Volitelný seznam tříd nebo struktur, které tato třída odvodí svoje členy z. Zobrazit [základní třídy](../cpp/base-classes.md) Další informace. Každý název základní třídy nebo struktury může být uvozen specifikátorem přístupu ([veřejné](../cpp/public-cpp.md), [privátní](../cpp/private-cpp.md), [chráněné](../cpp/protected-cpp.md)) a [virtuální](../cpp/virtual-cpp.md) klíčové slovo. Viz tabulka pro přístup ke členu [řízení přístupu ke členům třídy](member-access-control-cpp.md) Další informace.

*seznam členů*<br/>
Seznam členů třídy. Odkazovat na [přehled členů třídy](../cpp/class-member-overview.md) Další informace.

*deklarátory*<br/>
Seznam deklarátoru určující názvy jednu nebo více instancí typu třídy. Deklarátory mohou obsahovat inicializační seznamy, pokud jsou všechny datové členy třídy **veřejné**. To je běžné ve strukturách, jehož datové členy **veřejné** ve výchozím nastavení, než v třídách. Zobrazit [přehled Deklarátorů](../cpp/overview-of-declarators.md) Další informace.

## <a name="remarks"></a>Poznámky

Další informace o třídách obecně odkazovat na jeden z následujících témat:

- [struct](../cpp/struct-cpp.md)

- [sjednocení](../cpp/unions.md)

- [__multiple_inheritance](../cpp/inheritance-keywords.md)

- [__single_inheritance](../cpp/inheritance-keywords.md)

- [__virtual_inheritance](../cpp/inheritance-keywords.md)

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

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Třídy a struktury](../cpp/classes-and-structs-cpp.md)