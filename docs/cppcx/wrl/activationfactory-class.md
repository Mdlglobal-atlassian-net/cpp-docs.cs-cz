---
title: ActivationFactory – třída
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory
- module/Microsoft::WRL::ActivationFactory::ActivationFactory
- module/Microsoft::WRL::ActivationFactory::AddRef
- module/Microsoft::WRL::ActivationFactory::GetIids
- module/Microsoft::WRL::ActivationFactory::GetRuntimeClassName
- module/Microsoft::WRL::ActivationFactory::GetTrustLevel
- module/Microsoft::WRL::ActivationFactory::QueryInterface
- module/Microsoft::WRL::ActivationFactory::Release
helpviewer_keywords:
- Microsoft::WRL::ActivationFactory class
- Microsoft::WRL::ActivationFactory::ActivationFactory, constructor
- Microsoft::WRL::ActivationFactory::AddRef method
- Microsoft::WRL::ActivationFactory::GetIids method
- Microsoft::WRL::ActivationFactory::GetRuntimeClassName method
- Microsoft::WRL::ActivationFactory::GetTrustLevel method
- Microsoft::WRL::ActivationFactory::QueryInterface method
- Microsoft::WRL::ActivationFactory::Release method
ms.assetid: 5faddf1f-43b6-4f8a-97de-8c9d3ae1e1ff
ms.openlocfilehash: 0655caeb3f49a18e9c57c78f0008901aaaedda4a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368709"
---
# <a name="activationfactory-class"></a>ActivationFactory – třída

Umožňuje aktivaci jedné nebo více tříd prostředím Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
template <
    typename I0 = Details::Nil,
    typename I1 = Details::Nil,
    typename I2 = Details::Nil
>
class ActivationFactory :
    public Details::RuntimeClass<
        typename Details::InterfaceListHelper<
            IActivationFactory,
            I0,
            I1,
            I2,
            Details::Nil
        >::TypeT,
        RuntimeClassFlags<WinRt | InhibitWeakReference>,
        false
    >;
```

### <a name="parameters"></a>Parametry

*I0*<br/>
Nultý rozhraní.

*I1*<br/>
První rozhraní.

*I2*<br/>
Druhé rozhraní.

## <a name="remarks"></a>Poznámky

`ActivationFactory`poskytuje metody registrace a základní `IActivationFactory` funkce pro rozhraní. `ActivationFactory`také umožňuje poskytnout vlastní implementaci z výroby.

Následující fragment kódu symbolicky ilustruje, jak používat ActivationFactory.

[!code-cpp[wrl-microsoft__wrl__activationfactory#1](../codesnippet/CPP/activationfactory-class_1.cpp)]

Následující fragment kódu ukazuje, jak použít [implements](implements-structure.md) strukturu určit více než tři ID rozhraní.

`struct MyFactory : ActivationFactory<Implements<I1, I2, I3>, I4, I5>;`

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Name (Název)                                                       | Popis
---------------------------------------------------------- | ------------------------------------------
[ActivationFactory::ActivationFactory](#activationfactory) | Inicializuje `ActivationFactory` třídu.

### <a name="public-methods"></a>Veřejné metody

Name (Název)                                                           | Popis
-------------------------------------------------------------- | --------------------------------------------------------------------------------------------
[ActivationFactory::Addref](#addref)                           | Zintáží počet odkazů `ActivationFactory` aktuálního objektu.
[ActivationFactory::GetIIds](#getiids)                         | Načte pole implementovaných ID rozhraní.
[ActivationFactory::GetRuntimeClassName](#getruntimeclassname) | Získá název třídy runtime objektu, který aktuální `ActivationFactory` instance.
[ActivationFactory::GetTrustLevel](#gettrustlevel)             | Získá úroveň důvěryhodnosti objektu, `ActivationFactory` který aktuální instance.
[ActivationFactory::QueryInterface](#queryinterface)           | Načte ukazatel na zadané rozhraní.
[ActivationFactory::Vydání](#release)                         | Sníží počet odkazů aktuálního `ActivationFactory` objektu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`I0`

`ChainInterfaces`

`I0`

`RuntimeClassBase`

`ImplementsHelper`

`DontUseNewUseMake`

`RuntimeClassFlags`

`RuntimeClassBaseT`

`RuntimeClass`

`ActivationFactory`

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Obor názvů:** Microsoft::WRL

## <a name="activationfactoryactivationfactory"></a><a name="activationfactory"></a>ActivationFactory::ActivationFactory

Inicializuje `ActivationFactory` třídu.

```cpp
ActivationFactory();
```

## <a name="activationfactoryaddref"></a><a name="addref"></a>ActivationFactory::Addref

Zintáží počet odkazů `ActivationFactory` aktuálního objektu.

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak HRESULT, který popisuje selhání.

## <a name="activationfactorygetiids"></a><a name="getiids"></a>ActivationFactory::GetIIds

Načte pole implementovaných ID rozhraní.

```cpp
STDMETHOD(
   GetIids
)(_Out_ ULONG *iidCount, _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>Parametry

*iidCount*<br/>
Po dokončení této operace počet Interace ID v poli *IIDs.*

*IIDs*<br/>
Po dokončení této operace pole implementovaných ID rozhraní.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak HRESULT, který popisuje selhání. E_OUTOFMEMORY je možné selhání HRESULT.

## <a name="activationfactorygetruntimeclassname"></a><a name="getruntimeclassname"></a>ActivationFactory::GetRuntimeClassName

Získá název třídy runtime objektu, který aktuální `ActivationFactory` instance.

```cpp
STDMETHOD(
   GetRuntimeClassName
)(_Out_ HSTRING* runtimeName);
```

### <a name="parameters"></a>Parametry

*runtimeName*<br/>
Po dokončení této operace popisovač řetězce, který obsahuje název třídy runtime objektu, který aktuální `ActivationFactory` instance.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak HRESULT, který popisuje selhání.

## <a name="activationfactorygettrustlevel"></a><a name="gettrustlevel"></a>ActivationFactory::GetTrustLevel

Získá úroveň důvěryhodnosti objektu, `ActivationFactory` který aktuální instance.

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

### <a name="parameters"></a>Parametry

*důvěraLvl*<br/>
Po dokončení této operace úroveň důvěryhodnosti runtime `ActivationFactory` třídy, která instancí.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě je vyzařována chyba `FullTrust`kontrolního výrazu a *trustLvl* je nastavena na .

## <a name="activationfactoryqueryinterface"></a><a name="queryinterface"></a>ActivationFactory::QueryInterface

Načte ukazatel na zadané rozhraní.

```cpp
STDMETHOD(
   QueryInterface
)(REFIID riid, _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>Parametry

*riid řekl:*<br/>
ID rozhraní.

*ppvObjekt*<br/>
Po dokončení této operace ukazatel na rozhraní určené parametrem *riid*.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak HRESULT, který popisuje selhání.

## <a name="activationfactoryrelease"></a><a name="release"></a>ActivationFactory::Vydání

Sníží počet odkazů aktuálního `ActivationFactory` objektu.

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak HRESULT, který popisuje selhání.
