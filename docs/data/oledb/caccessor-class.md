---
title: "CAccessor – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CAccessor<T>
- ATL::CAccessor
- CAccessor
- ATL::CAccessor<T>
- ATL.CAccessor
dev_langs:
- C++
helpviewer_keywords:
- CAccessor class
ms.assetid: b2ba959f-a686-46f3-8837-176248aef748
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1f0e893f300b7d89bee14ce28490328979d0fa17
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="caccessor-class"></a>CAccessor – třída
Představuje jeden z typů přistupujícího objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
template <class T>  
class CAccessor : public CAccessorBase, public T  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Třída záznamu uživatele.  
  
## <a name="remarks"></a>Poznámky  
 Používá se při záznamu je staticky vázán ke zdroji dat. Záznam obsahuje vyrovnávací paměti. Tato třída podporuje několik přístupových objektů pro sadu řádků.  
  
 Tento typ přistupující objekt použijte, když víte strukturu a typ databáze.  
  
 Pokud vaše přistupujícího objektu obsahuje pole, které odkazují na paměti (například `BSTR` nebo rozhraní), musí být vydání, zavolejte členskou funkci [CAccessorRowset::FreeRecordMemory](../../data/oledb/caccessorrowset-freerecordmemory.md) před dalším záznam pro čtení.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)