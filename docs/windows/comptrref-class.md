---
title: "ComPtrRef – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::Details::ComPtrRef
dev_langs: C++
helpviewer_keywords: ComPtrRef class
ms.assetid: d6bdfd20-e977-45b4-9ac1-1b8efbdb77de
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9b1bbe134f15fdba6863f1725cbcc7effcb6d94f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="comptrref-class"></a>ComPtrRef – třída
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   typename T  
>  
class ComPtrRef : public ComPtrRefBase<T>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 A [ComPtr\<T >](../windows/comptr-class.md) typ nebo typ odvozený z něj, nikoli pouze rozhraní reprezentována ComPtr.  
  
## <a name="remarks"></a>Poznámky  
 Představuje odkaz na objekt typu ComPtr\<T >.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[ComPtrRef::ComPtrRef – konstruktor](../windows/comptrref-comptrref-constructor.md)|Inicializuje novou instanci třídy ComPtrRef ze zadaného ukazatele k jinému objektu ComPtrRef.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[ComPtrRef::GetAddressOf – metoda](../windows/comptrref-getaddressof-method.md)|Načte adresu ukazatele rozhraní představuje aktuální objekt ComPtrRef.|  
|[ComPtrRef::ReleaseAndGetAddressOf – metoda](../windows/comptrref-releaseandgetaddressof-method.md)|Odstraní aktuální objekt ComPtrRef a vrací ukazatel na ukazatel na rozhraní, která je reprezentována ComPtrRef objektu.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[ComPtrRef::operator InterfaceType** – operátor](../windows/comptrref-operator-interfacetype-star-star-operator.md)|Odstraní aktuální objekt ComPtrRef a vrací ukazatel na ukazatel na rozhraní, která je reprezentována ComPtrRef objektu.|  
|[ComPtrRef::operator T* – operátor](../windows/comptrref-operator-t-star-operator.md)|Vrátí hodnotu [ptr_ –](../windows/comptrrefbase-ptr-data-member.md) aktuálního objektu ComPtrRef – datový člen.|  
|[ComPtrRef::operator void** – operátor](../windows/comptrref-operator-void-star-star-operator.md)|Odstraní aktuální objekt ComPtrRef, vrhá má ukazatel na rozhraní, které byl objekt ComPtrRef reprezentována jako ukazatel na ukazatel – to `void`a potom se vrátí ukazatele přetypování.|  
|[ComPtrRef::operator* – operátor](../windows/comptrref-operator-star-operator.md)|Načte má ukazatel na rozhraní představuje aktuální objekt ComPtrRef.|  
|[ComPtrRef::operator== – operátor](../windows/comptrref-operator-equality-operator.md)|Určuje, zda dva objekty ComPtrRef jsou stejné.|  
|[ComPtrRef::operator!= – operátor](../windows/comptrref-operator-inequality-operator.md)|Určuje, zda dva objekty ComPtrRef nejsou stejné.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `ComPtrRefBase`  
  
 `ComPtrRef`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)