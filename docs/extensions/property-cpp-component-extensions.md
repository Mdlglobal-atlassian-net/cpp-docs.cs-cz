---
title: vlastnost (C++/CLI a C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- property_cpp
- property
helpviewer_keywords:
- property keyword [C++]
ms.assetid: cc79d2b2-f013-4d81-8252-eece97a18704
ms.openlocfilehash: 4a05f9cf8cbec9644254d14873a3259f12b33aed
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509713"
---
# <a name="property--ccli-and-ccx"></a>vlastnost (C++/CLI a C++/CX)

Deklaruje *vlastnost*, která je členská funkce, která se chová a je k dispozici jako datový člen nebo prvek pole.

## <a name="all-runtimes"></a>Všechny moduly runtime

Můžete deklarovat jeden z následujících typů vlastností.

*Jednoduchá vlastnost*<br/>
Ve výchozím nastavení vytvoří *přistupující objekt set* , který přiřadí hodnotu vlastnosti, *přístupový objekt get* , který načte hodnotu vlastnosti, a soukromý datový člen generovaný kompilátorem, který obsahuje hodnotu vlastnosti.

*blok vlastnosti*<br/>
Toto použijte k vytvoření uživatelem definovaných přístupových objektů Get nebo set. Vlastnost je určena pro čtení a zápis, jsou-li přístupové objekty get a set definovány, jen pro čtení, pokud je definován pouze přistupující objekt get, a pouze pro zápis, pokud je definován pouze přístupový objekt set.

Datový člen musíte explicitně deklarovat tak, aby obsahoval hodnotu vlastnosti.

*indexovaná vlastnost*<br/>
Blok vlastnosti, který lze použít k získání a nastavení hodnoty vlastnosti, která je určena jedním nebo více indexy.

Můžete vytvořit indexovanou vlastnost, která má buď uživatelsky definovaný název vlastnosti, nebo název *výchozí* vlastnosti. Název výchozí vlastnosti index je název třídy, ve které je vlastnost definovaná. Chcete-li deklarovat výchozí vlastnost, zadejte **výchozí** klíčové slovo místo názvu vlastnosti.

Datový člen musíte explicitně deklarovat tak, aby obsahoval hodnotu vlastnosti. U indexované vlastnosti je datový člen obvykle pole nebo kolekce.

### <a name="syntax"></a>Syntaxe

```cpp
property type property_name;

property type property_name {
   access-modifier type get() inheritance-modifier {property_body};
   access-modifier void set(type value) inheritance-modifier {property_body};
}

property type property_name[index_list] {
   access-modifier type get(index_list) inheritance-modifier {property_body};
   access-modifier void set(index_list, value) inheritance-modifier {property_body};
}

property type default[index_list] {
   access-modifier type get(index_list) inheritance-modifier {property_body};
   access-modifier void set(index_list, value) inheritance-modifier {property_body};
}
```

### <a name="parameters"></a>Parametry

*type*<br/>
Datový typ hodnoty vlastnosti, a následně samotnou vlastnost.

*property_name*<br/>
Název vlastnosti

*access-modifier*<br/>
Kvalifikátor přístupu. Platné kvalifikátory jsou **statické** a **virtuální**.

Přistupující objekty get nebo set nesouhlasí s virtuálním kvalifikátorem, ale musí souhlasit s jeho statickým kvalifikátorem.

*inheritance-modifier*<br/>
Kvalifikátor dědičnosti. Platné kvalifikátory jsou **abstraktní** a **zapečetěné**.

*index_list*<br/>
Seznam jednoho nebo více indexů oddělených čárkami. Každý index se skládá z typu indexu a volitelného identifikátoru, který lze použít v těle metody vlastnosti.

*value*<br/>
Hodnota, která má být přiřazena vlastnosti v operaci set nebo načtena v operaci get.

*property_body*<br/>
Tělo metody vlastnosti objektu set nebo Get. *Property_body* může použít *index_list* pro přístup k základnímu datovému členu vlastnosti nebo jako parametry v uživatelsky definovaném zpracování.

## <a name="windows-runtime"></a>prostředí Windows Runtime

Další informace najdete v tématu [vlastnosti (C++/CX)](../cppcx/properties-c-cx.md).

### <a name="requirements"></a>Požadavky

Možnost kompilátoru:`/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

### <a name="syntax"></a>Syntaxe

```cpp
modifier property type property_name;

modifier property type property_name {
   modifier void set(type);
   modifier type get();
}
modifier property type property_name[index-list, value] {
   modifier void set(index-list, value);
   modifier type get(index-list);

modifier property type default[index];
}
```

### <a name="parameters"></a>Parametry

*upravující*<br/>
Modifikátor, který lze použít buď pro deklaraci vlastnosti, nebo pro metodu get/set přístupového objektu. Možné hodnoty jsou **statické** a **virtuální**.

*type*<br/>
Typ hodnoty, která je reprezentována vlastností.

*property_name*<br/>
Parametr (y) pro metodu vyvolání; musí odpovídat signatuře delegáta.

*index_list*<br/>
Seznam jednoho nebo více indexů oddělených čárkami, který je určený v hranatých závorkách (operátor dolního indexu, ([])). Pro každý index zadejte typ a volitelně identifikátor, který lze použít v těle metody vlastnosti.

### <a name="remarks"></a>Poznámky

První příklad syntaxe ukazuje *jednoduchou vlastnost*, která implicitně deklaruje `set` metodu a. `get` Kompilátor automaticky vytvoří soukromé pole pro uložení hodnoty vlastnosti.

Druhý příklad syntaxe ukazuje *blok vlastnosti*, který explicitně deklaruje `set` metodu a. `get`

Třetí příklad syntaxe znázorňuje uživatelsky definovanou *vlastnost indexu*. Vlastnost index má kromě hodnoty, která má být nastavena nebo načtena, i parametry. Je nutné zadat název vlastnosti. Na `set` rozdíl od jednoduchých vlastností musí být metody a/ `get` nebo vlastnosti index explicitně definovány a musíte zadat název vlastnosti.

Čtvrtý příklad syntaxe ukazuje *výchozí* vlastnost, která poskytuje přístup jako typ pole k instanci typu. Klíčové slovo **Default**, slouží pouze k určení výchozí vlastnosti. Název výchozí vlastnosti je název typu, ve kterém je vlastnost definována.

Klíčové slovo **Property** se může objevit v typu třída, rozhraní nebo hodnoty. Vlastnost může mít funkci get (jen pro čtení), funkci set (pouze pro zápis) nebo obojí (pro čtení i zápis).

Název vlastnosti se nemůže shodovat s názvem spravované třídy, která ho obsahuje. Návratový typ funkce getter se musí shodovat s typem posledního parametru odpovídající funkce setter.

Pro klientský kód má vlastnost vzhled běžného datového členu a lze jej zapsat nebo číst pomocí stejné syntaxe jako datový člen.

Metody Get a set nemusí souhlasit s modifikátorem **Virtual** .

Přístupnost metody Get a set se může lišit.

Definice metody vlastnosti se může objevit mimo tělo třídy, stejně jako běžnou metodou.

Metoda get a set pro vlastnost musí souhlasit s modifikátorem **static** .

Vlastnost je skalární, pokud metody Get a set vyhovují následujícímu popisu:

- Metoda get nemá žádné parametry a má návratový typ `T`.

- Metoda set má parametr typu `T`a návratový typ **void**.

V oboru se stejným identifikátorem musí být deklarována pouze jedna skalární vlastnost. Skalární vlastnosti nelze přečítat.

Když je deklarován datový člen vlastnosti, kompilátor vloží datový člen (někdy označovaný jako "záložní úložiště") ve třídě. Název datového členu je však formulář, například, který nelze odkázat na člena ve zdroji, jako by šlo o skutečného datového člena obsahujícího třídu. Použijte Ildasm. exe k zobrazení metadat pro váš typ a podívejte se na název generovaný kompilátorem pro záložní úložiště vlastností.

Pro přístupové metody v bloku vlastností je povoleno jiné usnadnění.  To znamená, že metoda Set může být veřejná a metoda get může být soukromá.  Jedná se však o chybu, pokud metoda přístupového objektu má méně omezující přístupnost, než je v deklaraci samotné vlastnosti.

**vlastnost** je kontextově závislé klíčové slovo.  Další informace najdete v tématu [Kontextově závislá klíčová slova](context-sensitive-keywords-cpp-component-extensions.md).

### <a name="requirements"></a>Požadavky

Možnost kompilátoru:`/clr`

### <a name="examples"></a>Příklady

Následující příklad ukazuje deklaraci a použití datového člena vlastnosti a bloku vlastnosti.  Také ukazuje, že přistupující objekt vlastnosti lze definovat mimo třídu.

```cpp
// mcppv2_property.cpp
// compile with: /clr
using namespace System;
public ref class C {
   int MyInt;
public:

   // property data member
   property String ^ Simple_Property;

   // property block
   property int Property_Block {

      int get();

      void set(int value) {
         MyInt = value;
      }
   }
};

int C::Property_Block::get() {
   return MyInt;
}

int main() {
   C ^ MyC = gcnew C();
   MyC->Simple_Property = "test";
   Console::WriteLine(MyC->Simple_Property);

   MyC->Property_Block = 21;
   Console::WriteLine(MyC->Property_Block);
}
```

```Output
test

21
```

## <a name="see-also"></a>Viz také:

[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)