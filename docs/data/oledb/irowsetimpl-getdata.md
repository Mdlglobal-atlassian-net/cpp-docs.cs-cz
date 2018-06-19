---
title: IRowsetImpl::GetData | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IRowsetImpl.GetData
- ATL::IRowsetImpl::GetData
- IRowsetImpl::GetData
- IRowsetImpl.GetData
dev_langs:
- C++
helpviewer_keywords:
- GetData method [OLE DB]
ms.assetid: cb15f1cc-bd25-4b74-93c3-db71aa93829c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3e2a20e8f1948078aec6994516e05f83e95cdcc1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33102602"
---
# <a name="irowsetimplgetdata"></a>IRowsetImpl::GetData
Načte data z dané sadě řádků kopii řádku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD(GetData )(HROW hRow,  
   HACCESSOR hAccessor,  
   void* pDstData);  
```  
  
#### <a name="parameters"></a>Parametry  
 V tématu [IRowset::GetData](https://msdn.microsoft.com/en-us/library/ms716988.aspx) v *referenční příručka programátora prostředí OLE DB*.  
  
 Některé parametry odpovídají *referenční příručka programátora technologie OLE DB* parametry odlišné názvy, které jsou popsány v **IRowset::GetData**:  
  
|Parametry šablony technologie OLE DB|*Referenční příručka programátora technologie OLE DB* parametry|  
|--------------------------------|------------------------------------------------|  
|*pDstData*|`pData`|  
  
## <a name="remarks"></a>Poznámky  
 Také obstará převod dat pomocí převodu dat OLE DB knihovny DLL.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IRowsetImpl – třída](../../data/oledb/irowsetimpl-class.md)