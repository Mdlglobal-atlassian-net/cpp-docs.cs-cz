---
title: CDBErrorInfo – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDBErrorInfo
- ATL::CDBErrorInfo
- ATL.CDBErrorInfo
dev_langs:
- C++
helpviewer_keywords:
- CDBErrorInfo class
ms.assetid: 9a5c18a2-ee3e-40f5-ab4c-581288d7f737
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 59222e30fe4a0ee7914c4a4d4e8dfa0d6d3a260b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098612"
---
# <a name="cdberrorinfo-class"></a>CDBErrorInfo – třída
Poskytuje podporu pro zpracování chyby OLE DB pomocí OLE DB [IErrorRecords](https://msdn.microsoft.com/en-us/library/ms718112.aspx) rozhraní.  
  
## <a name="syntax"></a>Syntaxe

```cpp
class CDBErrorInfo  
```  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[GetAllErrorInfo](../../data/oledb/cdberrorinfo-getallerrorinfo.md)|Vrátí všechny informace o chybě obsažené v záznam chyby.|  
|[GetBasicErrorInfo](../../data/oledb/cdberrorinfo-getbasicerrorinfo.md)|Volání [IErrorRecords::GetBasicErrorInfo](https://msdn.microsoft.com/en-us/library/ms723907.aspx) vrátit základní informace o zadané chybě.|  
|[GetCustomErrorObject](../../data/oledb/cdberrorinfo-getcustomerrorobject.md)|Volání [IErrorRecords::GetCustomErrorObject](https://msdn.microsoft.com/en-us/library/ms725417.aspx) k vrácení ukazatel na rozhraní v objektu vlastní chyby.|  
|[GetErrorInfo](../../data/oledb/cdberrorinfo-geterrorinfo.md)|Volání [IErrorRecords::GetErrorInfo](https://msdn.microsoft.com/en-us/library/ms711230.aspx) vrátit **IErrorInfo** rozhraní ukazatel na zadaný záznam.|  
|[Geterrorparameters –](../../data/oledb/cdberrorinfo-geterrorparameters.md)|Volání [IErrorRecords::GetErrorParameters](https://msdn.microsoft.com/en-us/library/ms715793.aspx) vrátit parametry chyby.|  
|[GetErrorRecords](../../data/oledb/cdberrorinfo-geterrorrecords.md)|Získá chybu záznamy pro zadaný objekt.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní vrátí jeden nebo více záznamů Chyba uživateli. Volání [CDBErrorInfo::GetErrorRecords](../../data/oledb/cdberrorinfo-geterrorrecords.md) první, chcete-li získat počet záznamů, chyba. Potom jeden z přístup funguje, jako například volání [CDBErrorInfo::GetAllErrorInfo](../../data/oledb/cdberrorinfo-getallerrorinfo.md), načíst informace o chybě pro každý záznam.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [DBViewer](../../visual-cpp-samples.md)   
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)