---
title: "CDBErrorInfo – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDBErrorInfo
- ATL::CDBErrorInfo
- ATL.CDBErrorInfo
dev_langs: C++
helpviewer_keywords: CDBErrorInfo class
ms.assetid: 9a5c18a2-ee3e-40f5-ab4c-581288d7f737
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3d1ecd29e32686e8cc91ec9716625beeee2cef25
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cdberrorinfo-class"></a>CDBErrorInfo – třída
Poskytuje podporu pro zpracování chyby OLE DB pomocí OLE DB [IErrorRecords](https://msdn.microsoft.com/en-us/library/ms718112.aspx) rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDBErrorInfo  
```  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Getallerrorinfo –](../../data/oledb/cdberrorinfo-getallerrorinfo.md)|Vrátí všechny informace o chybě obsažené v záznam chyby.|  
|[Getbasicerrorinfo –](../../data/oledb/cdberrorinfo-getbasicerrorinfo.md)|Volání [IErrorRecords::GetBasicErrorInfo](https://msdn.microsoft.com/en-us/library/ms723907.aspx) vrátit základní informace o zadané chybě.|  
|[Getcustomerrorobject –](../../data/oledb/cdberrorinfo-getcustomerrorobject.md)|Volání [IErrorRecords::GetCustomErrorObject](https://msdn.microsoft.com/en-us/library/ms725417.aspx) k vrácení ukazatel na rozhraní v objektu vlastní chyby.|  
|[GetErrorInfo –](../../data/oledb/cdberrorinfo-geterrorinfo.md)|Volání [IErrorRecords::GetErrorInfo](https://msdn.microsoft.com/en-us/library/ms711230.aspx) vrátit **IErrorInfo** rozhraní ukazatel na zadaný záznam.|  
|[Geterrorparameters –](../../data/oledb/cdberrorinfo-geterrorparameters.md)|Volání [IErrorRecords::GetErrorParameters](https://msdn.microsoft.com/en-us/library/ms715793.aspx) vrátit parametry chyby.|  
|[Geterrorrecords –](../../data/oledb/cdberrorinfo-geterrorrecords.md)|Získá chybu záznamy pro zadaný objekt.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní vrátí jeden nebo více záznamů Chyba uživateli. Volání [CDBErrorInfo::GetErrorRecords](../../data/oledb/cdberrorinfo-geterrorrecords.md) první, chcete-li získat počet záznamů, chyba. Potom jeden z přístup funguje, jako například volání [CDBErrorInfo::GetAllErrorInfo](../../data/oledb/cdberrorinfo-getallerrorinfo.md), načíst informace o chybě pro každý záznam.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [DBViewer](../../visual-cpp-samples.md)   
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace šablony příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)