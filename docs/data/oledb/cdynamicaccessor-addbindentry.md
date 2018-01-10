---
title: CDynamicAccessor::AddBindEntry | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CDynamicAccessor::AddBindEntry
- AddBindEntry
- CDynamicAccessor.AddBindEntry
- CDynamicAccessor::AddBindEntry
- ATL.CDynamicAccessor.AddBindEntry
dev_langs: C++
helpviewer_keywords: AddBindEntry method
ms.assetid: 8f139376-7db3-4193-ba3b-63fe938ffa79
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 910418d83358817e7b0975507b6797c87cab514a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cdynamicaccessoraddbindentry"></a>CDynamicAccessor::AddBindEntry
Přidá položku vazby ke sloupcům výstup.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      HRESULT AddBindEntry(   
   const DBCOLUMNINFO& info    
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `info`  
 [v] A **DBCOLUMNINFO** struktura obsahující informace o sloupci. V části "DBCOLUMNINFO struktury" v [IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx) v *referenční příručka programátora prostředí OLE DB*.  
  
## <a name="return-value"></a>Návratová hodnota  
 Jeden standardní `HRESULT` hodnoty.  
  
## <a name="remarks"></a>Poznámky  
 Tuto metodu použijte, pokud přepsání výchozí přístupového objektu, vytvořené pomocí `CDynamicAccessor` (viz [jak se dá načíst Data?](../../data/oledb/fetching-data.md)).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDynamicAccessor – třída](../../data/oledb/cdynamicaccessor-class.md)