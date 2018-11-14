---
title: Platform::Box – třída
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Box
ms.assetid: b3d7ea37-e98a-4fbc-80b0-ad35e50250c6
ms.openlocfilehash: 29cbe852dcd606ea5cf2953c709fc8e47b89e1f1
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327028"
---
# <a name="platformbox-class"></a>Platform::Box – třída

Umožňuje typ hodnoty, jako `Windows::Foundation::DateTime` nebo skalární typ. například `int` k uložení do `Platform::Object` typu. Obvykle není nutné používat `Box` explicitně, protože zabalení implicitně dojde, pokud přetypovat na typ hodnoty `Object^`.

### <a name="syntax"></a>Syntaxe

```cpp
ref class Box abstract;
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** vccorlib.h

**Namespace:** platformy

### <a name="members"></a>Členové

|Člen|Popis|
|------------|-----------------|
|[Pole](#ctor) | Vytvoří `Box` , který může zapouzdřit hodnotu zadaného typu. |
|[operátor pole&lt;const T&gt;^](#box-const-t) | Umožňuje převod na uzavřené určení z `const` hodnotu třídy `T` nebo `enum` třídy `T` k `Box<T>`. |
|[operátor pole&lt;const volatile T&gt;^](#box-const-volatile-t) | Umožňuje převod na uzavřené určení z `const volatile` hodnotu třídy `T` nebo `enum` typ `T` k `Box<T>`. |
|[operátor pole&lt;T&gt;^](#box-t) | Umožňuje zabalení převody z hodnotové třídy `T` k `Box<T>`. |
|[operátor pole&lt;volatile T&gt;^](#box-volatile-t) | Umožňuje převod na uzavřené určení z `volatile` hodnotu třídy `T` nebo `enum` typ `T` k `Box<T>`. |
|[Box::Operator T](#t) | Umožňuje zabalení převody z hodnotové třídy `T` nebo `enum` třídy `T` k `Box<T>`. |
|[Value – vlastnost](#value) | Vrátí hodnotu, která jsou zapouzdřena v `Box` objektu. |

## <a name="ctor"></a> Box::Box konstruktor

Vytvoří `Box` , který může zapouzdřit hodnotu zadaného typu.

### <a name="syntax"></a>Syntaxe

```cpp
Box(T valueArg);
```

### <a name="parameters"></a>Parametry

*valueArg*<br/>
Hodnota, která má být pevně určený typ – například `int`, `bool`, `float64`, `DateTime`.

## <a name="box-const-t"></a> Pole Box::Operator&lt;const T&gt;^ – operátor

Umožňuje převod na uzavřené určení z `const` hodnotu třídy `T` nebo `enum` třídy `T` k `Box<T>`.

### <a name="syntax"></a>Syntaxe

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Žádné hodnotová třída, struktura hodnotu nebo výčtového typu. Obsahuje vestavěné typy v [výchozí obor názvů](../cppcx/default-namespace.md).

### <a name="return-value"></a>Návratová hodnota

A `Platform::Box<T>^` instanci, která představuje původní hodnoty v poli v referenční třídě.

## <a name="box-const-volatile-t"></a> Pole Box::Operator&lt;const volatile T&gt;^ – operátor

Umožňuje převod na uzavřené určení z `const volatile` hodnotu třídy `T` nebo `enum` typ `T` k `Box<T>`.

### <a name="syntax"></a>Syntaxe

```cpp
operator Box<const volatile T>^(const volatile T valueType);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Žádné typ výčtu, hodnotová třída nebo struktura hodnotu. Obsahuje vestavěné typy v [výchozí obor názvů](../cppcx/default-namespace.md).

### <a name="return-value"></a>Návratová hodnota

A `Platform::Box<T>^` instanci, která představuje původní hodnoty v poli v referenční třídě.

## <a name="box-t"></a> Pole Box::Operator&lt;T&gt;^ – operátor

Umožňuje zabalení převody z hodnotové třídy `T` k `Box<T>`.

### <a name="syntax"></a>Syntaxe

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Žádné typ výčtu, hodnotová třída nebo struktura hodnotu. Obsahuje vestavěné typy v [výchozí obor názvů](../cppcx/default-namespace.md).

### <a name="return-value"></a>Návratová hodnota

A `Platform::Box<T>^` instanci, která představuje původní hodnoty v poli v referenční třídě.

## <a name="box-volatile-t"></a> Pole Box::Operator&lt;volatile T&gt;^ – operátor

Umožňuje převod na uzavřené určení z `volatile` hodnotu třídy `T` nebo `enum` typ `T` k `Box<T>`.

### <a name="syntax"></a>Syntaxe

```cpp
operator Box<volatile T>^(volatile T valueType);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Žádné typ výčtu, hodnotová třída nebo struktura hodnotu. Obsahuje vestavěné typy v [výchozí obor názvů](../cppcx/default-namespace.md).

### <a name="return-value"></a>Návratová hodnota

A `Platform::Box<T>^` instanci, která představuje původní hodnoty v poli v referenční třídě.

## <a name="t"></a>  Operátor Box::Operator T

Umožňuje zabalení převody z hodnotové třídy `T` nebo `enum` třídy `T` k `Box<T>`.

### <a name="syntax"></a>Syntaxe

```cpp
operator Box<T>^(T valueType);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Žádné typ výčtu, hodnotová třída nebo struktura hodnotu. Obsahuje vestavěné typy v [výchozí obor názvů](../cppcx/default-namespace.md).

### <a name="return-value"></a>Návratová hodnota

A `Platform::Box<T>^` instanci, která představuje původní hodnoty v poli v referenční třídě.

## <a name="value"></a> Vlastnost Box::Value

Vrátí hodnotu, která jsou zapouzdřena v `Box` objektu.

### <a name="syntax"></a>Syntaxe

```cpp
virtual property T Value{
   T get();
}
```

### <a name="return-value"></a>Návratová hodnota

Vrátí zabalené hodnoty stejného typu jako původně předtím, než je zabalená.

## <a name="see-also"></a>Viz také

[Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)<br/>
[Zabalení](../cppcx/boxing-c-cx.md)