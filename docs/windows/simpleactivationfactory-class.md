---
title: SimpleActivationFactory – třída | Microsoft Docs
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
ms.openlocfilehash: 2d10544a08fa6faebb1434cd00ca80ac30d4570a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="simpleactivationfactory-class"></a>SimpleActivationFactory – třída
Poskytuje základní mechanismus pro vytvoření klasického základní třídy COM nebo prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Base>  
class SimpleActivationFactory : public ActivationFactory<>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `Base`  
 Základní třída.  
  
## <a name="remarks"></a>Poznámky  
 Základní třída musí obsahovat výchozí konstruktor.  
  
 Následující příklad kódu ukazuje, jak používat SimpleActivationFactory s [ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md) makro.  
  
 `ActivatableClassWithFactoryEx(MyClass, SimpleActivationFactory, MyServerName);`  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[SimpleActivationFactory::ActivateInstance – metoda](../windows/simpleactivationfactory-activateinstance-method.md)|Vytvoří instanci zadaného rozhraní.|  
|[SimpleActivationFactory::GetRuntimeClassName – metoda](../windows/simpleactivationfactory-getruntimeclassname-method.md)|Získá název třídy runtime instance třídy určeného `Base` – třída parametru šablony.|  
|[SimpleActivationFactory::GetTrustLevel – metoda](../windows/simpleactivationfactory-gettrustlevel-method.md)|Získá úroveň důvěryhodnosti instance třídy určeného `Base` – třída parametru šablony.|  
  
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