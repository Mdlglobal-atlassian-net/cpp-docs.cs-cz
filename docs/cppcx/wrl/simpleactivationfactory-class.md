---
title: SimpleActivationFactory – třída
ms.date: 09/07/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleActivationFactory
- module/Microsoft::WRL::SimpleActivationFactory::ActivateInstance
- module/Microsoft::WRL::SimpleActivationFactory::GetRuntimeClassName
- module/Microsoft::WRL::SimpleActivationFactory::GetTrustLevel
helpviewer_keywords:
- Microsoft::WRL::SimpleActivationFactory class
- Microsoft::WRL::SimpleActivationFactory::ActivateInstance method
- Microsoft::WRL::SimpleActivationFactory::GetRuntimeClassName method
- Microsoft::WRL::SimpleActivationFactory::GetTrustLevel method
ms.assetid: aff768e0-0038-4fd7-95d2-ad7d308da41c
ms.openlocfilehash: 39e539c63e91b508f51656114ee8fbd68150991f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370940"
---
# <a name="simpleactivationfactory-class"></a>SimpleActivationFactory – třída

Poskytuje základní mechanismus pro vytvoření prostředí Windows Runtime nebo klasické základní třídy COM.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename Base>
class SimpleActivationFactory : public ActivationFactory<>;
```

### <a name="parameters"></a>Parametry

*Základní*<br/>
Základní třída.

## <a name="remarks"></a>Poznámky

Základní třída musí poskytnout výchozí konstruktor.

Následující příklad kódu ukazuje, jak používat SimpleActivationFactory s macro [ActivatableClassWithFactoryEx.](activatableclass-macros.md)

`ActivatableClassWithFactoryEx(MyClass, SimpleActivationFactory, MyServerName);`

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[SimpleActivationFactory::ActivateInstance – metoda](#activateinstance)|Vytvoří instanci zadaného rozhraní.|
|[SimpleActivationFactory::GetRuntimeClassName – metoda](#getruntimeclassname)|Získá název třídy runtime instance třídy určené parametrem šablony *základní* třídy.|
|[SimpleActivationFactory::GetTrustLevel – metoda](#gettrustlevel)|Získá úroveň důvěryhodnosti instance třídy určené parametrem šablony *základní* třídy.|

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

`SimpleActivationFactory`

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Obor názvů:** Microsoft::WRL

## <a name="simpleactivationfactoryactivateinstance-method"></a><a name="activateinstance"></a>SimpleActivationFactory::Metoda ActivateInstance

Vytvoří instanci zadaného rozhraní.

```cpp
STDMETHOD( ActivateInstance )(
    _Deref_out_ IInspectable **ppvObject
);
```

#### <a name="parameters"></a>Parametry

*ppvObjekt*<br/>
Po dokončení této operace ukazatel na instanci `Base` objektu určené parametrem šablony třídy.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak HRESULT, který označuje chybu.

### <a name="remarks"></a>Poznámky

Pokud `__WRL_STRICT__` je definována, chyba assert je emitován, pokud základní třída zadaná v parametru šablony třídy není odvozena z [RuntimeClass](runtimeclass-class.md), nebo není nakonfigurována s hodnotou výčtu WinRt nebo WinRtClassicComMix [RuntimeClassType.](runtimeclasstype-enumeration.md)

## <a name="simpleactivationfactorygetruntimeclassname-method"></a><a name="getruntimeclassname"></a>SimpleActivationFactory::Metoda GetRuntimeClassName

Získá název třídy runtime instance třídy `Base` určené parametrem šablony třídy.

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

#### <a name="parameters"></a>Parametry

*runtimeName*<br/>
Po dokončení této operace název třídy runtime.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak HRESULT, který označuje chybu.

### <a name="remarks"></a>Poznámky

Pokud `__WRL_STRICT__` je definována, chyba assert je vyzařována, pokud třída určená parametrem šablony `Base` třídy není odvozena z [RuntimeClass](runtimeclass-class.md)nebo není nakonfigurována s hodnotou výčtu WinRt nebo WinRtClassicComMix [RuntimeClassType.](runtimeclasstype-enumeration.md)

## <a name="simpleactivationfactorygettrustlevel-method"></a><a name="gettrustlevel"></a>SimpleActivationFactory::Metoda GetTrustLevel

Získá úroveň důvěryhodnosti instance třídy určené `Base` parametrem šablony třídy.

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

#### <a name="parameters"></a>Parametry

*důvěraLvl*<br/>
Po dokončení této operace úroveň důvěryhodnosti aktuální objekt třídy.

### <a name="return-value"></a>Návratová hodnota

Vždycky S_OK.
