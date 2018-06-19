---
title: Mutex Class1 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex
dev_langs:
- C++
helpviewer_keywords:
- Mutex class
ms.assetid: 682a0963-721c-46a2-8871-000e9997505b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9a9e9674dd8ac5aa7d444a77df66c1aff4a70299
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878408"
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