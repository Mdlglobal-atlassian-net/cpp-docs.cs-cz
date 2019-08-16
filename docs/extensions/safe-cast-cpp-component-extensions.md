---
title: safe_cast (C++/CLI a C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- safe_cast
- safe_cast_cpp
- stdcli::language::safe_cast
helpviewer_keywords:
- safe_cast keyword [C++]
ms.assetid: 4fa688bf-a8ec-49bc-a4c5-f48134efa4f7
ms.openlocfilehash: 42e141caed720aa29cf918a2bdf69d9a2c4203dc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509547"
---
# <a name="safe_cast-ccli-and-ccx"></a>safe_cast (C++/CLI a C++/CX)

Operace **safe_cast** vrací zadaný výraz jako zadaný typ, pokud je úspěšný; v opačném `InvalidCastException`případě vyvolá výjimku.

## <a name="all-runtimes"></a>Všechny moduly runtime

(Žádné poznámky k této funkci jazyka se nevztahují na všechny moduly runtime.)

### <a name="syntax"></a>Syntaxe

```cpp
[default]:: safe_cast< type-id >( expression )
```

## <a name="windows-runtime"></a>prostředí Windows Runtime

**safe_cast** umožňuje změnit typ zadaného výrazu. V situacích, kdy plně očekáváte, že proměnnou nebo parametr převést na určitý typ, můžete použít **safe_cast** bez bloku **try-catch** k detekci chyb programování během vývoje. Další informace naleznete v tématu [přetypováníC++(/CX)](../cppcx/casting-c-cx.md).

### <a name="syntax"></a>Syntaxe

```cpp
[default]:: safe_cast< type-id >( expression )
```

### <a name="parameters"></a>Parametry

*Typ – ID*<br/>
Typ, na který se má *výraz* převést Popisovač typu odkazu nebo hodnoty, typu hodnoty nebo odkazu sledování na typ odkazu nebo hodnoty.

*vyjádření*<br/>
Výraz, který je vyhodnocen jako popisovač na typ odkazu nebo hodnoty, typ hodnoty nebo odkaz sledování na typ odkazu nebo hodnoty.

### <a name="remarks"></a>Poznámky

**safe_cast** vyvolá `InvalidCastException` , pokud nemůže převést *výraz* na typ určený identifikátorem *Type-ID*. Chcete- `InvalidCastException`li zachytit, určete možnost kompilátoru [/EH (model zpracování výjimek)](../build/reference/eh-exception-handling-model.md) a použijte příkaz **try/catch** .

### <a name="requirements"></a>Požadavky

Možnost kompilátoru:`/ZW`

### <a name="examples"></a>Příklady

Následující příklad kódu ukazuje, jak použít **safe_cast** s prostředí Windows Runtime.

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

**safe_cast** umožňuje změnit typ výrazu a generovat ověřitelný kód jazyka MSIL.

### <a name="syntax"></a>Syntaxe

```cpp
[cli]:: safe_cast< type-id >( expression )
```

### <a name="parameters"></a>Parametry

*Typ – ID*<br/>
Popisovač typu odkazu nebo hodnoty, typu hodnoty nebo odkazu sledování na typ odkazu nebo hodnoty.

*vyjádření*<br/>
Výraz, který je vyhodnocen jako popisovač na typ odkazu nebo hodnoty, typ hodnoty nebo odkaz sledování na typ odkazu nebo hodnoty.

### <a name="remarks"></a>Poznámky

`safe_cast<``>(`*Výraz*typu Expression-ID Převede výraz operandu na objekt typu ID.`)`

Kompilátor bude přijímat [static_cast](../cpp/static-cast-operator.md) na většině míst, kde bude akceptovat **safe_cast**.  **Safe_cast** je však zaručeno vytvořit ověřitelelné MSIL, kde jako **static_cast** by mohlo vytvořit neověřitelný jazyk MSIL.  Další informace o ověřitelném kódu naleznete v tématu [čistý a ověřitelný kód (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md) a [Nástroj Peverify. exe (Nástroj PEVerify nástroj)](/dotnet/framework/tools/peverify-exe-peverify-tool) .

Podobně jako **static_cast**, **safe_cast** vyvolá uživatelsky definované převody.

Další informace o přetypováních naleznete v tématu [operátory přetypování](../cpp/casting-operators.md).

**safe_cast** nepoužívá **const_cast** (const cast).

**safe_cast** je v oboru názvů CLI.  Další informace najdete v tématu [obory názvů Platform, default a CLI](platform-default-and-cli-namespaces-cpp-component-extensions.md) .

Další informace o **safe_cast**najdete v tématech:

- [Přetypování ve stylu jazyka C s možnostíC++/CLR (/CLI)](c-style-casts-with-clr-cpp-cli.md)

- [Postupy: Používání operátoru safe_cast v jazyce C++/CLI](../dotnet/how-to-use-safe-cast-in-cpp-cli.md)

### <a name="requirements"></a>Požadavky

Možnost kompilátoru:`/clr`

### <a name="examples"></a>Příklady

Jeden příklad, kde kompilátor nebude přijímat **static_cast** , ale přijme **safe_cast** , je pro přetypování mezi nesouvisejícími typy rozhraní.  V **safe_cast**kompilátor nevydá chybu převodu a provede kontrolu za běhu za účelem zjištění, zda je možné přetypování.

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
