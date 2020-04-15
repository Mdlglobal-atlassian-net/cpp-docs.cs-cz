---
title: Platforma::Třída krabice
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Box
ms.assetid: b3d7ea37-e98a-4fbc-80b0-ad35e50250c6
ms.openlocfilehash: 7484bcda3f05a8a9e56a33222d0630d4597e1219
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354763"
---
# <a name="platformbox-class"></a>Platforma::Třída krabice

Umožňuje typ hodnoty, `Windows::Foundation::DateTime` jako je například `int` nebo skalární `Platform::Object` typ, například být uložen v typu. Obvykle není nutné explicitně používat, `Box` protože zabalení se stane `Object^`implicitně při přetypování typu hodnoty na .

### <a name="syntax"></a>Syntaxe

```cpp
ref class Box abstract;
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** vccorlib.h

**Obor názvů:** Platforma

### <a name="members"></a>Členové

|Člen|Popis|
|------------|-----------------|
|[Box](#ctor) | `Box` Vytvoří, který může zapouzdřit hodnotu zadaného typu. |
|[operátor&lt;Box const T&gt;^](#box-const-t) | Povolí převody zabalení `T` z `enum` `T` `Box<T>` `const` třídy nebo třídy hodnoty na . |
|[operátor&lt;Box const těkavý T&gt;^](#box-const-volatile-t) | Povolí převody zabalení `T` z `enum` `T` `Box<T>` `const volatile` třídy nebo typu hodnoty na . |
|[obsluha&lt;Box T&gt;^](#box-t) | Povolí převody zabalení `T` z `Box<T>`třídy hodnoty na . |
|[operátor&lt;Box těkavý T&gt;^](#box-volatile-t) | Povolí převody zabalení `T` z `enum` `T` `Box<T>` `volatile` třídy nebo typu hodnoty na . |
|[Kolonka::operátor T](#t) | Povolí převody zabalení `T` z `enum` `T` třídy nebo třídy hodnoty na `Box<T>`. |
|[Value – vlastnost](#value) | Vrátí hodnotu, která je zapouzdřena v objektu. `Box` |

## <a name="boxbox-constructor"></a><a name="ctor"></a>Box::Konstruktor krabice

`Box` Vytvoří, který může zapouzdřit hodnotu zadaného typu.

### <a name="syntax"></a>Syntaxe

```cpp
Box(T valueArg);
```

### <a name="parameters"></a>Parametry

*valueArg*<br/>
Typ hodnoty, která má být zabalena `bool` `float64`– `DateTime`například `int`, , .

## <a name="boxoperator-boxltconst-tgt-operator"></a><a name="box-const-t"></a>Box::operátor&lt;Box const T&gt;^ Operátor

Povolí převody zabalení `T` z `enum` `T` `Box<T>` `const` třídy nebo třídy hodnoty na .

### <a name="syntax"></a>Syntaxe

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Libovolná třída hodnot, struktura hodnoty nebo typ výčtu. Zahrnuje předdefinované typy ve [výchozím oboru názvů](../cppcx/default-namespace.md).

### <a name="return-value"></a>Návratová hodnota

Instance, `Platform::Box<T>^` která představuje původní hodnotu zabalenou ve třídě ref.

## <a name="boxoperator-boxltconst-volatile-tgt-operator"></a><a name="box-const-volatile-t"></a>Box::operátor&lt;Box const&gt;volatile T ^ Operátor

Povolí převody zabalení `T` z `enum` `T` `Box<T>` `const volatile` třídy nebo typu hodnoty na .

### <a name="syntax"></a>Syntaxe

```cpp
operator Box<const volatile T>^(const volatile T valueType);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Libovolný typ výčtu, třída hodnoty nebo struktura hodnoty. Zahrnuje předdefinované typy ve [výchozím oboru názvů](../cppcx/default-namespace.md).

### <a name="return-value"></a>Návratová hodnota

Instance, `Platform::Box<T>^` která představuje původní hodnotu zabalenou ve třídě ref.

## <a name="boxoperator-boxlttgt-operator"></a><a name="box-t"></a>Box::operátor&lt;Box&gt;T ^ Operátor

Povolí převody zabalení `T` z `Box<T>`třídy hodnoty na .

### <a name="syntax"></a>Syntaxe

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Libovolný typ výčtu, třída hodnoty nebo struktura hodnoty. Zahrnuje předdefinované typy ve [výchozím oboru názvů](../cppcx/default-namespace.md).

### <a name="return-value"></a>Návratová hodnota

Instance, `Platform::Box<T>^` která představuje původní hodnotu zabalenou ve třídě ref.

## <a name="boxoperator-boxltvolatile-tgt-operator"></a><a name="box-volatile-t"></a>Box::operátor&lt;Box&gt;volatile T ^ Operátor

Povolí převody zabalení `T` z `enum` `T` `Box<T>` `volatile` třídy nebo typu hodnoty na .

### <a name="syntax"></a>Syntaxe

```cpp
operator Box<volatile T>^(volatile T valueType);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Libovolný typ výčtu, třída hodnoty nebo struktura hodnoty. Zahrnuje předdefinované typy ve [výchozím oboru názvů](../cppcx/default-namespace.md).

### <a name="return-value"></a>Návratová hodnota

Instance, `Platform::Box<T>^` která představuje původní hodnotu zabalenou ve třídě ref.

## <a name="boxoperator-t-operator"></a><a name="t"></a>Box::operátor T Operátor

Povolí převody zabalení `T` z `enum` `T` třídy nebo třídy hodnoty na `Box<T>`.

### <a name="syntax"></a>Syntaxe

```cpp
operator Box<T>^(T valueType);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Libovolný typ výčtu, třída hodnoty nebo struktura hodnoty. Zahrnuje předdefinované typy ve [výchozím oboru názvů](../cppcx/default-namespace.md).

### <a name="return-value"></a>Návratová hodnota

Instance, `Platform::Box<T>^` která představuje původní hodnotu zabalenou ve třídě ref.

## <a name="boxvalue-property"></a><a name="value"></a>Box::Vlastnost Value

Vrátí hodnotu, která je zapouzdřena v objektu. `Box`

### <a name="syntax"></a>Syntaxe

```cpp
virtual property T Value{
   T get();
}
```

### <a name="return-value"></a>Návratová hodnota

Vrátí zabalenou hodnotu se stejným typem, jaký měl původně před tím, než byla zabalena.

## <a name="see-also"></a>Viz také

[Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)<br/>
[Zabalení](../cppcx/boxing-c-cx.md)
