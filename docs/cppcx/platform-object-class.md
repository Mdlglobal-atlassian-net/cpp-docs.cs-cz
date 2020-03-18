---
title: 'Platform:: Object – Třída'
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
ms.openlocfilehash: 77313f8c4dcc87fa9de852afe2d60e614f8fc3a3
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418347"
---
# <a name="platformobject-class"></a>Platform:: Object – Třída

Poskytuje běžné chování pro referenční třídy a struktury ref v aplikacích prostředí Windows Runtime. Všechny instance třídy ref class a ref struct jsou implicitně převoditelné na Platform:: Object ^ a mohou přepsat svou virtuální metodu ToString.

## <a name="syntax"></a>Syntaxe

```cpp
public ref class Object : Object
```

### <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Object:: Object](#ctor)|Inicializuje novou instanci třídy Object.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Object:: Equals](#equals)|Určí, zda se zadaný objekt rovná aktuálnímu objektu.|
|[Objekt:: GetHashCode](#gethashcode)|Vrátí hodnotu hash pro tuto instanci.|
|[Objekt:: ReferenceEquals](#referenceequals)|Určuje, zda jsou zadané instance objektů stejné instance.|
|[Metodu](#tostring)|Vrátí řetězec, který představuje aktuální objekt. Lze přepsat.|
|[GetType](#gettype)|Načte objekt [Platform:: Type](../cppcx/platform-type-class.md) , který popisuje aktuální instanci.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Object`

`Object`

### <a name="requirements"></a>Požadavky

**Záhlaví:** vccorlib. h

**Obor názvů:** Platformy

## <a name="equals"></a>Object:: Equals – metoda

Určí, zda se zadaný objekt rovná aktuálnímu objektu.

### <a name="syntax"></a>Syntaxe

```cpp
bool Equals(
    Object^ obj
)
```

### <a name="parameters"></a>Parametry

*objektu*<br/>
Objekt k porovnání

### <a name="return-value"></a>Návratová hodnota

**true** , pokud jsou objekty stejné, v opačném případě **false**.

## <a name="gethashcode"></a>Object:: GetHashCode – metoda

Vrátí hodnotu `IUnknown`* identity této instance, pokud se jedná o objekt COM, nebo vypočítanou hodnotu hash, pokud se nejedná o objekt COM.

### <a name="syntax"></a>Syntaxe

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>Návratová hodnota

Číselná hodnota, která jednoznačně identifikuje tento objekt.

### <a name="remarks"></a>Poznámky

GetHashCode můžete použít k vytvoření klíčů pro objekty v mapách. Můžete porovnat kódy hash pomocí [objektu:: Equals](#equals). Pokud je cesta k kódu velmi kritická a `GetHashCode` a `Equals` nejsou dostatečně rychlé, můžete je vyřadit do podkladové vrstvy COM a provádět nativní porovnávání `IUnknown` ukazatelů.

## <a name="gettype"></a>Object:: GetType – metoda

Vrátí objekt [Platform:: Type](../cppcx/platform-type-class.md) , který popisuje typ modulu runtime objektu.

### <a name="syntax"></a>Syntaxe

```cpp
Object::GetType();
```

### <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota

Objekt [Platform:: Type](../cppcx/platform-type-class.md) , který popisuje typ modulu runtime objektu.

### <a name="remarks"></a>Poznámky

Statický [Typ:: GetTypeCode](../cppcx/platform-type-class.md#gettypecode) lze použít k získání hodnoty [výčtu Platform:: TypeCode](../cppcx/platform-typecode-enumeration.md) , která představuje aktuální typ. To je hlavně užitečné pro předdefinované typy. Kód typu pro všechny referenční třídy kromě [Platform:: String](../cppcx/platform-string-class.md) je Object (1).

Třída [Windows:: UI:: XAML:: Interop:: typeName](/uwp/api/windows.ui.xaml.interop.typename) se používá v rozhraních API systému Windows jako nezávislý způsob předávání informací o typech mezi součástmi systému Windows a aplikacemi. Třída T[Platform:: Type](../cppcx/platform-type-class.md) obsahuje operátory pro převod mezi `Type` a `TypeName`.

Použijte operátor [typeid](../extensions/typeid-cpp-component-extensions.md) k vrácení objektu `Platform::Type` pro název třídy, například při navigaci mezi stránkami XAML:

```
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

## <a name="ctor"></a>Object:: Object – konstruktor

Inicializuje novou instanci třídy Object.

### <a name="syntax"></a>Syntaxe

```cpp
public:Object();
```

## <a name="referenceequals"></a>Object:: ReferenceEquals – metoda

Určuje, zda jsou zadané instance objektů stejné instance.

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

**true** , pokud jsou tyto dva objekty stejné; v opačném případě **false**.

## <a name="tostring"></a>Object:: ToString – MetodaC++(/CX)

Vrátí řetězec, který představuje aktuální objekt.

### <a name="syntax"></a>Syntaxe

```cpp
public:
virtual String^ ToString();
```

### <a name="return-value"></a>Návratová hodnota

Řetězec, který představuje aktuální objekt. Tuto metodu můžete přepsat tak, aby poskytovala vlastní řetězcovou zprávu ve třídě ref class nebo struct:

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
