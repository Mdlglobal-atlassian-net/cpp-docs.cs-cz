---
title: ClassFactory – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory
dev_langs:
- C++
helpviewer_keywords:
- ClassFactory class
ms.assetid: f13e6bce-722b-4f18-b7cf-3ffa6345c1db
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 97c07b5cf97578c49da9d4a72b5a232b559ec0ab
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463863"
---
# <a name="classfactory-class"></a>ClassFactory – třída
Implementuje základní funkce `IClassFactory` rozhraní.  
  
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
 *I0*  
 ID nultého rozhraní.  
  
 *I1*  
 První rozhraní.  
  
 *I2*  
 Druhé síťové rozhraní.  
  
## <a name="remarks"></a>Poznámky  
 Využívat `ClassFactory` poskytují implementace uživatelem definovaný objekt pro vytváření.  
  
 Následující programovací model popisuje způsob použití [implementuje](../windows/implements-structure.md) struktura určit více než tři rozhraní na objekt pro vytváření tříd.  
  
 `struct MyFactory : ClassFactory<Implements<I1, I2, I3>, I4, I5>`  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[ClassFactory::ClassFactory – konstruktor](../windows/classfactory-classfactory-constructor.md)||  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[ClassFactory::AddRef – metoda](../windows/classfactory-addref-method.md)|Zvýší počet odkazů pro aktuální objekt ClassFactory –.|  
|[ClassFactory::LockServer – metoda](../windows/classfactory-lockserver-method.md)|Zvýší nebo sníží počet základní objekty, které jsou sledovány v aktuálním objektu ClassFactory –.|  
|[ClassFactory::QueryInterface – metoda](../windows/classfactory-queryinterface-method.md)|Načte ukazatel na rozhraní určené typem parametru.|  
|[ClassFactory::Release – metoda](../windows/classfactory-release-method.md)|Sníží počet referenční pro aktuální objekt ClassFactory –.|  
  
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