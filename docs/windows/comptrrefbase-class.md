---
title: Comptrrefbase – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRefBase
dev_langs:
- C++
helpviewer_keywords:
- ComPtrRefBase class
ms.assetid: 6d344c1a-cc13-4a3f-8a0d-f167ccb9348f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0342500fc41c650967e17919ebdc9605d4261cb5
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464240"
---
# <a name="comptrrefbase-class"></a>ComPtrRefBase – třída
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   typename T  
>  
class ComPtrRefBase;  
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 A [ComPtr\<T >](../windows/comptr-class.md) typ nebo z ní odvozené, nikoli pouze rozhraní, které jsou reprezentována **ComPtr**.  
  
## <a name="remarks"></a>Poznámky  
 Představuje základní třídu pro [comptrref –](../windows/comptrref-class.md) třídy.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`InterfaceType`|Synonymum pro typ parametru šablony *T*.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[ComPtrRefBase::operator IInspectable** – operátor](../windows/comptrrefbase-operator-iinspectable-star-star-operator.md)|Přetypování aktuální [ptr_ –](../windows/comptrrefbase-ptr-data-member.md) na ukazatel na ukazatel – datový člen rozhraní IInspectable.|  
|[ComPtrRefBase::operator IUnknown** – operátor](../windows/comptrrefbase-operator-iunknown-star-star-operator.md)|Přetypování aktuální [ptr_ –](../windows/comptrrefbase-ptr-data-member.md) na ukazatel na ukazatel – datový člen rozhraní IUnknown.|  
  
### <a name="protected-data-members"></a>Chránění členové dat  
  
|Název|Popis|  
|----------|-----------------|  
|[ComPtrRefBase::ptr_ – datový člen](../windows/comptrrefbase-ptr-data-member.md)|Ukazatel na typ zadaný v parametru aktuální šablony.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `ComPtrRefBase`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)