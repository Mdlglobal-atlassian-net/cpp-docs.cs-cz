---
title: IRowsetUpdateImpl::m_mapCachedData | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetUpdateImpl.m_mapCachedData
- IRowsetUpdateImpl::m_mapCachedData
- m_mapCachedData
dev_langs:
- C++
helpviewer_keywords:
- m_mapCachedData
ms.assetid: 65131743-8580-48c8-bb22-68f17c9dfa13
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bd19f8706e50d1eefb26dadfb837d8bd4f13f061
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33103252"
---
# <a name="irowsetupdateimplmmapcacheddata"></a>IRowsetUpdateImpl::m_mapCachedData
Mapa obsahující původní data pro odložené operaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      CAtlMap<   
   HROW hRow,    
   Storage* pData   
>   
m_mapCachedData;  
```  
  
#### <a name="parameters"></a>Parametry  
 `hRow`  
 Zpracování na řádky pro data.  
  
 `pData`  
 Ukazatel na data do mezipaměti. Data je typu *úložiště* (třída uživatelského záznamu). Najdete v článku *úložiště* argument šablony v [IRowsetUpdateImpl – třída](../../data/oledb/irowsetupdateimpl-class.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IRowsetUpdateImpl – třída](../../data/oledb/irowsetupdateimpl-class.md)