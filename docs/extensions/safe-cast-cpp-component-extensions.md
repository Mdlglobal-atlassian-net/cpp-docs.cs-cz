---
title: safe_cast (C + +/ CLI a C + +/ CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- safe_cast
- safe_cast_cpp
- stdcli::language::safe_cast
helpviewer_keywords:
- safe_cast keyword [C++]
ms.assetid: 4fa688bf-a8ec-49bc-a4c5-f48134efa4f7
ms.openlocfilehash: 199fda710a077998c6b10f101f6ebc15573e675e
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038878"
---
# <a name="safecast-ccli-and-ccx"></a>safe_cast (C + +/ CLI a C + +/ CX)

**Safe_cast** časový limit operace vrátí zadaný výraz jako zadaný typ, v případě úspěchu; jinak vyvolá výjimku `InvalidCastException`.

## <a name="all-runtimes"></a>Všechny moduly runtime

(Neexistují žádné poznámky o této funkci jazyka, které platí pro všechny moduly runtime.)

### <a name="syntax"></a>Syntaxe

```cpp
[default]:: safe_cast< type-id >( expression )
```

## <a name="windows-runtime"></a>prostředí Windows Runtime

**safe_cast** vám umožní změnit typ zadaného výrazu. V situacích, kdy plně očekáváte proměnná nebo parametr být převoditelná na určitý typ, můžete použít **safe_cast** bez **bloku try-catch** bloku k detekci programové chyby během vývoje. Další informace najdete v tématu [přetypování (C + +/ CX)](https://msdn.microsoft.com/library/windows/apps/hh755802.aspx).

### <a name="syntax"></a>Syntaxe

```cpp
[default]:: safe_cast< type-id >( expression )
```

### <a name="parameters"></a>Parametry

*id typu*<br/>
Typ, který chcete převést *výraz* k. Popisovač pro odkaz nebo typ hodnoty, typ hodnoty nebo odkaz sledování na typ odkazu nebo hodnoty.

*výraz*<br/>
Výraz, který se vyhodnotí jako popisovač pro odkaz nebo typ hodnoty, typ hodnoty nebo odkaz sledování na typ odkazu nebo hodnoty.

### <a name="remarks"></a>Poznámky

**safe_cast** vyvolá `InvalidCastException` Pokud nelze převést *výraz* na typ určený *id typu*. K zachycení `InvalidCastException`, zadejte [/EH (Model zpracování výjimek)](../build/reference/eh-exception-handling-model.md) – možnost kompilátoru a použití **bloku try/catch** příkazu.

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/ZW`

### <a name="examples"></a>Příklady

Následující příklad kódu ukazuje, jak používat **safe_cast** s modulem Windows Runtime.

```cpp
// safe_cast_ZW.cpp
// compile with: /ZW /EHsc

using namespace default;
using namespace Platform;

interface class I1 {};
interface class I2 {};
interface class I3 {};

ref class X : public I1, public I2 {};

int main(Array<String^>^ args) {
   I1^ i1 = ref new X;
   I2^ i2 = safe_cast<I2^>(i1);   // OK, I1 and I2 have common type: X
   // I2^ i3 = static_cast<I2^>(i1);   C2440 use safe_cast instead
   try {
      I3^ i4 = safe_cast<I3^>(i1);   // Fails because i1 is not derived from I3.
   }
   catch(InvalidCastException^ ic) {
   wprintf(L"Caught expected exception: %s\n", ic->Message);
   }
}
```

```Output
Caught expected exception: InvalidCastException
```

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

**safe_cast** umožňuje změnit typ výrazu a generovat ověřitelného kódu MSIL.

### <a name="syntax"></a>Syntaxe

```cpp
[cli]:: safe_cast< type-id >( expression )
```

### <a name="parameters"></a>Parametry

*id typu*<br/>
Popisovač pro odkaz nebo typ hodnoty, typ hodnoty nebo odkaz sledování na typ odkazu nebo hodnoty.

*výraz*<br/>
Výraz, který se vyhodnotí jako popisovač pro odkaz nebo typ hodnoty, typ hodnoty nebo odkaz sledování na typ odkazu nebo hodnoty.

### <a name="remarks"></a>Poznámky

Výraz `safe_cast<` *id typu*`>(`*výraz* `)` převede operand *výraz* na objekt typu *id typu*.

Kompilátor přijme [static_cast](../cpp/static-cast-operator.md) ve většině případů, které bude přijímat **safe_cast**.  Ale **safe_cast** je zaručeno, že k tvorbě ověřitelného kódu MSIL, přičemž **static_cast** by mohla vést neověřitelný MSIL.  Zobrazit [prázdná a ověřitelný kód (C + +/ CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md) a [Peverify.exe (Nástroj PEVerify)](/dotnet/framework/tools/peverify-exe-peverify-tool) Další informace o kódu s možností ověření.

Stejně jako **static_cast**, **safe_cast** vyvolá uživatelem definovaných převodů.

Další informace o přetypování, naleznete v tématu [operátory přetypování](../cpp/casting-operators.md).

**safe_cast** se nevztahuje **const_cast** (přetypovat pryč **const**).

**safe_cast** je v oboru názvů rozhraní příkazového řádku.  Zobrazit [Platform, default a cli obory názvů](platform-default-and-cli-namespaces-cpp-component-extensions.md) Další informace.

Další informace o **safe_cast**, naleznete v tématu:

- [Přetypování ve stylu jazyka pomocí možnosti /clr (C++/CLI)](c-style-casts-with-clr-cpp-cli.md)

- [Postupy: Používání operátoru safe_cast v jazyce C + +/ CLI](../dotnet/how-to-use-safe-cast-in-cpp-cli.md)

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/clr`

### <a name="examples"></a>Příklady

Jeden příklad, ve kterém kompilátor nepřijímá **static_cast** přijme, ale **safe_cast** je pro přetypování mezi typy nesouvisejících rozhraní.  S **safe_cast**, kompilátor nevydá Chyba převodu a provede kontrolu za běhu, jestli je možné přetypování

```cpp
// safe_cast.cpp
// compile with: /clr
using namespace System;

interface class I1 {};
interface class I2 {};
interface class I3 {};

ref class X : public I1, public I2 {};

int main() {
   I1^ i1 = gcnew X;
   I2^ i2 = safe_cast<I2^>(i1);   // OK, I1 and I2 have common type: X
   // I2^ i3 = static_cast<I2^>(i1);   C2440 use safe_cast instead
   try {
      I3^ i4 = safe_cast<I3^>(i1);   // fail at runtime, no common type
   }
   catch(InvalidCastException^) {
      Console::WriteLine("Caught expected exception");
   }
}
```

```Output
Caught expected exception
```

## <a name="see-also"></a>Viz také:

[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)
