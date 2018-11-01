---
title: literál (C + +/ CLI a C + +/ CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- literal
- literal_cpp
helpviewer_keywords:
- literal keyword [C++]
ms.assetid: 6b1a1f36-2e1d-4a23-8eb6-172f4f3c477f
ms.openlocfilehash: d58df1bb6a6ec1e53ee434cf60a8caf3d557eeb2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50521028"
---
# <a name="literal-ccli-and-ccx"></a>literál (C + +/ CLI a C + +/ CX)

Proměnné (datový člen) označené jako **literálu** v **/CLR** je ekvivalentem nativní kompilace **konstrukce static const** proměnné.

## <a name="all-platforms"></a>Všechny platformy

### <a name="remarks"></a>Poznámky

(Neexistují žádné poznámky o této funkci jazyka, které platí pro všechny moduly runtime.)

## <a name="windows-runtime"></a>prostředí Windows Runtime

### <a name="remarks"></a>Poznámky

(Neexistují žádné poznámky o této funkci jazyka, které se vztahují jenom Windows Runtime.)

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

## <a name="remarks"></a>Poznámky

Datový člen označen jako **literálu** musí být při deklaraci inicializovány a hodnota musí být konstantní integrál, výčet nebo typ řetězce. Převod z typu výrazu inicializace typ const statických dat – člen nesmí vyžadovat uživatelsky definovaný převod.

Žádná paměť je přidělena pro pole literálu za běhu; kompilátor vloží jenom její hodnotu v metadatech pro třídu.

Proměnné označené **konstrukce static const** nebude k dispozici v metadatech na jiné kompilátory.

Další informace najdete v tématu [statické](../cpp/storage-classes-cpp.md) a [const](../cpp/const-cpp.md).

**literál** je kontextové klíčové slovo. Zobrazit [Context-Sensitive Keywords](../windows/context-sensitive-keywords-cpp-component-extensions.md) Další informace.

## <a name="example"></a>Příklad

Tento příklad ukazuje, že **literálu** proměnné znamená **statické**.

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

Všimněte si rozdílu v metadatech pro `sc` a `lit`: `modopt` – direktiva se použije pro `sc`, což znamená, ho můžete ignorovat jinými kompilátory.

```
.field public static int32 modopt([mscorlib]System.Runtime.CompilerServices.IsConst) sc = int32(0x0000000A)
```

```
.field public static literal int32 lit = int32(0x0000000A)
```

## <a name="example"></a>Příklad

Následující příklad a vytvořené v jazyce C#, odkazuje na metadata vytvořili v předchozí ukázce a ukazuje vliv **literálu** a **konstrukce static const** proměnné:

```cs
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

– Možnost kompilátoru: `/clr`

## <a name="see-also"></a>Viz také

[Přípony komponent pro .NET a UPW](../windows/component-extensions-for-runtime-platforms.md)