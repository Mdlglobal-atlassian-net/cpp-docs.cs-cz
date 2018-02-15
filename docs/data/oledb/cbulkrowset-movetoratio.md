---
title: CBulkRowset::MoveToRatio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CBulkRowset.MoveToRatio
- ATL::CBulkRowset::MoveToRatio
- MoveToRatio
- CBulkRowset::MoveToRatio
- ATL.CBulkRowset<TAccessor>.MoveToRatio
- ATL::CBulkRowset<TAccessor>::MoveToRatio
- ATL.CBulkRowset.MoveToRatio
- CBulkRowset<TAccessor>::MoveToRatio
dev_langs:
- C++
helpviewer_keywords:
- MoveToRatio method
ms.assetid: 86be60f5-9341-44c1-8e1e-9174c082d0d5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e680a7e562aaf3e0b1fcb1ee33ea0eb558f62069
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="cbulkrowsetmovetoratio"></a>CBulkRowset::MoveToRatio
Načte řádky od zlomkové pozice v dané sadě řádků.  
  
## <a name="syntax"></a>Syntaxe  
  
```
HRESULT MoveToRatio(DBCOUNTITEM nNumerator,  
   DBCOUNTITEM nDenominator)throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `nNumerator`  
 [v] Čítači používá k určení zlomkové pozici, ze kterého chcete načíst data.  
  
 `nDenominator`  
 [v] Jmenovatel používá k určení zlomkové pozici, ze kterého chcete načíst data.  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
## <a name="remarks"></a>Poznámky  
 `MoveToRatio` načte řádků zhruba podle následující vzorec:  
  
 `(nNumerator *  RowsetSize ) / nDenominator`  
  
 Kde `RowsetSize` je velikost řádků, měřená v řádků. Přesnost tento vzorec závisí na konkrétního zprostředkovatele. Podrobnosti najdete v tématu [IRowsetScroll::GetRowsAtRatio](https://msdn.microsoft.com/en-us/library/ms709602.aspx) v *referenční příručka programátora technologie OLE DB*.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CBulkRowset – třída](../../data/oledb/cbulkrowset-class.md)