---
title: CRowset::IsSameRow | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRowset::IsSameRow
- CRowset.IsSameRow
- IsSameRow
- ATL::CRowset::IsSameRow
- ATL.CRowset.IsSameRow
- CRowset<TAccessor>::IsSameRow
- ATL.CRowset<TAccessor>.IsSameRow
- CRowset<TAccessor>.IsSameRow
- ATL::CRowset<TAccessor>::IsSameRow
dev_langs: C++
helpviewer_keywords: IsSameRow method
ms.assetid: 53cba847-52f5-4dd9-973f-bbe7454c425c
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a67952947275789fbcb38e8807a2b754cd4baf8a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="crowsetissamerow"></a>CRowset::IsSameRow
Porovná zadaný řádek s aktuální řádek.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      HRESULT IsSameRow(   
   HROW hRow    
) const throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `hRow`  
 [v] Popisovač pro řádek, který má být porovnán na aktuálním řádku.  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`. `S_OK`Označuje, že řádky jsou stejné. Pro ostatní hodnoty, najdete v části [IRowsetIndentity::IsSameRow](https://msdn.microsoft.com/en-us/library/ms719629.aspx) v *referenční příručka programátora technologie OLE DB* ve Windows SDK.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CRowset – třída](../../data/oledb/crowset-class.md)