---
title: CManualAccessor::AddBindEntry | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CManualAccessor::AddBindEntry
- ATL.CManualAccessor.AddBindEntry
- CManualAccessor::AddBindEntry
- AddBindEntry
- CManualAccessor.AddBindEntry
dev_langs: C++
helpviewer_keywords: AddBindEntry method
ms.assetid: 8556dda9-dda1-4f67-96bc-6031e6c6a271
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 14a2fbae8ee29728d145b3ff8d20a02b4000b5a2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmanualaccessoraddbindentry"></a>CManualAccessor::AddBindEntry
Přidá položku vazby ke sloupcům výstup.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      void AddBindEntry(  
   DBORDINAL nOrdinal,  
   DBTYPE wType,  
   DBLENGTH nColumnSize,  
   void* pData,  
   void* pLength = NULL,  
   void* pStatus = NULL   
) throw ( );  
```  
  
#### <a name="parameters"></a>Parametry  
 V tématu [DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx) v *referenční příručka programátora prostředí OLE DB*.  
  
 `nOrdinal`  
 [v] Počet sloupců.  
  
 `wType`  
 [v] Datový typ.  
  
 `nColumnSize`  
 [v] Sloupec velikost v bajtech.  
  
 `pData`  
 [v] Ukazatel na data ve sloupci uložené ve vyrovnávací paměti.  
  
 `pLength`  
 [v] Ukazatel na délka pole, v případě potřeby.  
  
 `pStatus`  
 [v] Ukazatel na proměnnou bylo vázané na sloupec Stav, pokud je to nutné.  
  
## <a name="remarks"></a>Poznámky  
 Pokud chcete používat tuto funkci, nejprve je třeba volat [CreateAccessor –](../../data/oledb/cmanualaccessor-createaccessor.md). Nelze přidat další položky než počet sloupců zadaný v `CreateAccessor`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CManualAccessor – třída](../../data/oledb/cmanualaccessor-class.md)   
 [Ukázka DBViewer](../../visual-cpp-samples.md)