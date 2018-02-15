---
title: CTable::Open | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CTable.Open
- ATL::CTable::Open
- CTable::Open
- CTable.Open
dev_langs:
- C++
helpviewer_keywords:
- Open method
ms.assetid: 5d006d95-74d7-4e2b-b243-a33bc53b5455
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8f4e969e1ab8fd6e43a2a8c1d568974b41f3b692
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="ctableopen"></a>CTable::Open
Otevře se v tabulce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Open(const CSession& session,  
   LPCWSTR wszTableName,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0) throw ();  


HRESULT Open(const CSession& session,  
   LPCSTR szTableName,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0) throw ();  


HRESULT Open(const CSession& session,  
   DBID& dbid,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0) throw ();  
```  
  
#### <a name="parameters"></a>Parametry  
 `session`  
 [v] Relace, pro kterou je otevřen v tabulce.  
  
 *wszTableName*  
 [v] Název tabulky, který chcete otevřít, předat jako řetězec znaků Unicode.  
  
 *szTableName*  
 [v] Název tabulky, který chcete otevřít, předat jako řetězec ANSI.  
  
 *DBID*  
 [v] **DBID** tabulky otevřete.  
  
 *pPropSet*  
 [v] Ukazatel na pole [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) struktury obsahující vlastnosti a hodnoty nastavení. V tématu [sady vlastností a vlastnost skupiny](https://msdn.microsoft.com/en-us/library/ms713696.aspx) v *referenční příručka programátora prostředí OLE DB* ve Windows SDK. Výchozí hodnota Null určuje žádné vlastnosti.  
  
 `ulPropSets`  
 [v] Počet [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) struktury předaná *pPropSet* argument.  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
## <a name="remarks"></a>Poznámky  
 Další podrobnosti najdete v tématu [IOpenRowset::OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx) v *referenční příručka programátora technologie OLE DB*.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CTable – třída](../../data/oledb/ctable-class.md)