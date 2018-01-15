---
title: "ClassFactory – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::ClassFactory
dev_langs: C++
helpviewer_keywords: ClassFactory class
ms.assetid: f13e6bce-722b-4f18-b7cf-3ffa6345c1db
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8c37c016809d31fcb072f23768e9f54313331016
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="classfactory-class"></a>ClassFactory – třída
Implementuje základních funkcí rozhraní IClassFactory.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   typename I0 = Details::Nil,  
   typename I1 = Details::Nil,  
   typename I2 = Details::Nil  
>  
class ClassFactory : public Details::RuntimeClass<  
   typename Details::InterfaceListHelper<IClassFactory,   
   I0,   
   I1,   
   I2,   
   Details::Nil>::TypeT,   
   RuntimeClassFlags<ClassicCom | InhibitWeakReference>,   
      false>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `I0`  
 Rozhraní zeroth.  
  
 `I1`  
 První rozhraní.  
  
 `I2`  
 Druhý rozhraní.  
  
## <a name="remarks"></a>Poznámky  
 Využívat `ClassFactory` k zajištění implementace vlastní objekt pro vytváření.  
  
 Následující programovací vzor ukazuje, jak používat [implementuje](../windows/implements-structure.md) struktura zadání víc než třemi rozhraní v továrně, třída.  
  
 `struct MyFactory : ClassFactory<Implements<I1, I2, I3>, I4, I5>`  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[ClassFactory::ClassFactory – konstruktor](../windows/classfactory-classfactory-constructor.md)||  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[ClassFactory::AddRef – metoda](../windows/classfactory-addref-method.md)|Zvýší počet odkazů pro aktuální objekt ClassFactory.|  
|[ClassFactory::LockServer – metoda](../windows/classfactory-lockserver-method.md)|Zvýší nebo sníží počet základní objekty, které sleduje aktuální objekt ClassFactory.|  
|[ClassFactory::QueryInterface – metoda](../windows/classfactory-queryinterface-method.md)|Načte ukazatel na rozhraní určený parametrem.|  
|[ClassFactory::Release – metoda](../windows/classfactory-release-method.md)|Snižuje počet odkaz na aktuální objekt ClassFactory.|  
  
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
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)   
 [RuntimeClassType – výčet](../windows/runtimeclasstype-enumeration.md)