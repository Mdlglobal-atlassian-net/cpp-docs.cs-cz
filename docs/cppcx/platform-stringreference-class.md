---
title: Platform::StringReference – třída
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::StringReference::StringReference
- VCCORLIB/Platform::StringReference::Data
- VCCORLIB/Platform::StringReference::Length
- VCCORLIB/Platform::StringReference::GetHSTRING
- VCCORLIB/Platform::StringReference::GetString
ms.assetid: 2d09c7ec-0f16-458e-83ed-7225a1b9221e
ms.openlocfilehash: 4748eecdf67ae5a60ddf97783a934a05e80b406c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374652"
---
# <a name="platformstringreference-class"></a>Platform::StringReference – třída

Typ optimalizace, který můžete použít `Platform::String^` k předání řetězcových dat ze vstupních parametrů do jiných metod s minimálními operacemi kopírování.

## <a name="syntax"></a>Syntaxe

```cpp
class StringReference
```

### <a name="remarks"></a>Poznámky

### <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[StringReference::StringReference](#ctor)|Dva konstruktory pro vytváření `StringReference`instancí .|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[StringReference::Data](#data)|Vrátí data řetězce jako pole hodnot char16.|
|[StringReference::Délka](#length)|Vrátí počet znaků v řetězci.|
|[StringReference::GetHSTRING](#gethstring)|Vrátí data řetězce jako HSTRING.|
|[StringReference::GetString](#getstring)|Vrátí data řetězce `Platform::String^`jako .|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[StringReference::operátor=](#operator-assign)|Přiřadí `StringReference` a nové `StringReference` instanci.|
|[StringReference::operátor()](#operator-call)|Převede `StringReference` a `Platform::String^`na .|

### <a name="requirements"></a>Požadavky

**Minimální podporovaný klient:** Windows 8

**Minimální podporovaný server:** Windows Server 2012

**Obor názvů:** Platforma

**Záhlaví:** vccorlib.h

## <a name="stringreferencedata-method"></a><a name="data"></a>StringReference::Data Metoda

Vrátí obsah tohoto `StringReference` jako pole char16 hodnoty.

### <a name="syntax"></a>Syntaxe

```cpp
const ::default::char16 * Data() const;
```

### <a name="return-value"></a>Návratová hodnota

Pole znaků znaku 16 UNICODE.

## <a name="stringreferencegethstring-method"></a><a name="gethstring"></a>StringReference::Metoda GetHSTRING

Vrátí obsah řetězce jako `__abi_HSTRING`.

### <a name="syntax"></a>Syntaxe

```cpp
__abi_HSTRING GetHSTRING() const;
```

### <a name="return-value"></a>Návratová hodnota

A `__abi_HSTRING` který obsahuje data řetězce.

### <a name="remarks"></a>Poznámky

## <a name="stringreferencegetstring-method"></a><a name="getstring"></a>StringReference::Metoda GetString

Vrátí obsah řetězce jako `Platform::String^`.

### <a name="syntax"></a>Syntaxe

```cpp
__declspec(no_release_return) __declspec(no_refcount)
    ::Platform::String^ GetString() const;
```

### <a name="return-value"></a>Návratová hodnota

A, `Platform::String^` který obsahuje data řetězce.

## <a name="stringreferencelength-method"></a><a name="length"></a>StringReference::Metoda length

Vrátí počet znaků v řetězci.

### <a name="syntax"></a>Syntaxe

```cpp
unsigned int Length() const;
```

### <a name="return-value"></a>Návratová hodnota

Nepodepsané celé číslo, které určuje počet znaků v řetězci.

### <a name="remarks"></a>Poznámky

## <a name="stringreferenceoperator-operator"></a><a name="operator-assign"></a>StringReference::operátor= Operátor

Přiřadí zadaný objekt `StringReference` k aktuálnímu objektu.

### <a name="syntax"></a>Syntaxe

```cpp
StringReference& operator=(const StringReference& __fstrArg);
StringReference& operator=(const ::default::char16* __strArg);
```

### <a name="parameters"></a>Parametry

*__fstrArg*<br/>
Adresa objektu, `StringReference` který slouží k inicializaci aktuálního `StringReference` objektu.

*__strArg*<br/>
Ukazatel na pole char16 hodnoty, které se používá `StringReference` k inicializaci aktuálního objektu.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt typu `StringReference`.

### <a name="remarks"></a>Poznámky

Protože `StringReference` je standardní třída C++ a není třída ref, nezobrazí se v **prohlížeči objektů**.

## <a name="stringreferenceoperator--operator"></a><a name="operator-call"></a>StringReference::operátor() Operátor

Převede `StringReference` objekt na `Platform::String^` objekt.

### <a name="syntax"></a>Syntaxe

```cpp
__declspec(no_release_return) __declspec(no_refcount)
         operator ::Platform::String^() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač objektu typu `Platform::String`.

## <a name="stringreferencestringreference-constructor"></a><a name="ctor"></a>StringReference::Konstruktor StringReference

Inicializuje novou instanci třídy. `StringReference`

### <a name="syntax"></a>Syntaxe

```cpp
StringReference();
StringReference(const StringReference& __fstrArg);
StringReference(const ::default::char16* __strArg);
StringReference(const ::default::char16* __strArg, size_t __lenArg);
```

### <a name="parameters"></a>Parametry

*__fstrArg*<br/>
Jehož `StringReference` data se používá k inicializaci nové instance.

*__strArg*<br/>
Ukazatel na pole char16 hodnoty, které se používá k inicializaci nové instance.

*__lenArg*<br/>
Počet prvků v `__strArg`.

### <a name="remarks"></a>Poznámky

První verze tohoto konstruktoru je výchozí konstruktor. Druhá verze inicializuje `StringReference` novou třídu instance z objektu, který je určen parametrem. `__fstrArg` Třetí a čtvrté přetížení inicializovat novou `StringReference` instanci z pole char16 hodnoty. char16 představuje 16bitový textový znak UNICODE.

## <a name="see-also"></a>Viz také

[Platform::StringReference – třída](../cppcx/platform-stringreference-class.md)
