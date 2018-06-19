---
title: CRowset::IsSameRow | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- IsSameRow method
ms.assetid: 53cba847-52f5-4dd9-973f-bbe7454c425c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5cbe8179c04b8d7ab855942a4e6190341cc03128
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33097117"
---
# <a name="crowsetissamerow"></a>CRowset::IsSameRow
Porovná zadaný řádek s aktuální řádek.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT IsSameRow(HROW hRow) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `hRow`  
 [v] Popisovač pro řádek, který má být porovnán na aktuálním řádku.  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`. `S_OK` Označuje, že řádky jsou stejné. Pro ostatní hodnoty, najdete v části [IRowsetIndentity::IsSameRow](https://msdn.microsoft.com/en-us/library/ms719629.aspx) v *referenční příručka programátora technologie OLE DB* ve Windows SDK.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CRowset – třída](../../data/oledb/crowset-class.md)