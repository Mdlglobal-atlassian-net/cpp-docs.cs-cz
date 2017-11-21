---
title: IRowsetLocateImpl::GetRowsByBookmark | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IRowsetLocateImpl::GetRowsByBookmark
- IRowsetLocateImpl.GetRowsByBookmark
- GetRowsByBookmark
dev_langs: C++
helpviewer_keywords: GetRowsByBookmark method
ms.assetid: 07906e42-3582-427e-812a-aa19791e3c56
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 938a32796f61bbb1873866db6b6b81b017e0a1d0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetlocateimplgetrowsbybookmark"></a>IRowsetLocateImpl::GetRowsByBookmark
Načte jeden nebo více řádků, které odpovídají zadané záložky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      STDMETHOD ( GetRowsByBookmark )(  
   HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const DBBKMARK rgcbBookmarks[],  
   const BYTE* rgpBookmarks,  
   HROW rghRows[],  
   DBROWSTATUS* rgRowStatus[]   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hReserved`  
 [v] Odpovídá `hChapter` parametru [IRowsetLocate::GetRowsByBookmark](https://msdn.microsoft.com/en-us/library/ms725420.aspx).  
  
 Dalších parametrů, najdete v části [IRowsetLocate::GetRowsByBookmark](https://msdn.microsoft.com/en-us/library/ms725420.aspx) v *referenční příručka programátora technologie OLE DB*.  
  
## <a name="remarks"></a>Poznámky  
 Záložka může být hodnota definujete nebo OLE DB [standardní záložky](https://msdn.microsoft.com/en-us/library/ms712954.aspx) (**DBBMK_FIRST** nebo **DBBMK_LAST**). Nedojde ke změně pozice kurzoru.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IRowsetLocateImpl – třída](../../data/oledb/irowsetlocateimpl-class.md)   
 [IRowsetLocateImpl::GetRowsAt](../../data/oledb/irowsetlocateimpl-getrowsat.md)