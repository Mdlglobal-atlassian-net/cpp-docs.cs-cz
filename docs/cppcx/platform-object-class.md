---
title: Platforma::Třída objektů
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Object::Object
- VCCORLIB/Platform::Object::Equals
- VCCORLIB/Platform::Object::GetHashCode
- VCCORLIB/Platform::Object::ReferenceEquals
- VCCORLIB/Platform::ToString
- VCCORLIB/Platform::GetType
helpviewer_keywords:
- Object class
ms.assetid: 709e84a8-0bff-471b-bc14-63e424080b5a
ms.openlocfilehash: 8300ec484bdb58919ce8e450b706dd07c275ceee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363690"
---
# <a name="platformobject-class"></a>Platforma::Třída objektů

Poskytuje běžné chování pro třídy ref a struktury ref v aplikacích prostředí Windows Runtime. Všechny instance třídy ref a ref struct jsou implicitně převoditelné na Platform::Object^ a mohou přepsat její virtuální metodu ToString.

## <a name="syntax"></a>Syntaxe

```cpp
public ref class Object : Object
```

### <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[Objekt::Objekt](#ctor)|Inicializuje novou instanci třídy Object.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[Objekt::Rovná se](#equals)|Určí, zda se zadaný objekt rovná aktuálnímu objektu.|
|[Objekt::GetHashCode](#gethashcode)|Vrátí hodnotu hash pro tuto instanci.|
|[Objekt::ReferenceEquals](#referenceequals)|Určuje, zda jsou zadané instance Object stejné instance.|
|[ToString](#tostring)|Vrátí řetězec, který představuje aktuální objekt. Může být přepsána.|
|[GetType](#gettype)|Získá [Platform::Type,](../cppcx/platform-type-class.md) který popisuje aktuální instanci.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Object`

`Object`

### <a name="requirements"></a>Požadavky

**Záhlaví:** vccorlib.h

**Obor názvů:** Platforma

## <a name="objectequals-method"></a><a name="equals"></a>Objekt::Metoda rovná se

Určí, zda se zadaný objekt rovná aktuálnímu objektu.

### <a name="syntax"></a>Syntaxe

```cpp
bool Equals(
    Object^ obj
)
```

### <a name="parameters"></a>Parametry

*Obj*<br/>
Objekt k porovnání

### <a name="return-value"></a>Návratová hodnota

**true,** pokud jsou objekty stejné, jinak **false**.

## <a name="objectgethashcode-method"></a><a name="gethashcode"></a>Objekt::Metoda GetHashCode

Vrátí `IUnknown`hodnotu * identity pro tuto instanci, pokud se jedná o objekt COM, nebo vypočítanou hodnotu hash, pokud není objektem COM.

### <a name="syntax"></a>Syntaxe

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>Návratová hodnota

Číselná hodnota, která jednoznačně identifikuje tento objekt.

### <a name="remarks"></a>Poznámky

GetHashCode můžete použít k vytvoření klíčů pro objekty v mapách. Kódy hash můžete porovnat pomocí [objektu::Equals](#equals). Pokud je cesta kódu `GetHashCode` velmi `Equals` kritická a není dostatečně rychlá, můžete rozbalit `IUnknown` základní vrstvu COM a provést nativní porovnání ukazatelů.

## <a name="objectgettype-method"></a><a name="gettype"></a>Objekt::Metoda GetType

Vrátí [platformu::Type](../cppcx/platform-type-class.md) objekt, který popisuje typ runtime objektu.

### <a name="syntax"></a>Syntaxe

```cpp
Object::GetType();
```

### <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota

A [Platform::Type](../cppcx/platform-type-class.md) objekt, který popisuje typ runtime objektu.

### <a name="remarks"></a>Poznámky

Statický [Type::GetTypeCode](../cppcx/platform-type-class.md#gettypecode) lze získat [platformu::TypeCode výčet](../cppcx/platform-typecode-enumeration.md) hodnotu, která představuje aktuální typ. To je většinou užitečné pro předdefinované typy. Kód typu pro všechny třídy ref kromě [Platform::String](../cppcx/platform-string-class.md) je Object (1).

Třída [Windows::UI::Xaml::Interop::TypeName](/uwp/api/windows.ui.xaml.interop.typename) se používá v rozhraní CHI systému Windows jako jazykově nezávislý způsob předávání informací o typu mezi součástmi a aplikacemi systému Windows. [Platforma T::Třída typu](../cppcx/platform-type-class.md) má operátory pro převod mezi `Type` a `TypeName`.

Pomocí operátoru [typeid](../extensions/typeid-cpp-component-extensions.md) `Platform::Type` vraťte objekt pro název třídy, například při navigaci mezi stránkami XAML:

```
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

## <a name="objectobject-constructor"></a><a name="ctor"></a>Objekt::Konstruktor objektu

Inicializuje novou instanci třídy Object.

### <a name="syntax"></a>Syntaxe

```cpp
public:Object();
```

## <a name="objectreferenceequals-method"></a><a name="referenceequals"></a>Objekt::Metoda ReferenceEquals

Určuje, zda jsou zadané instance Object stejné instance.

### <a name="syntax"></a>Syntaxe

```cpp
public:static bool ReferenceEquals(  Object^ obj1,   Object^ obj2);
```

### <a name="parameters"></a>Parametry

*obj1*<br/>
První objekt k porovnání

*obj2*<br/>
Druhý objekt k porovnání

### <a name="return-value"></a>Návratová hodnota

**true,** pokud jsou oba objekty stejné; jinak **false**.

## <a name="objecttostring-method-ccx"></a><a name="tostring"></a>Objekt::Metoda tostring (C++/CX)

Vrátí řetězec, který představuje aktuální objekt.

### <a name="syntax"></a>Syntaxe

```cpp
public:
virtual String^ ToString();
```

### <a name="return-value"></a>Návratová hodnota

Řetězec, který představuje aktuální objekt. Tuto metodu můžete přepsat a poskytnout vlastní zprávu řetězce ve třídě ref nebo struktuře:

```cpp
public ref class Tree sealed
{
public:
    Tree(){}
    virtual Platform::String^ ToString() override
    {
      return "I’m a Tree";
    };
};
```

## <a name="see-also"></a>Viz také

[Obor názvů platformy](platform-namespace-c-cx.md)<br/>
[Platform::Type – třída](platform-type-class.md)<br/>
[Systém typů](type-system-c-cx.md)
