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
ms.openlocfilehash: c5ee72e557c62e3db2eeb5dac4811133719183f6
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57746303"
---
# <a name="for-each-in"></a>for each, in

Prochází skrze pole nebo kolekci. Toto nestandardní klíčové slovo je k dispozici v projektech v jazyce C++/CLI a v nativním jazyce C++. Jeho použití se však nedoporučuje. Zvažte použití standardního [Range-based for Statement (C++)](../cpp/range-based-for-statement-cpp.md) místo.

## <a name="all-runtimes"></a>Všechny moduly runtime

### <a name="syntax"></a>Syntaxe

> **pro každou (** *typ* *identifikátor* **v** *výraz* **) {}**<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;*Příkazy*<br/>
> **}**

### <a name="parameters"></a>Parametry

*type*<br/>
Typ `identifier`.

*identifier*<br/>
Iterační proměnná, která představuje prvek kolekce.  Když `identifier` je [Tracking Reference Operator](../windows/tracking-reference-operator-cpp-component-extensions.md), lze tento prvek upravit.

*Výraz*<br/>
Výraz pole nebo kolekce. Prvek kolekce musí být tak, aby kompilátor mohl převést tak, `identifier` typu.

*Příkazy*<br/>
Jeden nebo více příkazů ke spuštění.

### <a name="remarks"></a>Poznámky

`for each` Prohlášení se používá k iteraci v kolekci. Prvky v kolekci je možné měnit, ale nelze je přidávat ani odstraňovat.

*Příkazy* jsou spouštěny pro každý prvek v poli nebo kolekci. Po dokončení iterace u všech prvků v kolekci je kontrola předána příkazu následujícímu `for each` bloku.

`for each` a `in` jsou [kontextově závislá klíčová slova](../windows/context-sensitive-keywords-cpp-component-extensions.md).

Další informace:

- [Iterace nad kolekcí STL C++ s použitím výrazu for each](../dotnet/iterating-over-stl-collection-by-using-for-each.md)

- [Postupy: Iterace v polích s výrazem for each](../dotnet/how-to-iterate-over-arrays-with-for-each.md)

- [Postupy: Iterace v obecné kolekci s výrazem for each](../dotnet/how-to-iterate-over-a-generic-collection-with-for-each.md)

- [Postupy: Iterace v uživatelem definované kolekci s výrazem for each](../dotnet/how-to-iterate-over-a-user-defined-collection-with-for-each.md)

## <a name="windows-runtime"></a>prostředí Windows Runtime

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: **/ZW**

### <a name="example"></a>Příklad

Tento příklad ukazuje způsob použití `for each` k iteraci v rámci řetězce.

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

**Output**

```Output
abcd

Testing
```

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

**Poznámky**

Syntaxe CLR je stejná jako **všechny moduly runtime** syntaxe, s výjimkou následujícího.

*Výraz*<br/>
Výraz spravovaného pole nebo kolekce. Prvek kolekce musí být tak, aby kompilátor mohl převést z <xref:System.Object> k *identifikátor* typu.

*výraz* vyhodnocen jako typ, který implementuje <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, nebo typ, který definuje `GetEnumerator` metody, aby buď vrátil typ, který implementuje <xref:System.Collections.IEnumerator> nebo deklaruje všechny metody, které jsou definovány v `IEnumerator`.

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru:   **/CLR**

### <a name="example"></a>Příklad

Tento příklad ukazuje způsob použití `for each` k iteraci v rámci řetězce.

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

**Output**

```Output
abcd

Testing
```

## <a name="see-also"></a>Viz také:

[Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)
