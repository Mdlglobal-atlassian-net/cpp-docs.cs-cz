---
title: "ComPtrRefBase – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::Details::ComPtrRefBase
dev_langs: C++
helpviewer_keywords: ComPtrRefBase class
ms.assetid: 6d344c1a-cc13-4a3f-8a0d-f167ccb9348f
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 071598c83086afe12e1d19ef541dbfb3d0dbc55a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="comptrrefbase-class"></a>ComPtrRefBase – třída
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   typename T  
>  
class ComPtrRefBase;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 A [ComPtr\<T >](../windows/comptr-class.md) typ nebo typ odvozený z něj, nikoli pouze rozhraní reprezentována ComPtr.  
  
## <a name="remarks"></a>Poznámky  
 Představuje základní třídu pro [ComPtrRef](../windows/comptrref-class.md) třídy.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`InterfaceType`|Synonymum pro typ parametru šablony `T`.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[ComPtrRefBase::operator IInspectable** – operátor](../windows/comptrrefbase-operator-iinspectable-star-star-operator.md)|Vrhá aktuální [ptr_ –](../windows/comptrrefbase-ptr-data-member.md) data člena ukazatel k ukazatele k rozhraní IInspectable.|  
|[ComPtrRefBase::operator IUnknown** – operátor](../windows/comptrrefbase-operator-iunknown-star-star-operator.md)|Vrhá aktuální [ptr_ –](../windows/comptrrefbase-ptr-data-member.md) data člena ukazatel k ukazatele k rozhraní IUnknown.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[ComPtrRefBase::ptr_ – datový člen](../windows/comptrrefbase-ptr-data-member.md)|Ukazatel na typ určený parametrem aktuální šablony.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `ComPtrRefBase`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)