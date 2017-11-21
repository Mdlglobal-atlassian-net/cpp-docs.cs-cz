---
title: "CManualAccessor – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CManualAccessor
- ATL.CManualAccessor
- CManualAccessor
dev_langs: C++
helpviewer_keywords: CManualAccessor class
ms.assetid: a0088074-7135-465c-b228-69097a50b8cc
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f368bbb2f56497ecb16dc2cbfd2f8cf7d214e5cc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cmanualaccessor-class"></a>CManualAccessor – třída
Představuje typ přístupového objektu, který je určený pro pokročilé uživatele.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CManualAccessor : public CAccessorBase  
```  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[AddBindEntry –](../../data/oledb/cmanualaccessor-addbindentry.md)|Přidá položku vazby ke sloupcům výstup.|  
|[AddParameterEntry –](../../data/oledb/cmanualaccessor-addparameterentry.md)|Přidá položku parametr parametr přistupujícího objektu.|  
|[CreateAccessor –](../../data/oledb/cmanualaccessor-createaccessor.md)|Přidělí paměť pro sloupec struktury vazby a inicializuje data členy sloupců.|  
|[Createparameteraccessor –](../../data/oledb/cmanualaccessor-createparameteraccessor.md)|Přidělí paměť pro parametr vazby struktury a inicializuje parametry datových členů.|  
  
## <a name="remarks"></a>Poznámky  
 Pomocí `CManualAccessor`, můžete zadat parametr a výstup vazba sloupce ve volání funkce spuštění.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [DBViewer](../../visual-cpp-samples.md)   
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace šablony příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor – třída](../../data/oledb/caccessor-class.md)   
 [CDynamicAccessor – třída](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicParameterAccessor – třída](../../data/oledb/cdynamicparameteraccessor-class.md)