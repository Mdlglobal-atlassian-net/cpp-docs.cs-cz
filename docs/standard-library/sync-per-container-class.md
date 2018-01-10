---
title: "sync_per_container – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::sync_per_container
- allocators/stdext::sync_per_container::equals
dev_langs: C++
helpviewer_keywords: sync_per_container class
ms.assetid: 0b4b2904-b668-4d94-a422-d4f919cbffab
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7864b6367d716ff7504982c4a8cbbed55f7784c0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="syncpercontainer-class"></a>sync_per_container – třída
Popisuje [filtr synchronizace](../standard-library/allocators-header.md) poskytující objekt samostatné mezipaměti pro každý objekt přidělení.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Cache>  
class sync_per_container
 : public Cache
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Cache`|Typ mezipaměti přidružené k filtru synchronizace. To může být [cache_chunklist –](../standard-library/cache-chunklist-class.md), [cache_freelist –](../standard-library/cache-freelist-class.md), nebo [cache_suballoc –](../standard-library/cache-suballoc-class.md).|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[equals](#equals)|Porovná dva mezipamětí rovnosti.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<alokátorů >  
  
 **Namespace:** stdext –  
  
##  <a name="equals"></a>sync_per_container::Equals  
 Porovná dva mezipamětí rovnosti.  
  
```
bool equals(const sync_per_container<Cache>& Other) const;
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Cache`|Objekt mezipaměti filtru synchronizace.|  
|`Other`|Objekt mezipaměti pro porovnání rovnosti.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Členská funkce vždy vrátí hodnotu `false`.  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [\<alokátorů >](../standard-library/allocators-header.md)



