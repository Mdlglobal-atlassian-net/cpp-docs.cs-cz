---
title: IRowsetImpl::GetData | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4c8238fba101efe81219bc332e050d7fd0ed8165
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
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