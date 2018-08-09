---
title: Simpleclassfactory – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleClassFactory
dev_langs:
- C++
helpviewer_keywords:
- SimpleClassFactory class
ms.assetid: 6edda1b2-4e44-4e14-9364-72f519249962
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c490e21717e44ec3e772c01f84a0f5adb08471fd
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40012492"
---
# <a name="simpleclassfactory-class"></a>SimpleClassFactory – třída
Poskytuje základní mechanismus pro vytvoření základní třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Base>  
class SimpleClassFactory : public ClassFactory<>;  
```  
  
### <a name="parameters"></a>Parametry  
 *základ*  
 Základní třída.  
  
## <a name="remarks"></a>Poznámky  
 Základní třída musí poskytovat konstruktor default.  
  
 Následující příklad kódu ukazuje, jak používat **simpleclassfactory –** s [ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md) – makro.  
  
 `ActivatableClassWithFactoryEx(MyClass, SimpleClassFactory, MyServerName);`  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[SimpleClassFactory::CreateInstance – metoda](../windows/simpleclassfactory-createinstance-method.md)|Vytvoří instanci zadaného rozhraní.|  
  
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
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)