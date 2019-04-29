---
title: vlastnosti (C++vyhodnocovací a C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- property_cpp
- property
helpviewer_keywords:
- property keyword [C++]
ms.assetid: cc79d2b2-f013-4d81-8252-eece97a18704
ms.openlocfilehash: 8ec76db37cffb1b3d15447165300bedf1a8771c9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374201"
---
# <a name="property--ccli-and-ccx"></a>vlastnosti (C++vyhodnocovací a C++/CX)

Deklaruje *vlastnost*, což je členská funkce, který se chová a je přístupná jako datový člen nebo element pole.

## <a name="all-runtimes"></a>Všechny moduly runtime

Je možné deklarovat jedním z následujících typů vlastností.

*jednoduché vlastnosti*<br/>
Ve výchozím nastavení vytvoří *nastavení přístupového objektu* , který přiřazuje hodnotu vlastnosti *načtení přístupového objektu* , která načte hodnotu vlastnosti a vygenerovaný kompilátorem privátní datový člen, který obsahuje hodnotu vlastnosti.

*Vlastnost bloku*<br/>
Můžete tak vytvořit uživatelem definované get a/nebo přístupové objekty set. Vlastnost je čtení a zápisu, pokud mají oba get a přístupové objekty set jsou definované, pokud pouze přistupující objekt get je definována pouze pro čtení a jen pro zápis, pokud jen pro přistupující objekt set je definována.

Musíte explicitně deklarovat datový člen tak, aby obsahovala hodnotu vlastnosti.

*indexované vlastnosti*<br/>
Vlastnost blok, který můžete použít k získání a nastavení hodnoty vlastnosti, které je zadána jedna nebo více indexů.

Indexovaná vlastnost, která má buď můžete vytvořit uživatelem definované vlastnosti name nebo *výchozí* název vlastnosti. Název výchozí vlastnosti indexu je název třídy, ve kterém je definována vlastnost. Chcete-li deklarovat výchozí vlastnost, zadejte **výchozí** – klíčové slovo místo názvu vlastnosti.

Musíte explicitně deklarovat datový člen tak, aby obsahovala hodnotu vlastnosti. Datový člen indexovanou vlastnost, je obvykle pole nebo kolekce.

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
Datový typ hodnoty vlastnosti a proto samotné vlastnosti.

*property_name*<br/>
Název vlastnosti

*access-modifier*<br/>
Kvalifikátor k přístupu. Jsou platné kvalifikátory **statické** a **virtuální**.

Get nebo nemusí odsouhlasení přístupové objekty set **virtuální** kvalifikátor, ale musí shodnout na **statické** kvalifikátoru.

*inheritance-modifier*<br/>
Dědičnosti kvalifikátoru. Jsou platné kvalifikátory **abstraktní** a **zapečetěné**.

*index_list*<br/>
Čárkami oddělený seznam jednoho nebo více indexů. Každý index se skládá z typ indexu a volitelný identifikátor, který lze použít v těle metody vlastností.

*value*<br/>
Hodnota určená k přiřazení vlastnosti v operaci set nebo načíst v operaci get.

*property_body*<br/>
Tělo metody vlastností přistupujícího objektu set nebo get. *Property_body* můžete použít *index_list* pro přístup k základní datový člen vlastnost, nebo jako parametry v uživatelem definované zpracování.

## <a name="windows-runtime"></a>prostředí Windows Runtime

Další informace najdete v tématu [vlastnosti (C++/CX)](https://msdn.microsoft.com/library/windows/apps/hh755807.aspx).

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/ZW`

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

*modifier*<br/>
Modifikátor, který lze použít v deklaraci vlastnosti nebo metody přístupového objektu get/set. Možné hodnoty jsou **statické** a **virtuální**.

*type*<br/>
Typ hodnoty, která je reprezentována vlastnost.

*property_name*<br/>
Parametry pro metodu raise; signatura delegáta se musí shodovat.

*index_list*<br/>
Čárkami oddělený seznam jednoho nebo více indexů, zadaný v hranatých závorkách (operátor dolního indexu, ([])). Pro každý index zadejte typ a volitelně identifikátor, který lze použít v těle metody vlastností.

### <a name="remarks"></a>Poznámky

První příklad ukazuje syntaxi *jednoduchou vlastnost*, který implicitně deklaruje název i `set` a `get` metoda. Kompilátor automaticky vytvoří soukromé pole pro uložení hodnoty vlastnosti.

Druhý příklad ukazuje syntaxi *vlastnost bloku*, které obě explicitně deklaruje `set` a `get` – metoda.

Třetí příklad syntaxe ukazuje definované zákazníkem *index – vlastnost*. Nepřetíží indexovanou vlastnost přijímá parametry než hodnota nastavit nebo načíst. Je nutné zadat název vlastnosti. Na rozdíl od jednoduché vlastnosti `set` a/nebo `get` metody nepřetíží indexovanou vlastnost musí být explicitně definovány a je nutné zadat název vlastnosti.

Čtvrtý ukazuje příklad syntaxe *výchozí* vlastnost, která poskytuje přístup jako pole instance typu. Klíčové slovo **výchozí**, slouží pouze k určení výchozí vlastnost. Název výchozí vlastnosti je název typu, ve kterém je definována vlastnost.

**Vlastnost** – klíčové slovo se může zobrazit ve třídě, rozhraní nebo hodnotového typu. Vlastnost může mít funkci get (jen pro čtení), funkce set (jen pro zápis) nebo obě (čtení a zápis).

Název vlastnosti nesmí shodovat s názvem spravované třídy, která ji obsahuje. Návratový typ metody getter funkce musí odpovídat typ posledního parametru odpovídající funkce setter.

Pro klientský kód vlastnost vzhledem běžný datový člen a může být zapsána do nebo číst z pomocí stejné syntaxe jako datový člen.

Get a set metod nemusí shodnout na **virtuální** modifikátor.

Usnadnění přístupu get a set – metoda se může lišit.

Definice metody vlastnost může být použito mimo tělo třídy, stejně jako běžné metody.

Get a metodu set pro vlastnost dohodnou **statické** modifikátor.

Je skalární vlastnost pokud jeho get a set metod podle následujícího popisu:

- Metoda get nemá žádné parametry a má návratový typ `T`.

- Set – metoda má parametr typu `T`a návratový typ **void**.

Musí existovat pouze jeden skalární vlastnost deklarovaná v oboru se stejným identifikátorem. Skalární vlastnosti nemohou být přetíženy.

Při deklaraci datový člen vlastnost, kompilátor vkládá datový člen – někdy označovány jako "úložiště zálohování" – ve třídě. Název datového člena, je však formuláře tak, že nemůže odkazovat člena ve zdroji, jako by šlo skutečný datový člen obsahující třídy. Použijte ildasm.exe zobrazení metadat pro váš typ a zobrazí název generovaného kompilátorem pro vlastnosti záložního úložiště.

Pro přístupové metody v bloku vlastnost je povolen různou přístupností.  To znamená set – metoda může být veřejný a Metoda get může být privátní.  Nicméně jedná se o chybu pro přístupové metody pro mít méně omezující přístupnost než u deklarace samotná hodnota vlastnosti.

**Vlastnost** je kontextové klíčové slovo.  Další informace najdete v tématu [Context-Sensitive Keywords](context-sensitive-keywords-cpp-component-extensions.md).

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/clr`

### <a name="examples"></a>Příklady

Následující příklad ukazuje deklaraci a použití vlastností datový člen a zároveň se zablokují vlastnost.  Také ukazuje, že přístupový objekt vlastnosti je možné definovat mimo třídu.

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