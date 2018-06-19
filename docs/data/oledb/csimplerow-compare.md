---
title: CSimpleRow::Compare | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CSimpleRow.Compare
- CSimpleRow::Compare
dev_langs:
- C++
helpviewer_keywords:
- Compare method
ms.assetid: 0bb65f09-c7bc-449b-aa4e-c828cac13510
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 75d79e753f1f4af630c26ef07fbb7241576535ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098962"
---
# <a name="csimplerowcompare"></a>CSimpleRow::Compare
Porovná dva řádky, které chcete zobrazit, pokud odkazují na stejnou instanci řádek.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Compare(CSimpleRow* pRow);  
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