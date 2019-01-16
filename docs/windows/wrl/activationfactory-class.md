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
ms.openlocfilehash: 8e5132f4a8711f6420cd9b52751550a96d10d8fc
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334721"
---
# <a name="activationfactory-class"></a>ActivationFactory – třída

Umožňuje jednu nebo více tříd aktivováno modulu Windows Runtime.

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
ID nultého rozhraní.

*I1*<br/>
První rozhraní.

*I2*<br/>
Druhé síťové rozhraní.

## <a name="remarks"></a>Poznámky

`ActivationFactory` poskytuje metody registrace a základní funkce pro `IActivationFactory` rozhraní. `ActivationFactory` Můžete také poskytnout implementaci vlastní objekt pro vytváření.

Následující fragment kódu symbolicky ukazuje, jak používat activationfactory –.

[!code-cpp[wrl-microsoft__wrl__activationfactory#1](../codesnippet/CPP/activationfactory-class_1.cpp)]

Následující fragment kódu ukazuje způsob použití [implementuje](implements-structure.md) struktury zadat více než tři ID rozhraní.

`struct MyFactory : ActivationFactory<Implements<I1, I2, I3>, I4, I5>;`

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Název                                                       | Popis
---------------------------------------------------------- | ------------------------------------------
[ActivationFactory::ActivationFactory](#activationfactory) | Inicializuje `ActivationFactory` třídy.

### <a name="public-methods"></a>Veřejné metody

Název                                                           | Popis
-------------------------------------------------------------- | --------------------------------------------------------------------------------------------
[Activationfactory::addref –](#addref)                           | Zvýší počet odkazů aktuálního `ActivationFactory` objektu.
[Activationfactory::getiids –](#getiids)                         | Načte pole ID implementovaného rozhraní.
[ActivationFactory::GetRuntimeClassName](#getruntimeclassname) | Získá název třídy runtime objektu, který aktuální `ActivationFactory` vytvoří instanci.
[ActivationFactory::GetTrustLevel](#gettrustlevel)             | Získá úroveň důvěryhodnosti objektu, který aktuální `ActivationFactory` vytvoří instanci.
[ActivationFactory::QueryInterface](#queryinterface)           | Načte ukazatel na rozhraní zadané.
[Activationfactory::Release –](#release)                         | Sníží počet odkaz na aktuální `ActivationFactory` objektu.

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

**Namespace:** Microsoft::WRL

## <a name="activationfactory"></a>ActivationFactory::ActivationFactory

Inicializuje `ActivationFactory` třídy.

```cpp
ActivationFactory();
```

## <a name="addref"></a>Activationfactory::addref –

Zvýší počet odkazů aktuálního `ActivationFactory` objektu.

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT s popisem chyby.

## <a name="getiids"></a>Activationfactory::getiids –

Načte pole ID implementovaného rozhraní.

```cpp
STDMETHOD(
   GetIids
)(_Out_ ULONG *iidCount, _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>Parametry

*iidCount*<br/>
Když tato operace dokončí, počet ID uživatelského rozhraní v *IID* pole.

*iids*<br/>
Po dokončení této operace implementované pole ID rozhraní.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT s popisem chyby. E_OUTOFMEMORY je možné selhání hodnoty HRESULT.

## <a name="getruntimeclassname"></a>Activationfactory::getruntimeclassname –

Získá název třídy runtime objektu, který aktuální `ActivationFactory` vytvoří instanci.

```cpp
STDMETHOD(
   GetRuntimeClassName
)(_Out_ HSTRING* runtimeName);
```

### <a name="parameters"></a>Parametry

*runtimeName*<br/>
Když tato operace dokončí, popisovač pro řetězec, který obsahuje název třídy runtime objektu, který aktuální `ActivationFactory` vytvoří instanci.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT s popisem chyby.

## <a name="gettrustlevel"></a>ActivationFactory::GetTrustLevel

Získá úroveň důvěryhodnosti objektu, který aktuální `ActivationFactory` vytvoří instanci.

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

### <a name="parameters"></a>Parametry

*trustLvl*<br/>
Po dokončení této operace úroveň důvěryhodnosti modulu runtime třídy, která `ActivationFactory` vytvoří instanci.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě je vygenerován chybu kontrolní výraz a *trustLvl* je nastavena na `FullTrust`.

## <a name="queryinterface"></a>ActivationFactory::QueryInterface

Načte ukazatel na rozhraní zadané.

```cpp
STDMETHOD(
   QueryInterface
)(REFIID riid, _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>Parametry

*riid*<br/>
Identifikátor rozhraní.

*ppvObject*<br/>
Po dokončení této operace, ukazatel na rozhraní určené typem parametru *riid*.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT s popisem chyby.

## <a name="release"></a>Activationfactory::Release –

Sníží počet odkaz na aktuální `ActivationFactory` objektu.

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT s popisem chyby.