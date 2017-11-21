---
title: "SimpleActivationFactory – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::SimpleActivationFactory
dev_langs: C++
helpviewer_keywords: SimpleActivationFactory class
ms.assetid: aff768e0-0038-4fd7-95d2-ad7d308da41c
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3c56d03b74080ae65f84ffbad8c4dd2092be1082
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="simpleactivationfactory-class"></a>SimpleActivationFactory – třída
Poskytuje základní mechanismus pro vytvoření klasického základní třídy COM nebo prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<  
   typename Base  
>  
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
|[Simpleactivationfactory::activateinstance – metoda](../windows/simpleactivationfactory-activateinstance-method.md)|Vytvoří instanci zadaného rozhraní.|  
|[Simpleactivationfactory::getruntimeclassname – metoda](../windows/simpleactivationfactory-getruntimeclassname-method.md)|Získá název třídy runtime instance třídy určeného `Base` – třída parametru šablony.|  
|[Simpleactivationfactory::gettrustlevel – metoda](../windows/simpleactivationfactory-gettrustlevel-method.md)|Získá úroveň důvěryhodnosti instance třídy určeného `Base` – třída parametru šablony.|  
  
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
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)