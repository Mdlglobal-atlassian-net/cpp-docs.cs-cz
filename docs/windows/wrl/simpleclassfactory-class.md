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
ms.openlocfilehash: 9a4c169944d56b693efa681bf7089636477012ea
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334689"
---
# <a name="simpleclassfactory-class"></a>SimpleClassFactory – třída

Poskytuje základní mechanismus pro vytvoření základní třídy.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename Base>
class SimpleClassFactory : public ClassFactory<>;
```

### <a name="parameters"></a>Parametry

*základ*<br/>
Základní třída.

## <a name="remarks"></a>Poznámky

Základní třída musí poskytovat konstruktor default.

Následující příklad kódu ukazuje, jak používat `SimpleClassFactory` s [ActivatableClassWithFactoryEx](activatableclass-macros.md) – makro.

`ActivatableClassWithFactoryEx(MyClass, SimpleClassFactory, MyServerName);`

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
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

**Namespace:** Microsoft::WRL

## <a name="createinstance"></a>Simpleclassfactory::CreateInstance – metoda

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
Musí být `nullptr`; v opačném případě je vrácená hodnota CLASS_E_NOAGGREGATION.

Simpleclassfactory – nepodporuje agregace. Pokud byly podporovány agregace a součást agregace, byl tento objekt vytváří *pUnkOuter* bude ukazatel řízení `IUnknown` rozhraní agregace.

*riid*<br/>
ID objektu pro vytváření rozhraní.

*ppvObject*<br/>
Když tato operace dokončí, ukazatel na instanci objektu určeného parametrem *riid* parametru.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.

### <a name="remarks"></a>Poznámky

Pokud `__WRL_STRICT__` je definován, chybu kontrolní výraz je vygenerován, pokud zadaná v parametru šablony třídy základní třída není odvozen od [RuntimeClass](runtimeclass-class.md), nebo nemá nakonfigurovanou ClassicCom nebo WinRtClassicComMix [ Runtimeclasstype –](runtimeclasstype-enumeration.md) hodnota výčtu.
