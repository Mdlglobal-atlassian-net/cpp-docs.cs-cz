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
ms.openlocfilehash: a9483a4acec14fbd7e520e047b259f1e5cb7f9c4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50515385"
---
# <a name="simpleactivationfactory-class"></a>SimpleActivationFactory – třída

Poskytuje základní mechanismus pro vytvoření prostředí Windows Runtime nebo klasického modelu COM základní třídy.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename Base>
class SimpleActivationFactory : public ActivationFactory<>;
```

### <a name="parameters"></a>Parametry

*základ*<br/>
Základní třída.

## <a name="remarks"></a>Poznámky

Základní třída musí poskytovat konstruktor default.

Následující příklad kódu ukazuje, jak používat simpleactivationfactory – s [ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md) – makro.

`ActivatableClassWithFactoryEx(MyClass, SimpleActivationFactory, MyServerName);`

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[SimpleActivationFactory::ActivateInstance – metoda](#activateinstance)|Vytvoří instanci zadaného rozhraní.|
|[SimpleActivationFactory::GetRuntimeClassName – metoda](#getruntimeclassname)|Získá název třídy runtime instance třídy určené *Base* parametr šablony třídy.|
|[SimpleActivationFactory::GetTrustLevel – metoda](#gettrustlevel)|Získá instanci třídy určené úroveň důvěryhodnosti *Base* parametr šablony třídy.|

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

**Namespace:** Microsoft::WRL

## <a name="activateinstance"></a>Simpleactivationfactory::activateinstance – metoda

Vytvoří instanci zadaného rozhraní.

```cpp
STDMETHOD( ActivateInstance )(
    _Deref_out_ IInspectable **ppvObject
);
```

#### <a name="parameters"></a>Parametry

*ppvObject*<br/>
Když tato operace dokončí, ukazatel na instanci objektu určeného parametrem `Base` parametr šablony třídy.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.

### <a name="remarks"></a>Poznámky

Pokud `__WRL_STRICT__` je definován, chybu kontrolní výraz je vygenerován, pokud zadaná v parametru šablony třídy základní třída není odvozen od [RuntimeClass](../windows/runtimeclass-class.md), nebo nemá nakonfigurovanou WinRt nebo WinRtClassicComMix [ Runtimeclasstype –](../windows/runtimeclasstype-enumeration.md) hodnota výčtu.

## <a name="getruntimeclassname"></a>Simpleactivationfactory::getruntimeclassname – metoda

Získá název třídy runtime instance třídy určené `Base` parametr šablony třídy.

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

#### <a name="parameters"></a>Parametry

*runtimeName*<br/>
Po dokončení této operace, název třídy runtime.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.

### <a name="remarks"></a>Poznámky

Pokud `__WRL_STRICT__` je definován, chybu kontrolní výraz je vygenerován, pokud třída určená `Base` parametr šablony třídy není odvozen od [RuntimeClass](../windows/runtimeclass-class.md), nebo nemá nakonfigurovanou WinRt nebo WinRtClassicComMix [Runtimeclasstype –](../windows/runtimeclasstype-enumeration.md) hodnota výčtu.

## <a name="gettrustlevel"></a>Simpleactivationfactory::gettrustlevel – metoda

Získá instanci třídy určené úroveň důvěryhodnosti `Base` parametr šablony třídy.

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

#### <a name="parameters"></a>Parametry

*trustLvl*<br/>
Když tato operace dokončí, úroveň důvěryhodnosti objektu aktuální třídy.

### <a name="return-value"></a>Návratová hodnota

Vždy S_OK.
