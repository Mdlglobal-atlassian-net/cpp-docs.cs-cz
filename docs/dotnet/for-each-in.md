---
title: for each, in
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::foreach
- for
- each
- in
helpviewer_keywords:
- for each keyword [C++]
ms.assetid: 0c3a364b-2747-43f3-bb8d-b7d3b7023f79
ms.openlocfilehash: f1f5523eb22bd8a839da9b3f73dd6c3718b4fd63
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825787"
---
# <a name="for-each-in"></a>for each, in

Prochází skrze pole nebo kolekci. Toto nestandardní klíčové slovo je k dispozici v projektech v jazyce C++/CLI a v nativním jazyce C++. Jeho použití se však nedoporučuje. Zvažte možnost použít místo toho standardní [příkaz pro použití rozsahů (C++)](../cpp/range-based-for-statement-cpp.md) .

## <a name="all-runtimes"></a>Všechny moduly runtime

### <a name="syntax"></a>Syntaxe

> **for each (** *type* *identifikátor* **typu ve** *výrazu* **) {**\
> &nbsp;&nbsp;&nbsp;&nbsp;*učiněn*\
> **}**

### <a name="parameters"></a>Parametry

*textový*<br/>
Typ `identifier`.

*RID*<br/>
Iterační proměnná, která představuje prvek kolekce.  Je `identifier` -li [Operátor sledovacího odkazu](../extensions/tracking-reference-operator-cpp-component-extensions.md), lze prvek upravit.

*vyjádření*<br/>
Výraz pole nebo kolekce. Prvek kolekce musí být takový, aby jej kompilátor mohl převést na `identifier` typ.

*učiněn*<br/>
Jeden nebo více příkazů ke spuštění.

### <a name="remarks"></a>Poznámky

`for each` Příkaz se používá k iteraci v kolekci. Prvky v kolekci je možné měnit, ale nelze je přidávat ani odstraňovat.

*Příkazy* jsou spouštěny pro každý prvek v poli nebo kolekci. Po dokončení iterace pro všechny prvky v kolekci se ovládací prvek přenese do příkazu, který následuje po `for each` bloku.

`for each`a `in` jsou [Kontextově závislá klíčová slova](../extensions/context-sensitive-keywords-cpp-component-extensions.md).

Další informace najdete tady:

- [Iterace nad kolekcí STL C++ s použitím výrazu for each](../dotnet/iterating-over-stl-collection-by-using-for-each.md)

- [Postupy: Iterace v polích s použitím výrazu for each](../dotnet/how-to-iterate-over-arrays-with-for-each.md)

- [Postupy: Iterace v obecné kolekci s výrazem for each](../dotnet/how-to-iterate-over-a-generic-collection-with-for-each.md)

- [Postupy: Iterace v uživatelem definované kolekci s výrazem for each](../dotnet/how-to-iterate-over-a-user-defined-collection-with-for-each.md)

## <a name="windows-runtime"></a>prostředí Windows Runtime

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: **/ZW**

### <a name="example"></a>Příklad

Tento příklad ukazuje, jak použít `for each` k iterování řetězce.

```cpp
// for_each_string1.cpp
// compile with: /ZW
#include <stdio.h>
using namespace Platform;

ref struct MyClass {
   property String^ MyStringProperty;
};

int main() {
   String^ MyString = ref new String("abcd");

   for each ( char c in MyString )
      wprintf("%c", c);

   wprintf("/n");

   MyClass^ x = ref new MyClass();
   x->MyStringProperty = "Testing";

   for each( char c in x->MyStringProperty )
      wprintf("%c", c);
}
```

**Výstup**

```Output
abcd

Testing
```

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

**Poznámky**

Syntaxe CLR je stejná jako syntaxe **všechny moduly runtime** , s výjimkou následujících.

*vyjádření*<br/>
Výraz spravovaného pole nebo kolekce. Prvek kolekce musí být takový, aby jej kompilátor mohl převést z <xref:System.Object> na typ *identifikátoru* .

*výraz* je vyhodnocen jako typ, který <xref:System.Collections.IEnumerable>implementuje <xref:System.Collections.Generic.IEnumerable%601>, nebo typ, který definuje `GetEnumerator` metodu, která buď vrátí typ, který implementuje <xref:System.Collections.IEnumerator> nebo deklaruje všechny metody, které jsou definovány v. `IEnumerator`

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: **/CLR**

### <a name="example"></a>Příklad

Tento příklad ukazuje, jak použít `for each` k iterování řetězce.

```cpp
// for_each_string2.cpp
// compile with: /clr
using namespace System;

ref struct MyClass {
   property String ^ MyStringProperty;
};

int main() {
   String ^ MyString = gcnew String("abcd");

   for each ( Char c in MyString )
      Console::Write(c);

   Console::WriteLine();

   MyClass ^ x = gcnew MyClass();
   x->MyStringProperty = "Testing";

   for each( Char c in x->MyStringProperty )
      Console::Write(c);
}
```

**Výstup**

```Output
abcd

Testing
```

## <a name="see-also"></a>Viz také

[Přípony komponent pro platformy běhového prostředí](../extensions/component-extensions-for-runtime-platforms.md)
