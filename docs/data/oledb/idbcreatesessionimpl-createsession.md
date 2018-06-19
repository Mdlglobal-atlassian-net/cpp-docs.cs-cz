---
title: IDBCreateSessionImpl::CreateSession | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IDBCreateSessionImpl::CreateSession
- IDBCreateSessionImpl.CreateSession
- CreateSession
dev_langs:
- C++
helpviewer_keywords:
- CreateSession method
ms.assetid: 035e5ddb-56e6-43b1-874d-89c0e40b103b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fe8117d77ae82e4287e7ed4a81a07569848c213b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33099196"
---
# <a name="idbcreatesessionimplcreatesession"></a>IDBCreateSessionImpl::CreateSession
Vytvoří novou relaci z objekt zdroje dat a vrátí požadované rozhraní v nově vytvořené relace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD(CreateSession)(IUnknown * pUnkOuter,   
   REFIID riid,   
   IUnknown ** ppDBSession);  
```  
  
#### <a name="parameters"></a>Parametry  
 V tématu [IDBCreateSession::CreateSession](https://msdn.microsoft.com/en-us/library/ms714942.aspx) v *referenční příručka programátora prostředí OLE DB*.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IDBCreateSessionImpl – třída](../../data/oledb/idbcreatesessionimpl-class.md)