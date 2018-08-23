---
title: Simpleactivationfactory – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleActivationFactory
dev_langs:
- C++
helpviewer_keywords:
- SimpleActivationFactory class
ms.assetid: aff768e0-0038-4fd7-95d2-ad7d308da41c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0820012c8c22de1287fcb09037212b870a4ff7bf
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594795"
---
# <a name="simpleactivationfactory-class"></a>SimpleActivationFactory – třída

Poskytuje základní mechanismus pro vytvoření prostředí Windows Runtime nebo klasického modelu COM základní třídy.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename Base>
class SimpleActivationFactory : public ActivationFactory<>;
```

### <a name="parameters"></a>Parametry

*základ*  
Základní třída.

## <a name="remarks"></a>Poznámky

Základní třída musí poskytovat konstruktor default.

Následující příklad kódu ukazuje, jak používat simpleactivationfactory – s [ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md) – makro.

`ActivatableClassWithFactoryEx(MyClass, SimpleActivationFactory, MyServerName);`

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[SimpleActivationFactory::ActivateInstance – metoda](../windows/simpleactivationfactory-activateinstance-method.md)|Vytvoří instanci zadaného rozhraní.|
|[SimpleActivationFactory::GetRuntimeClassName – metoda](../windows/simpleactivationfactory-getruntimeclassname-method.md)|Získá název třídy runtime instance třídy určené *Base* parametr šablony třídy.|
|[SimpleActivationFactory::GetTrustLevel – metoda](../windows/simpleactivationfactory-gettrustlevel-method.md)|Získá instanci třídy určené úroveň důvěryhodnosti *Base* parametr šablony třídy.|

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

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)