---
title: IRowsetLocateImpl::Compare | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IRowsetLocateImpl.Compare
- IRowsetLocateImpl::Compare
- IRowsetLocateImpl.Compare
- ATL::IRowsetLocateImpl::Compare
dev_langs:
- C++
helpviewer_keywords:
- Compare method
ms.assetid: 6f84052c-c68c-480a-982f-03748faa7d5d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 208f912e92045daec36066e1dcc06fc38b5a8ed2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="irowsetlocateimplcompare"></a>IRowsetLocateImpl::Compare
Porovná dvě záložky.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD (Compare )(HCHAPTER /* hReserved */,  
   DBBKMARK cbBookmark1,  
   const BYTE* pBookmark1,  
   DBBKMARK cbBookmark2,  
   const BYTE* pBookmark2,  
   DBCOMPARE* pComparison);  
```  
  
#### <a name="parameters"></a>Parametry  
 V tématu [IRowsetLocate::Compare](https://msdn.microsoft.com/en-us/library/ms709539.aspx) v *referenční příručka programátora prostředí OLE DB*.  
  
## <a name="remarks"></a>Poznámky  
 Některý z záložky může být standard definovaný OLE DB [standardní záložku](https://msdn.microsoft.com/en-us/library/ms712954.aspx) (**DBBMK_FIRST**, **DBBMK_LAST**, nebo **DBBMK_INVALID**). Hodnota vrácená v `pComparison` označuje vztah mezi dvěma záložky:  
  
-   **DBCOMPARE_LT** (`cbBookmark1` před `cbBookmark2`.)  
  
-   **DBCOMPARE_EQ** (`cbBookmark1` rovná `cbBookmark2`.)  
  
-   **DBCOMPARE_GT** (`cbBookmark1` po `cbBookmark2`.)  
  
-   **DBCOMPARE_NE** (záložky jsou stejná a není seřazené).  
  
-   **DBCOMPARE_NOTCOMPARABLE** (záložky nejde porovnat.)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IRowsetLocateImpl – třída](../../data/oledb/irowsetlocateimpl-class.md)