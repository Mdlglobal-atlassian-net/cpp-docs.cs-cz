---
title: IRowsetUpdateImpl::m_mapCachedData | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IRowsetUpdateImpl.m_mapCachedData
- IRowsetUpdateImpl::m_mapCachedData
- m_mapCachedData
dev_langs: C++
helpviewer_keywords: m_mapCachedData
ms.assetid: 65131743-8580-48c8-bb22-68f17c9dfa13
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6007498d85160124484860726d09523b9340bd14
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetupdateimplmmapcacheddata"></a>IRowsetUpdateImpl::m_mapCachedData
Mapa obsahující původní data pro odložené operaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
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