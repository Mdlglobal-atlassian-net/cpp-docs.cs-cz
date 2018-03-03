---
title: "MixIn – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::MixIn
dev_langs:
- C++
helpviewer_keywords:
- MixIn structure
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 883e952dde579cce3f5a65ba4a453f98ddbb4740
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="mixin-structure"></a>MixIn – struktura
Zajišťuje třídu runtime, pochází z prostředí Windows Runtime rozhraní, pokud existuje a pak classic COM – rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<  
   typename Derived,  
   typename MixInType,  
   bool hasImplements = __is_base_of(Details::ImplementsBase,  
   MixInType)  
>  
struct MixIn;  
```  
  
#### <a name="parameters"></a>Parametry  
 `Derived`  
 Typ odvozený od [implementuje](../windows/implements-structure.md) struktura.  
  
 `MixInType`  
 Základní typ.  
  
 `hasImplements`  
 `true`Pokud `MixInType` je odvozen od aktuální implementace základní typ; `false` jinak.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je třída odvozená z prostředí Windows Runtime a rozhraní třídy COM, seznamu deklarace tříd musí nejprve seznam všech rozhraní prostředí Windows Runtime a pak všechny classic COM rozhraní. MixIn zajistí, že rozhraní jsou zadané ve správném pořadí.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `MixIn`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)