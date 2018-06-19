---
title: IOpenRowsetImpl::CreateRowset | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IOpenRowsetImpl.CreateRowset
- IOpenRowsetImpl::CreateRowset
- CreateRowset
dev_langs:
- C++
helpviewer_keywords:
- CreateRowset method
ms.assetid: 69041cf6-7a2f-4409-a26e-6e984c24986e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2d4554a2aeee3218ce505dc2c135167a3e38d55c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33105176"
---
# <a name="iopenrowsetimplcreaterowset"></a>IOpenRowsetImpl::CreateRowset
Vytvoří objekt sady řádků. Není volána přímo uživatelem. V tématu [IOpenRowset::OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx) v *referenční příručka programátora prostředí OLE DB.*  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      template template <class RowsetClass  
      >  
HRESULT CreateRowset(IUnknown* pUnkOuter,  
   DBID* pTableID,  
   DBID* pIndexID,  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown** ppRowset,  
   RowsetClass*& pRowsetObj);  
```  
  
#### <a name="parameters"></a>Parametry  
 `RowsetClass`  
 Člena třídy šablony představující uživatele třídy sady řádků. Obvykle je vygenerovat průvodcem.  
  
 `pRowsetObj`  
 [out] Ukazatel na objektu sady řádků. Tento parametr se obvykle nepoužívá, ale můžete použít, pokud je třeba provést další práci na sadě řádků před předáním k objektu COM. Životnost `pRowsetObj` je svázaná s `ppRowset`.  
  
 Dalších parametrů, najdete v části [IOpenRowset::OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx) v *referenční příručka programátora technologie OLE DB.*  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IOpenRowsetImpl – třída](../../data/oledb/iopenrowsetimpl-class.md)