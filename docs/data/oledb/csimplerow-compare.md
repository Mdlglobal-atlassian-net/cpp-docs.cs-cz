---
title: CSimpleRow::Compare | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CSimpleRow.Compare
- CSimpleRow::Compare
dev_langs: C++
helpviewer_keywords: Compare method
ms.assetid: 0bb65f09-c7bc-449b-aa4e-c828cac13510
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 87ee21022aa379820ced0463892be12ee0676d88
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="csimplerowcompare"></a>CSimpleRow::Compare
Porovná dva řádky, které chcete zobrazit, pokud odkazují na stejnou instanci řádek.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      HRESULT Compare(   
   CSimpleRow* pRow    
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRow`  
 Ukazatel na `CSimpleRow` objektu.  
  
## <a name="return-value"></a>Návratová hodnota  
 `HRESULT` Hodnota se obvykle `S_OK`, o tom, dva řádky na stejnou instanci řádek nebo **S_FALSE**, označující dva řádky se liší. V tématu [IRowsetIdentity::IsSameRow](https://msdn.microsoft.com/en-us/library/ms719629.aspx) v *referenční příručka programátora technologie OLE DB* pro ostatní možné vrácené hodnoty.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [CSimpleRow – třída](../../data/oledb/csimplerow-class.md)   
 [CSimpleRow::ReleaseRow](../../data/oledb/csimplerow-releaserow.md)   
 [IRowsetImpl::RefRows](../../data/oledb/irowsetimpl-refrows.md)