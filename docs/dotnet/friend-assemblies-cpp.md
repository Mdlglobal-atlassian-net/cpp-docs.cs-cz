---
title: Přátelská sestavení (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- friend assemblies, Visual C++
ms.assetid: 8d55fee0-b7c2-4fbe-a23b-dfe424dc71cd
ms.openlocfilehash: 05b9d8bcf5d7364e1dcd31940bc0db64a5e605f1
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447302"
---
# <a name="friend-assemblies-c"></a>Přátelská sestavení (C++)

Pro příslušné moduly runtime *přátelských sestavení* typy, které jsou v oboru názvů nebo globálního rozsahu v sestavení součásti, která je přístupná pro jeden nebo více sestavení klienta nebo modulů .NET díky funkci jazyka.

## <a name="all-runtimes"></a>Všechny moduly runtime

**Poznámky**

(Tato funkce jazyk nepodporuje všechny moduly runtime.)

## <a name="windows-runtime"></a>prostředí Windows Runtime

**Poznámky**

(Tato funkce jazyka není podporována v modulu Windows Runtime).

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: **/ZW**

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

**Poznámky**

#### <a name="to-make-types-at-namespace-scope-or-global-scope-in-an-assembly-component-accessible-to-a-client-assembly-or-netmodule"></a>Aby typy v oboru názvů nebo globálního rozsahu v jako součást sestavení k sestavení klienta nebo .netmodule

1. V komponentě, zadejte atribut sestavení <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>a předejte mu název klienta sestavení nebo modul .NET, který bude mít přístup k typy v oboru názvů nebo globálního rozsahu v komponentě.  Zadáním dalších atributů můžete zadat několik sestavení klienta nebo modulů .NET.

1. V sestavení klienta nebo .netmodule, při odkazování na sestavení součástí s použitím `#using`, předejte `as_friend` atribut.  Pokud zadáte `as_friend` atribut pro sestavení, které neurčuje `InternalsVisibleToAttribute`, výjimka za běhu bude vyvolána, pokud se pokusíte získat přístup k typu v oboru názvů nebo globálního rozsahu v komponentě.

Chyba sestavení dojde, pokud sestavení, která obsahuje <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut nemá silný název, ale sestavení klienta, který používá `as_friend` atribut provádí.

Přestože typy v oboru názvů a globální rozsah může být známé klienta sestavení nebo modul .NET, usnadnění přístupu člena je stále v platnosti.  Například nelze přistupovat k privátní člen.

Přístup pro všechny typy v sestavení je třeba udělit explicitně.  Například sestavení C nemá přístup pro všechny typy v sestavení A Pokud sestavení B odkazuje na sestavení C a sestavení B má přístup pro všechny typy v sestavení A.

Informace o tom, jak podepsat – to znamená, jak udělit silný název – sestavení, která je vytvořená pomocí Microsoft C++ kompilátoru, naleznete v tématu [sestavení se silným názvem (podepisování sestavení) (C++vyhodnocovací)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md).

Jako alternativu k použití funkce sestavení typu friend, můžete použít <xref:System.Security.Permissions.StrongNameIdentityPermission> k omezení přístupu k jednotlivých typů.

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru:   **/CLR**

### <a name="examples"></a>Příklady

Následující příklad kódu definuje komponenty, která určuje sestavení klienta, který má přístup k typům v komponentě.

```cpp
// friend_assemblies.cpp
// compile by using: /clr /LD
using namespace System::Runtime::CompilerServices;
using namespace System;
// an assembly attribute, not bound to a type
[assembly:InternalsVisibleTo("friend_assemblies_2")];

ref class Class1 {
public:
   void Test_Public() {
      Console::WriteLine("Class1::Test_Public");
   }
};
```

Následující příklad kódu získá přístup k privátním reprezentacím v komponentě.

```cpp
// friend_assemblies_2.cpp
// compile by using: /clr
#using "friend_assemblies.dll" as_friend

int main() {
   Class1 ^ a = gcnew Class1;
   a->Test_Public();
}
```

```Output
Class1::Test_Public
```

Následující příklad kódu definuje komponentu, ale neurčuje sestavení klienta, který bude mít přístup k typům v komponentě.

Všimněte si, že součást je propojený s použitím **/ opt: noref**. Tím se zajistí, že privátní typy jsou emitovány v metadatech součásti, které se nevyžaduje při `InternalsVisibleTo` je přítomen atribut. Další informace najdete v tématu [/OPT (optimalizace)](../build/reference/opt-optimizations.md).

```cpp
// friend_assemblies_3.cpp
// compile by using: /clr /LD /link /opt:noref
using namespace System;

ref class Class1 {
public:
   void Test_Public() {
      Console::WriteLine("Class1::Test_Public");
   }
};
```

Následující příklad kódu definuje klienta, který se pokusí o přístup k privátním reprezentacím v součásti, které neposkytují přístup k jeho privátní typy. Z důvodu chování modulu runtime Pokud chcete zachytit výjimku, musí pokusíte o přístup k privátním reprezentacím ve funkci pomocné rutiny.

```cpp
// friend_assemblies_4.cpp
// compile by using: /clr
#using "friend_assemblies_3.dll" as_friend
using namespace System;

void Test() {
   Class1 ^ a = gcnew Class1;
}

int main() {
   // to catch this kind of exception, use a helper function
   try {
      Test();
   }
   catch(MethodAccessException ^ e) {
      Console::WriteLine("caught an exception");
   }
}
```

```Output
caught an exception
```

Následující příklad kódu ukazuje, jak vytvořit komponenty se silným názvem, který určuje sestavení klienta, který bude mít přístup k typům v komponentě.

```cpp
// friend_assemblies_5.cpp
// compile by using: /clr /LD /link /keyfile:friend_assemblies.snk
using namespace System::Runtime::CompilerServices;
using namespace System;
// an assembly attribute, not bound to a type

[assembly:InternalsVisibleTo("friend_assemblies_6, PublicKey=00240000048000009400000006020000002400005253413100040000010001000bf45d77fd991f3bff0ef51af48a12d35699e04616f27ba561195a69ebd3449c345389dc9603d65be8cd1987bc7ea48bdda35ac7d57d3d82c666b7fc1a5b79836d139ef0ac8c4e715434211660f481612771a9f7059b9b742c3d8af00e01716ed4b872e6f1be0e94863eb5745224f0deaba5b137624d7049b6f2d87fba639fc5")];

private ref class Class1 {
public:
   void Test_Public() {
      Console::WriteLine("Class1::Test_Public");
   }
};
```

Všimněte si, že součást musíte zadat svůj veřejný klíč. My Navrhujeme, spusťte následující příkazy sekvenčně příkazového řádku k vytvoření páru klíčů a získat veřejný klíč:

**sn -d friend_assemblies.snk**

**sn -k friend_assemblies.snk**

**sn -i friend_assemblies.snk friend_assemblies.snk**

**sériové číslo -pc friend_assemblies.snk key.publickey**

**-tp key.publickey sériové číslo**

Následující příklad kódu získá přístup k privátním reprezentacím komponenty se silným názvem.

```cpp
// friend_assemblies_6.cpp
// compile by using: /clr /link /keyfile:friend_assemblies.snk
#using "friend_assemblies_5.dll" as_friend

int main() {
   Class1 ^ a = gcnew Class1;
   a->Test_Public();
}
```

```Output
Class1::Test_Public
```

## <a name="see-also"></a>Viz také:

[Přípony komponent pro platformy běhového prostředí](../extensions/component-extensions-for-runtime-platforms.md)
