---
title: abstraktní (C + +/ CLI a C + +/ CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- abstract
- abstract_cpp
helpviewer_keywords:
- abstract keyword [C++]
ms.assetid: cbae3408-0378-4ac8-b70d-c016b381a6d5
ms.openlocfilehash: d5060f1a0950b9b2ac2638b99ff157983944a3bb
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59031190"
---
# <a name="abstract--ccli-and-ccx"></a>abstraktní (C + +/ CLI a C + +/ CX)

**Abstraktní** deklaruje klíčové slovo:

- Typ může sloužit jako základní typ, ale samotný datový typ se nedá vytvořit instance.

- Členské funkce typu lze definovat pouze v odvozeném typu.

## <a name="all-platforms"></a>Všechny platformy

### <a name="syntax"></a>Syntaxe

*class-declaration* *class-identifier* **abstract {}**

**virtuální** *návratový typ* *identifikátor funkce členu* **abstraktní ();**

### <a name="remarks"></a>Poznámky

První příklad syntaxe deklaruje třídu jako abstraktní. *Deklarace třídy* komponenta může být buď nativní deklarace C++ (**třídy** nebo **struktura**), nebo deklaraci rozšíření jazyka C++ (**třídy ref class** nebo **ref struct**) Pokud `/ZW` nebo `/clr` je zadána možnost kompilátoru.

Druhý příklad syntaxe deklaruje virtuální členskou funkci být abstraktní. Deklarace funkce abstract je stejné jako deklarování čistě virtuální funkce. Deklarace abstraktu funkce člena zároveň způsobí, že nadřazené třídy, která má být deklarováno jako abstraktní.

**Abstraktní** – klíčové slovo je podporována v specifické pro platformu a nativního kódu; to znamená, ho můžete zkompilovat s nebo bez něj `/ZW` nebo `/clr` – možnost kompilátoru.

Pokud je abstraktní s typem, můžete zjistit v době kompilace `__is_abstract(type)` typovou vlastnost. Další informace najdete v tématu [podpora kompilátoru pro typové vlastnosti](compiler-support-for-type-traits-cpp-component-extensions.md).

**Abstraktní** – klíčové slovo je kontextové přepsání specifikátor. Další informace o kontextových klíčových slov najdete v tématu [Context-Sensitive Keywords](context-sensitive-keywords-cpp-component-extensions.md). Další informace o specifikátorech přepisu naleznete v tématu [jak: Deklarace specifikátorů Override v nativních kompilacích](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).

## <a name="windows-runtime"></a>prostředí Windows Runtime

Další informace najdete v tématu [referenční třídy a struktury](../cppcx/ref-classes-and-structs-c-cx.md).

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/clr`

### <a name="examples"></a>Příklady

Následující příklad vygeneruje chybu, protože třída `X` je označen **abstraktní**.

```cpp
// abstract_keyword.cpp
// compile with: /clr
ref class X abstract {
public:
   virtual void f() {}
};

int main() {
   X ^ MyX = gcnew X;   // C3622
}
```

Následující příklad kódu dojde k chybě, protože ho vytvoří instanci nativních tříd, který je označen **abstraktní**. K této chybě dojde, s nebo bez něj `/clr` – možnost kompilátoru.

```cpp
// abstract_keyword_2.cpp
class X abstract {
public:
   virtual void f() {}
};

int main() {
   X * MyX = new X; // C3622: 'X': a class declared as 'abstract'
                    // cannot be instantiated. See declaration of 'X'}
```

Následující příklad vygeneruje chybu, protože funkce `f` obsahuje definice, ale je označen **abstraktní**. Poslední příkaz v příkladu ukazuje, že deklarace abstraktní virtuální funkce je ekvivalentní k deklarování čistě virtuální funkce.

```cpp
// abstract_keyword_3.cpp
// compile with: /clr
ref class X {
public:
   virtual void f() abstract {}   // C3634
   virtual void g() = 0 {}   // C3634
};
```

## <a name="see-also"></a>Viz také:

[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)
