---
title: IDBInitializeImpl::m_dwStatus | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::IDBInitializeImpl::m_dwStatus
- IDBInitializeImpl.m_dwStatus
- ATL.IDBInitializeImpl.m_dwStatus
- IDBInitializeImpl::m_dwStatus
- IDBInitializeImpl<T>::m_dwStatus
- ATL.IDBInitializeImpl<T>.m_dwStatus
- ATL::IDBInitializeImpl<T>::m_dwStatus
- m_dwStatus
dev_langs: C++
helpviewer_keywords: m_dwStatus
ms.assetid: 7621ccff-ca60-4b75-9c6a-c104bd0e2038
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c54cc1d91916e23e432faf8e407400b0985e3285
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="idbinitializeimplmdwstatus"></a>IDBInitializeImpl::m_dwStatus
Zdroje dat příznaky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DWORD m_dwStatus;  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Tyto příznaky zadejte nebo označují stav různých atributy pro objekt zdroje dat. Obsahuje jeden nebo více z následujících `enum` hodnoty:  
  
```  
enum DATASOURCE_FLAGS {  
    DSF_MASK_INIT     = 0xFFFFF00F,  
    DSF_PERSIST_DIRTY = 0x00000001,  
    DSF_INITIALIZED   = 0x00000010,  
};  
```  
  
|||  
|-|-|  
|**DSF_MASK_INIT**|Maska povolit obnovení neinicializovaném stavu.|  
|**DSF_PERSIST_DIRTY**|Nastavte, pokud objekt zdroje dat vyžaduje trvalost (Pokud došlo ke změnám).|  
|**DSF_INITIALIZED**|Nastavit, pokud zdroj dat byl inicializován.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IDBInitializeImpl – třída](../../data/oledb/idbinitializeimpl-class.md)   
 [IDBInitializeImpl::IDBInitializeImpl](../../data/oledb/idbinitializeimpl-idbinitializeimpl.md)   
 [IDBInitializeImpl::Uninitialize](../../data/oledb/idbinitializeimpl-uninitialize.md)