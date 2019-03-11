---
title: Platform::STAThreadAttribute – třída
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Platform
- COLLECTION/Platform::Platform::STAThreadAttribute constructor 1
- COLLECTION/Platform::Platform::STAThreadAttribute::Equals
- COLLECTION/Platform::Platform::STAThreadAttribute::GetHashCode
- COLLECTION/Platform::Platform::STAThreadAttribute::ToString
helpviewer_keywords:
- Platform::STAThreadAttribute Class
ms.assetid: f97960fc-e673-4d9e-910a-54c8415411c4
ms.openlocfilehash: 05fb2879839c504f49f56e25ffe28329aa969c69
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743571"
---
# <a name="platformstathreadattribute-class"></a>Platform::STAThreadAttribute – třída

Označuje, že model vláken pro aplikaci je jednovláknový apartment (STA).

## <a name="syntax"></a>Syntaxe

```
public ref class STAThreadAttribute sealed : Attribute
```

### <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Atribut STAThreadAttribute konstruktor 1](#ctor)|Inicializuje novou instanci třídy.|

### <a name="public-methods"></a>Veřejné metody

Atribut STAThreadAttribute dědí z [Platform::Object – třída](../cppcx/platform-object-class.md). Atribut STAThreadAttribute také přetížení nebo má následující členy:

|Název|Popis|
|----------|-----------------|
|[STAThreadAttribute::Equals](#equals)|Určuje, zda se zadaný objekt rovná aktuálnímu objektu.|
|[STAThreadAttribute::GetHashCode](#gethashcode)|Vrátí kód hash této instance.|
|[STAThreadAttribute::ToString](#tostring)|Vrací řetězec, který představuje aktuální objekt.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Platform`

### <a name="requirements"></a>Požadavky

**Záhlaví:** collection.h

**Namespace:** Platforma

## <a name="ctor"></a> Atribut STAThreadAttribute konstruktor

Inicializuje novou instanci třídy atribut STAThreadAttribute.

### <a name="syntax"></a>Syntaxe

```cpp
public:STAThreadAttribute();
```

## <a name="equals"></a> STAThreadAttribute::Equals

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

## <a name="gethashcode"></a> STAThreadAttribute::GetHashCode

Vrátí kód hash této instance.

### <a name="syntax"></a>Syntaxe

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>Návratová hodnota

Kód hash této instance

## <a name="tostring"></a> STAThreadAttribute::ToString

Vrací řetězec, který představuje aktuální objekt.

### <a name="syntax"></a>Syntaxe

```cpp
public:String^ ToString();
```

### <a name="return-value"></a>Návratová hodnota

Řetězec, který představuje aktuální objekt.

## <a name="see-also"></a>Viz také:

[Platforma Namespace](platform-namespace-c-cx.md)
