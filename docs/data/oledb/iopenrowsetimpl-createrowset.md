---
title: IOpenRowsetImpl::CreateRowset | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IOpenRowsetImpl.CreateRowset
- IOpenRowsetImpl::CreateRowset
- CreateRowset
dev_langs: C++
helpviewer_keywords: CreateRowset method
ms.assetid: 69041cf6-7a2f-4409-a26e-6e984c24986e
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: dc67ec84af8125f92334077dcd3ab3580d31877a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="iopenrowsetimplcreaterowset"></a>IOpenRowsetImpl::CreateRowset
Vytvoří objekt sady řádků. Není volána přímo uživatelem. V tématu [IOpenRowset::OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx) v *referenční příručka programátora prostředí OLE DB.*  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      template <class   
      RowsetClass  
      >  
HRESULT CreateRowset(  
   IUnknown* pUnkOuter,  
   DBID* pTableID,  
   DBID* pIndexID,  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown** ppRowset,  
   RowsetClass*& pRowsetObj   
);  
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