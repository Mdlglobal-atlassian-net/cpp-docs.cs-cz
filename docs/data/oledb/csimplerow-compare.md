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
ms.openlocfilehash: 8e49dcc0356c563312c0d73041ab412716694c1a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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