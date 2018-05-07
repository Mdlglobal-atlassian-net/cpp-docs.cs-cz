---
title: CManualAccessor::AddBindEntry | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CManualAccessor::AddBindEntry
- ATL.CManualAccessor.AddBindEntry
- CManualAccessor::AddBindEntry
- AddBindEntry
- CManualAccessor.AddBindEntry
dev_langs:
- C++
helpviewer_keywords:
- AddBindEntry method
ms.assetid: 8556dda9-dda1-4f67-96bc-6031e6c6a271
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 59793bd61b17fe2ead4948932efa1b583da8e1a8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cmanualaccessoraddbindentry"></a>CManualAccessor::AddBindEntry
Přidá položku vazby ke sloupcům výstup.  
  
## <a name="syntax"></a>Syntaxe  
  
```
void AddBindEntry(DBORDINAL nOrdinal,  
   DBTYPE wType,  DBLENGTH nColumnSize,  
   void* pData,  
   void* pLength = NULL,  
   void* pStatus = NULL) throw ();  
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