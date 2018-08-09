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
ms.openlocfilehash: adbc7b6bbeafff277f32170627d6804526900049
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40019014"
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