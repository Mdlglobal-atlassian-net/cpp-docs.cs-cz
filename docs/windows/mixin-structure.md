---
title: MixIn – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::MixIn
dev_langs:
- C++
helpviewer_keywords:
- MixIn structure
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b20dac5f189a51a1610da45e43e03e51ff1c3610
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33876160"
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
 `true` Pokud `MixInType` je odvozen od aktuální implementace základní typ; `false` jinak.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je třída odvozená z prostředí Windows Runtime a rozhraní třídy COM, seznamu deklarace tříd musí nejprve seznam všech rozhraní prostředí Windows Runtime a pak všechny classic COM rozhraní. MixIn zajistí, že rozhraní jsou zadané ve správném pořadí.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `MixIn`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)