---
title: CManualAccessor – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CManualAccessor
- ATL.CManualAccessor
- CManualAccessor
dev_langs:
- C++
helpviewer_keywords:
- CManualAccessor class
ms.assetid: a0088074-7135-465c-b228-69097a50b8cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7b8efc46971b1aa72f8c5e572aa540bfed250d2b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cmanualaccessor-class"></a>CManualAccessor – třída
Představuje typ přístupového objektu, který je určený pro pokročilé uživatele.  
  
## <a name="syntax"></a>Syntaxe

```cpp
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