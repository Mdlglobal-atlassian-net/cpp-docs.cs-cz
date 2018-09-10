---
title: Platform::Object – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Object::Object
- VCCORLIB/Platform::Object::Equals
- VCCORLIB/Platform::Object::GetHashCode
- VCCORLIB/Platform::Object::ReferenceEquals
- VCCORLIB/Platform::ToString
- VCCORLIB/Platform::GetType
dev_langs:
- C++
helpviewer_keywords:
- Object class
ms.assetid: 709e84a8-0bff-471b-bc14-63e424080b5a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 82f9cf473a1b38e3a77b43bc5fde30057c7b1a8a
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44106537"
---
# <a name="platformobject-class"></a>Platform::Object – třída

Poskytuje běžné chování pro referenční třídy a struktury ref v aplikacích pro Windows Runtime. Všechny třídy ref class a instance struktury ref jsou implicitně převést na Platform::Object ^ a jeho virtuální metodu ToString lze přepsat.

## <a name="syntax"></a>Syntaxe

```cpp
public ref class Object : Object
```

### <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Object::Object](#ctor)|Inicializuje novou instanci třídy objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Object::Equals](#equals)|Určuje, zda se zadaný objekt rovná aktuálnímu objektu.|
|[Object::GetHashCode](#gethashcode)|Vrátí kód hash této instance.|
|[Object::ReferenceEquals](#referenceequals)|Určuje, zda jsou zadané instance objektu stejné instanci.|
|[ToString](#tostring)|Vrací řetězec, který představuje aktuální objekt. Může být přepsána.|
|[GetType](#gettype)|Získá [Platform::type –](../cppcx/platform-type-class.md) , která popisuje aktuální instance.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Object`

`Object`

### <a name="requirements"></a>Požadavky

**Záhlaví:** vccorlib.h

**Namespace:** platformy

## <a name="equals"></a> Object::Equals – metoda

Určuje, zda se zadaný objekt rovná aktuálnímu objektu.

### <a name="syntax"></a>Syntaxe

```cpp
bool Equals(
    Object^ obj
)
```

### <a name="parameters"></a>Parametry

*obj*<br/>
Objekt k porovnání.

### <a name="return-value"></a>Návratová hodnota

`true` Pokud jsou objekty stejné, jinak `false`.

## <a name="gethashcode"></a>  Object::GetHashCode – metoda

Vrátí `IUnknown`* hodnotu identity pro tuto instanci, pokud je objekt modelu COM, nebo hodnotu Vypočítaný algoritmus hash, pokud není objekt modelu COM.

### <a name="syntax"></a>Syntaxe

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>Návratová hodnota

Číselná hodnota, která jednoznačně identifikuje tento objekt.

### <a name="remarks"></a>Poznámky

Metoda GetHashCode slouží k vytvoření klíče pro objekty v rámci služby maps. Hodnota hash kódy můžete porovnat s použitím [Object::Equals](#equals). Pokud cesta kódu je velmi důležité a `GetHashCode` a `Equals` nejsou dostatečně rychle, můžete rozevírací seznam pro základní vrstvě COM a proveďte nativní `IUnknown` porovnání ukazatelů.

## <a name="gettype"></a>  Object::gettype – metoda

Vrátí [Platform::type –](../cppcx/platform-type-class.md) objekt, který popisuje typ objektu v modulu runtime.

### <a name="syntax"></a>Syntaxe

```cpp
Object::GetType();
```

### <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota

A [Platform::type –](../cppcx/platform-type-class.md) objekt, který popisuje modulu runtime typu objektu.

### <a name="remarks"></a>Poznámky

Statické [Type::GetTypeCode](../cppcx/platform-type-class.md#gettypecode) můžete použít k získání [Platform::TypeCode – výčet](../cppcx/platform-typecode-enumeration.md) hodnotu, která představuje aktuálního typu. To oceníte především pro předdefinované typy. Typ kódu pro všechny třídy ref class kromě [Platform::String](../cppcx/platform-string-class.md) je objekt (1).

[Windows::UI::Xaml::Interop::TypeName](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx) třída se používá v rozhraní Windows API způsobem nezávislým na jazyku předávání informací o typu mezi součásti Windows a aplikace. T[Platform::type – třída](../cppcx/platform-type-class.md) má operátory pro převod mezi `Type` a `TypeName`.

Použití [typeid](../windows/typeid-cpp-component-extensions.md) operátor se vraťte `Platform::Type` objekt pro název třídy, například při navigaci mezi stránkami XAML:

```
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

## <a name="see-also"></a>Viz také

[Platform::Type – třída](../cppcx/platform-type-class.md)<br/>
[Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)<br/>
[Typ System] (.. /cppcx/Type-System-c-CX.MD

## <a name="ctor"></a>  Object::Object konstruktor

Inicializuje novou instanci třídy objektu.

### <a name="syntax"></a>Syntaxe

```cpp
public:Object();
```

## <a name="referenceequals"></a>  Object::ReferenceEquals – metoda

Určuje, zda jsou zadané instance objektu stejné instanci.

### <a name="syntax"></a>Syntaxe

```cpp
public:static bool ReferenceEquals(  Object^ obj1,   Object^ obj2);
```

### <a name="parameters"></a>Parametry

*Obj1*<br/>
První objekt k porovnání.

*obj2*<br/>
Druhý objekt k porovnání.

### <a name="return-value"></a>Návratová hodnota

`true` Pokud jsou oba objekty stejné. v opačném případě `false`.

## <a name="tostring"></a>  Metoda Object::ToString (C + +/ CX)

Vrací řetězec, který představuje aktuální objekt.

### <a name="syntax"></a>Syntaxe

```cpp
public:
virtual String^ ToString();
```

### <a name="return-value"></a>Návratová hodnota

Řetězec, který představuje aktuální objekt. Můžete přepsat tuto metodu za účelem zadejte vlastní řetězec zprávu v referenční třídy nebo struktury:

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

[Platforma Namespace](platform-namespace-c-cx.md)