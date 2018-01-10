---
title: Mutex Class1 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::Mutex
dev_langs: C++
helpviewer_keywords: Mutex class
ms.assetid: 682a0963-721c-46a2-8871-000e9997505b
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c0e849d1fee7eca67f3b5765d31b54e0660eaa25
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="mutex-class1"></a>Mutex Class1
Představuje objekt synchronizace, kterými se řídí výhradně sdíleného prostředku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class Mutex : public HandleT<HandleTraits::MutexTraits>  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|**SyncLock –**|Synonymum pro třídu, která podporuje synchronní zámky.|  
  
### <a name="public-constructor"></a>Veřejný konstruktor  
  
|Název|Popis|  
|----------|-----------------|  
|[Mutex::Mutex – konstruktor](../windows/mutex-mutex-constructor.md)|Inicializuje novou instanci třídy Mutex.|  
  
### <a name="public-members"></a>Veřejné členy  
  
|Název|Popis|  
|----------|-----------------|  
|[Mutex::Lock – metoda](../windows/mutex-lock-method.md)|Počká, dokud nebude aktuální objekt nebo objekt Mutex přidružené k zadanému popisovači, uvolní mutex nebo zadaný časový limit uplynul.|  
  
### <a name="public-operator"></a>Veřejný operátor  
  
|Název|Popis|  
|----------|-----------------|  
|[Mutex::operator= – operátor](../windows/mutex-operator-assign-operator.md)|Přiřadí (přesune) zadaný objekt Mutex do aktuální objekt Mutex objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `Mutex`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Wrappers – obor názvů](../windows/microsoft-wrl-wrappers-namespace.md)