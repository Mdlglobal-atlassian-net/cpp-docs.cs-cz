---
title: AtlTraceErrorRecords | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.AtlTraceErrorRecords
- ATL::AtlTraceErrorRecords
- AtlTraceErrorRecords
dev_langs: C++
helpviewer_keywords: AtlTraceErrorRecords function
ms.assetid: b83970b3-dc2a-445c-9142-f52218719905
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 696d00e32ebf692d8155b93247f3ca83b0bb2b08
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="atltraceerrorrecords"></a>AtlTraceErrorRecords
Vypíše záznam chyby technologie OLE DB informace k výpisu zařízení, pokud se vrátí chyba.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      inline void AtlTraceErrorRecords(   
   HRESULT hrErr = S_OK    
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hErr`  
 [v] `HRESULT` Vrácené funkcí člen šablony příjemce technologie OLE DB.  
  
## <a name="remarks"></a>Poznámky  
 Pokud `hErr` není `S_OK`, `AtlTraceErrorRecords` vypíše záznam chyby technologie OLE DB informace o zařízení výpisu ( **ladění** kartě ve výstupním okně nebo soubor). Informace o záznam chyby, které se získají z poskytovatele, zahrnuje číslo řádku, zdroj, popis, soubor nápovědy, kontextu a identifikátor GUID pro každou položku záznamu chyby. `AtlTraceErrorRecords`Vypíše tyto informace jenom u sestavení ladicí verze. V sestavení pro vydání je prázdný stub, která je optimalizovaná limitu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Makra a globální funkce pro šablony příjemců OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [CDBErrorInfo – třída](../../data/oledb/cdberrorinfo-class.md)