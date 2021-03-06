---
title: Platform::MTAThreadAttribute – třída
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::MTAThreadAttribute::Equals
- VCCORLIB/Platform::MTAThreadAttribute::GetHashCode
- VCCORLIB/Platform::MTAThreadAttribute::ToString
helpviewer_keywords:
- Platform::MTAThreadAttribute Class
ms.assetid: bfc546a7-4333-4407-85b4-4721565e1f44
ms.openlocfilehash: 4564def412834ae0586292e8aa533d3b2bd0d679
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152667"
---
# <a name="platformmtathreadattribute-class"></a>Platform::MTAThreadAttribute – třída

Označuje, že model vláken pro aplikaci je vícevláknového objektu apartment (MTA).

## <a name="syntax"></a>Syntaxe

```
public ref class MTAThreadAttribute sealed : Attribute
```

### <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[1 konstruktor MTAThreadAttribute](#ctor) konstruktor|Inicializuje novou instanci třídy.|

### <a name="public-methods"></a>Veřejné metody

Atribut MTAThreadAttribute dědí z [Platform::Object – třída](../cppcx/platform-object-class.md). MTAThreadAttribute také přetížení nebo má následující členy:

|Název|Popis|
|----------|-----------------|
|[MTAThreadAttribute::Equals](#equals)|Určuje, zda se zadaný objekt rovná aktuálnímu objektu.|
|[MTAThreadAttribute::GetHashCode](#gethashcode)|Vrátí kód hash této instance.|
|[MTAThreadAttribute::ToString](#tostring)|Vrací řetězec, který představuje aktuální objekt.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Platform`

### <a name="requirements"></a>Požadavky

**Metadata:** platform.winmd

**Namespace:** Platforma

## <a name="ctor"></a> MTAThreadAttribute konstruktor

Inicializuje novou instanci třídy MTAThreadAttribute.

### <a name="syntax"></a>Syntaxe

```cpp
public:MTAThreadAttribute();
```

## <a name="equals"></a> MTAThreadAttribute::Equals

Určuje, zda se zadaný objekt rovná aktuálnímu objektu.

### <a name="syntax"></a>Syntaxe

```cpp
public:virtual override bool Equals( Object^ obj );
```

### <a name="parameters"></a>Parametry

*obj*<br/>
Objekt k porovnání.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud jsou objekty stejné; jinak **false**.

## <a name="gethashcode"></a> MTAThreadAttribute::GetHashCode

Vrátí kód hash této instance.

### <a name="syntax"></a>Syntaxe

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>Návratová hodnota

Kód hash této instance

## <a name="tostring"></a> MTAThreadAttribute::ToString

Vrací řetězec, který představuje aktuální objekt.

### <a name="syntax"></a>Syntaxe

```cpp
public:String^ ToString();
```

### <a name="return-value"></a>Návratová hodnota

Řetězec, který představuje aktuální objekt.

## <a name="see-also"></a>Viz také:

[Platforma Namespace](platform-namespace-c-cx.md)
