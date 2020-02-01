---
title: literál (C++/CLI a C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- literal
- literal_cpp
helpviewer_keywords:
- literal keyword [C++]
ms.assetid: 6b1a1f36-2e1d-4a23-8eb6-172f4f3c477f
ms.openlocfilehash: d567f8270dcb8965ed2f882c9a0c005f295fc619
ms.sourcegitcommit: c4528a7424d35039454f17778baf1b5f98fbbee7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912830"
---
# <a name="literal-ccli-and-ccx"></a>literál (C++/CLI a C++/CX)

Proměnná (datový člen), která je označena jako **literál** v kompilaci **/CLR** , je nativní ekvivalent **statické proměnné const** .

## <a name="all-platforms"></a>Všechny platformy

### <a name="remarks"></a>Poznámky

(Žádné poznámky k této funkci jazyka se nevztahují na všechny moduly runtime.)

## <a name="windows-runtime"></a>prostředí Windows Runtime

### <a name="remarks"></a>Poznámky

(Pro tuto funkci jazyka neexistují žádné poznámky, které platí jenom pro prostředí Windows Runtime.)

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

## <a name="remarks"></a>Poznámky

Datový člen označený jako **literál** musí být inicializován při deklaraci a hodnota musí být konstantní celočíselný, Výčtový nebo řetězcový typ. Převod z typu inicializačního výrazu na typ statického datového členu const nesmí vyžadovat převod definovaný uživatelem.

Za běhu není přidělena žádná paměť pro pole literálu. Kompilátor vloží svou hodnotu do metadat pro třídu.

Proměnná označená jako **statická const** nebude v metadatech k ostatním kompilátorům k dispozici.

Další informace naleznete v tématu [static](../cpp/storage-classes-cpp.md) a [const](../cpp/const-cpp.md).

**literál** je kontextově závislé klíčové slovo. Další informace najdete v tématu [Kontextově závislá klíčová slova](context-sensitive-keywords-cpp-component-extensions.md) .

## <a name="example"></a>Příklad

Tento příklad ukazuje, že proměnná **literálu** implikuje **statickou**.

```cpp
// mcppv2_literal.cpp
// compile with: /clr
ref struct X {
   literal int i = 4;
};

int main() {
   int value = X::i;
}
```

## <a name="example"></a>Příklad

Následující příklad ukazuje vliv literálu v metadatech:

```cpp
// mcppv2_literal2.cpp
// compile with: /clr /LD
public ref struct A {
   literal int lit = 0;
   static const int sc = 1;
};
```

Všimněte si rozdílu v metadatech pro `sc` a `lit`: direktiva `modopt` se použije na `sc`, což znamená, že je může ignorovat jiné kompilátory.

```
.field public static int32 modopt([mscorlib]System.Runtime.CompilerServices.IsConst) sc = int32(0x0000000A)
```

```
.field public static literal int32 lit = int32(0x0000000A)
```

## <a name="example"></a>Příklad

Následující ukázka, která je vytvořena v C#, odkazuje na metadata vytvořená v předchozí ukázce a ukazuje vliv **literálových** a **statických proměnných const** :

```csharp
// mcppv2_literal3.cs
// compile with: /reference:mcppv2_literal2.dll
// A C# program
class B {
   public static void Main() {
      // OK
      System.Console.WriteLine(A.lit);
      System.Console.WriteLine(A.sc);

      // C# does not enforce C++ const
      A.sc = 9;
      System.Console.WriteLine(A.sc);

      // C# enforces const for a literal
      A.lit = 9;   // CS0131

      // you can assign a C++ literal variable to a C# const variable
      const int i = A.lit;
      System.Console.WriteLine(i);

      // but you cannot assign a C++ static const variable
      // to a C# const variable
      const int j = A.sc;   // CS0133
      System.Console.WriteLine(j);
   }
}
```

## <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/clr`

## <a name="see-also"></a>Viz také:

[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)