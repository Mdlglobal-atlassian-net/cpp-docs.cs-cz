---
title: Platform::stringreference – třída
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::StringReference::StringReference
- VCCORLIB/Platform::StringReference::Data
- VCCORLIB/Platform::StringReference::Length
- VCCORLIB/Platform::StringReference::GetHSTRING
- VCCORLIB/Platform::StringReference::GetString
ms.assetid: 2d09c7ec-0f16-458e-83ed-7225a1b9221e
ms.openlocfilehash: 7b6ab42dc630ce7e0014534064e8f1ce6da00857
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182987"
---
# <a name="platformstringreference-class"></a>Platform::stringreference – třída

Typ optimalizace, které můžete použít k předávání řetězcovými daty z `Platform::String^` vstupní parametry jiným metodám, přičemž minimum je operace kopírování.

## <a name="syntax"></a>Syntaxe

```cpp
class StringReference
```

### <a name="remarks"></a>Poznámky

### <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[StringReference::StringReference](#ctor)|Dva konstruktory pro vytváření instancí `StringReference`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[StringReference::Data](#data)|Vrátí řetězec data jako pole hodnot char16 typu.|
|[StringReference::Length](#length)|Vrátí počet znaků v řetězci.|
|[StringReference::GetHSTRING](#gethstring)|Vrátí řetězec data jako HSTRING.|
|[StringReference::GetString](#getstring)|Vrátí řetězec data jako `Platform::String^`.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[StringReference::operator =](#operator-assign)|Přiřadí `StringReference` do nového `StringReference` instance.|
|[StringReference::operator()](#operator-call)|Převede `StringReference` k `Platform::String^`.|

### <a name="requirements"></a>Požadavky

**Minimální podporovaná klienta:** Windows 8

**Minimální podporovaná serveru:** Windows Server 2012

**Namespace:** Platforma

**Záhlaví:** vccorlib.h

## <a name="data"></a>  StringReference::Data – metoda

Vrátí obsah tohoto `StringReference` jako pole hodnot char16 typu.

### <a name="syntax"></a>Syntaxe

```cpp
const ::default::char16 * Data() const;
```

### <a name="return-value"></a>Návratová hodnota

Pole znaků textu char16 kódování UNICODE.

## <a name="gethstring"></a>  StringReference::GetHSTRING – metoda

Vrátí obsah řetězce jako `__abi_HSTRING`.

### <a name="syntax"></a>Syntaxe

```cpp
__abi_HSTRING GetHSTRING() const;
```

### <a name="return-value"></a>Návratová hodnota

`__abi_HSTRING` , Který obsahuje data řetězce.

### <a name="remarks"></a>Poznámky

## <a name="getstring"></a>  StringReference::GetString – metoda

Vrátí obsah řetězce jako `Platform::String^`.

### <a name="syntax"></a>Syntaxe

```cpp
__declspec(no_release_return) __declspec(no_refcount)
    ::Platform::String^ GetString() const;
```

### <a name="return-value"></a>Návratová hodnota

A `Platform::String^` , který obsahuje data řetězce.

## <a name="length"></a>  StringReference::Length – metoda

Vrátí počet znaků v řetězci.

### <a name="syntax"></a>Syntaxe

```cpp
unsigned int Length() const;
```

### <a name="return-value"></a>Návratová hodnota

Celé číslo bez znaménka, která určuje počet znaků v řetězci.

### <a name="remarks"></a>Poznámky

## <a name="operator-assign"></a>  StringReference::operator = – operátor

Přiřadí zadaný objekt do aktuální `StringReference` objektu.

### <a name="syntax"></a>Syntaxe

```cpp
StringReference& operator=(const StringReference& __fstrArg);
StringReference& operator=(const ::default::char16* __strArg);
```

### <a name="parameters"></a>Parametry

*__fstrArg*<br/>
Adresa `StringReference` objekt, který slouží k inicializaci aktuální `StringReference` objektu.

*__strArg*<br/>
Ukazatel na pole char16 hodnoty, které slouží k inicializaci aktuální `StringReference` objektu.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt typu `StringReference`.

### <a name="remarks"></a>Poznámky

Protože `StringReference` je standardní třídu C++ a ne ref class, nezobrazí se v **prohlížeče objektů**.

## <a name="operator-call"></a>  StringReference::operator() – operátor

Převede `StringReference` do objektu `Platform::String^` objektu.

### <a name="syntax"></a>Syntaxe

```cpp
__declspec(no_release_return) __declspec(no_refcount)
         operator ::Platform::String^() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač pro objekt typu `Platform::String`.

## <a name="ctor"></a>  StringReference::StringReference konstruktor

Inicializuje novou instanci třídy `StringReference` třídy.

### <a name="syntax"></a>Syntaxe

```cpp
StringReference();
StringReference(const StringReference& __fstrArg);
StringReference(const ::default::char16* __strArg);
StringReference(const ::default::char16* __strArg, size_t __lenArg);
```

### <a name="parameters"></a>Parametry

*__fstrArg*<br/>
`StringReference` Jehož data slouží k inicializaci nové instance.

*__strArg*<br/>
Ukazatel na pole char16 hodnoty, které slouží k inicializaci nové instance.

*__lenArg*<br/>
Počet prvků v `__strArg`.

### <a name="remarks"></a>Poznámky

První verze tento konstruktor je výchozí konstruktor. Druhá verze inicializuje novou `StringReference` instance třídy z objektu, která je zadána `__fstrArg` parametru. Třetí a čtvrtá přetížení inicializovat nový `StringReference` instanci char16 hodnoty z pole. char16 hodnota představuje znak UNICODE text 16 bitů.

## <a name="see-also"></a>Viz také:

[Platform::StringReference – třída](../cppcx/platform-stringreference-class.md)
