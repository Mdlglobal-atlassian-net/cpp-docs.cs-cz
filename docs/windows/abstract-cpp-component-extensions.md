---
title: abstract (rozšíření komponent C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- abstract
- abstract_cpp
dev_langs:
- C++
helpviewer_keywords:
- abstract keyword [C++]
ms.assetid: cbae3408-0378-4ac8-b70d-c016b381a6d5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 463848ea5f01bf232850d548c9f4255c07409254
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42610996"
---
# <a name="abstract--c-component-extensions"></a>abstract (rozšíření komponent C++)

**Abstraktní** deklaruje klíčové slovo:

- Typ může sloužit jako základní typ, ale samotný datový typ se nedá vytvořit instance.

- Členské funkce typu lze definovat pouze v odvozeném typu.

## <a name="all-platforms"></a>Všechny platformy

### <a name="syntax"></a>Syntaxe

```cpp
      class-declaration
      class-identifier
      abstract {}
virtualreturn-typemember-function-identifier() abstract ;
```

### <a name="remarks"></a>Poznámky

První příklad syntaxe deklaruje třídu jako abstraktní. *Deklarace třídy* komponenta může být buď nativní deklarace C++ (**třídy** nebo **struktura**), nebo deklaraci rozšíření jazyka C++ (**třídy ref class** nebo **ref struct**) Pokud `/ZW` nebo `/clr` je zadána možnost kompilátoru.

Druhý příklad syntaxe deklaruje virtuální členskou funkci být abstraktní. Deklarace funkce abstract je stejné jako deklarování čistě virtuální funkce. Deklarace abstraktu funkce člena zároveň způsobí, že nadřazené třídy, která má být deklarováno jako abstraktní.

**Abstraktní** – klíčové slovo je podporována v specifické pro platformu a nativního kódu; to znamená, ho můžete zkompilovat s nebo bez něj `/ZW` nebo `/clr` – možnost kompilátoru.

Pokud je abstraktní s typem, můžete zjistit v době kompilace `__is_abstract(type)` typovou vlastnost. Další informace najdete v tématu [podpora kompilátoru pro typové vlastnosti](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).

**Abstraktní** – klíčové slovo je kontextové přepsání specifikátor. Další informace o kontextových klíčových slov najdete v tématu [Context-Sensitive Keywords](../windows/context-sensitive-keywords-cpp-component-extensions.md). Další informace o specifikátorech přepisu naleznete v tématu [jak: deklarovat specifikátorů Override v nativní kompilaci](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).

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

## <a name="see-also"></a>Viz také

[Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)