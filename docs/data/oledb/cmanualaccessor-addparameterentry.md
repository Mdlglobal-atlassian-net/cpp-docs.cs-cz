---
title: CManualAccessor::AddParameterEntry | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CManualAccessor::AddParameterEntry
- ATL.CManualAccessor.AddParameterEntry
- CManualAccessor.AddParameterEntry
- AddParameterEntry
- ATL::CManualAccessor::AddParameterEntry
dev_langs: C++
helpviewer_keywords: AddParameterEntry method
ms.assetid: 9048b164-052b-41b1-a861-227fc529e0b5
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c2e364ce947baa800611f50b67add748a47472fd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cmanualaccessoraddparameterentry"></a>CManualAccessor::AddParameterEntry
Přidá položku parametr struktury vstupní parametr.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      void AddParameterEntry(  
   DBORDINAL nOrdinal,  
   DBTYPE wType,  
   DBLENGTH nColumnSize,  
   void* pData,  
   void* pLength = NULL,  
   void* pStatus = NULL,  
   DBPARAMIO eParamIO = DBPARAMIO_INPUT   
) throw ( );  
```  
  
#### <a name="parameters"></a>Parametry  
 V tématu [DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx) v *referenční příručka programátora prostředí OLE DB*.  
  
 `nOrdinal`  
 [v] Parametr číslo.  
  
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
  
 *eParamIO*  
 [v] Určuje, zda je parametr, ke kterému je přiřazeno vazby vstupní, vstupu a výstupu nebo výstupní parametr.  
  
## <a name="remarks"></a>Poznámky  
 Pokud chcete používat tuto funkci, nejprve je třeba volat [createparameteraccessor –](../../data/oledb/cmanualaccessor-createparameteraccessor.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CManualAccessor – třída](../../data/oledb/cmanualaccessor-class.md)   
 [CManualAccessor::AddBindEntry](../../data/oledb/cmanualaccessor-addbindentry.md)   
 [Ukázka DBViewer](../../visual-cpp-samples.md)