---
title: SimpleClassFactory – třída
ms.date: 09/7/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleClassFactory
- module/Microsoft::WRL::SimpleClassFactory::CreateInstance
helpviewer_keywords:
- Microsoft::WRL::SimpleClassFactory class
- Microsoft::WRL::SimpleClassFactory::CreateInstance method
ms.assetid: 6edda1b2-4e44-4e14-9364-72f519249962
ms.openlocfilehash: 924b9d2c30f11e6f0444d9c647807f1c86dcc411
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373552"
---
# <a name="simpleclassfactory-class"></a>SimpleClassFactory – třída

Poskytuje základní mechanismus pro vytvoření základní třídy.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename Base>
class SimpleClassFactory : public ClassFactory<>;
```

### <a name="parameters"></a>Parametry

*Základní*<br/>
Základní třída.

## <a name="remarks"></a>Poznámky

Základní třída musí poskytnout výchozí konstruktor.

Následující příklad kódu ukazuje, `SimpleClassFactory` jak používat s macro [ActivatableClassWithFactoryEx.](activatableclass-macros.md)

`ActivatableClassWithFactoryEx(MyClass, SimpleClassFactory, MyServerName);`

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[SimpleClassFactory::CreateInstance – metoda](#createinstance)|Vytvoří instanci zadaného rozhraní.|

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

`ClassFactory`

`SimpleClassFactory`

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Obor názvů:** Microsoft::WRL

## <a name="simpleclassfactorycreateinstance-method"></a><a name="createinstance"></a>SimpleClassFactory::Metoda CreateInstance

Vytvoří instanci zadaného rozhraní.

```cpp
STDMETHOD( CreateInstance )(
   _Inout_opt_ IUnknown* pUnkOuter,
   REFIID riid,
   _Deref_out_ void** ppvObject
);
```

#### <a name="parameters"></a>Parametry

*pUnkOuter*<br/>
Musí `nullptr`být ; v opačném případě je CLASS_E_NOAGGREGATION vrácená hodnota.

SimpleClassFactory nepodporuje agregaci. Pokud agregace byly podporovány a objekt, který je vytvořen byl součástí agregace, *pUnkOuter* by ukazatel na řídící `IUnknown` rozhraní agregace.

*riid řekl:*<br/>
ID rozhraní objektu, který chcete vytvořit.

*ppvObjekt*<br/>
Po dokončení této operace ukazatel na instanci objektu určené *riid* parametr.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak HRESULT, který označuje chybu.

### <a name="remarks"></a>Poznámky

Pokud `__WRL_STRICT__` je definována, chyba assert je vyzařována, pokud základní třída zadaná v parametru šablony třídy není odvozena z [RuntimeClass](runtimeclass-class.md), nebo není nakonfigurována s hodnotou výčtu ClassicCom nebo WinRtClassicComMix [RuntimeClassType.](runtimeclasstype-enumeration.md)
