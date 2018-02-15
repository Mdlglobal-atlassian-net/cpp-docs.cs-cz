---
title: CBulkRowset::MoveToBookmark | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CBulkRowset<TAccessor>::MoveToBookmark
- CBulkRowset.MoveToBookmark
- MoveToBookmark
- ATL.CBulkRowset.MoveToBookmark
- CBulkRowset::MoveToBookmark
- ATL::CBulkRowset<TAccessor>::MoveToBookmark
- ATL::CBulkRowset::MoveToBookmark
dev_langs:
- C++
helpviewer_keywords:
- MoveToBookmark method
ms.assetid: 76aab025-819e-4ecd-ae0a-d8d3fb2d2099
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8ec5c21c11fc7a733b64ce97863e7fc4bfa583e6
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="cbulkrowsetmovetobookmark"></a>CBulkRowset::MoveToBookmark
Načte řádek označený záložku nebo řádek na zadaný posun (`lSkip`) z tuto záložku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT MoveToBookmark(const CBookmarkBase& bookmark,  
   DBCOUNTITEM lSkip = 0) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `bookmark`  
 [v] Záložku označení umístění, ze kterého chcete načíst data.  
  
 `lSkip`  
 [v] Číslo počet řádků z záložky na cílový řádek. Pokud `lSkip` rovná nule, načtených první řádek je řádek označený záložkou. Pokud `lSkip` je 1, načtených první řádek je řádek po řádku záložkou. Pokud `lSkip` je -1, načtených první řádek je řádek před záložkou řádek.  
  
## <a name="return-value"></a>Návratová hodnota  
 V tématu [IRowset::GetData](https://msdn.microsoft.com/en-us/library/ms716988.aspx) v *referenční příručka programátora prostředí OLE DB*.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CBulkRowset – třída](../../data/oledb/cbulkrowset-class.md)