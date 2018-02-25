---
title: "IErrorRecordsImpl – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::IErrorRecordsImpl
- ATL.IErrorRecordsImpl
- IErrorRecordsImpl
dev_langs:
- C++
helpviewer_keywords:
- IErrorRecordsImpl class
ms.assetid: dea8e938-c5d8-45ab-86de-eb8fbf534ffb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f3d466cbf761342706774a9b5a52c5b4e69a7328
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ierrorrecordsimpl-class"></a>IErrorRecordsImpl – třída
Implementuje OLE DB [IErrorRecords](https://msdn.microsoft.com/en-us/library/ms718112.aspx) rozhraní, přidání záznamů do a z datový člen načítání záznamů ([m_rgErrors](../../data/oledb/ierrorrecordsimpl-m-rgerrors.md)) typu **CAtlArray <** `RecordClass`**>**.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class RecordClass = ATLERRORINFO>  
class IErrorRecordsImpl : public IErrorRecords  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Třída odvozená z `IErrorRecordsImpl`.  
  
 `RecordClass`  
 Třída, která představuje objekt Chyba OLE DB.  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[GetErrorDescriptionString](../../data/oledb/ierrorrecordsimpl-geterrordescriptionstring.md)|Získá řetězec popis chyby z záznam chyby.|  
|[GetErrorGUID](../../data/oledb/ierrorrecordsimpl-geterrorguid.md)|Získá chybu identifikátoru GUID z záznam chyby.|  
|[GetErrorHelpContext](../../data/oledb/ierrorrecordsimpl-geterrorhelpcontext.md)|Získá ID kontextové nápovědy z záznam chyby.|  
|[GetErrorHelpFile](../../data/oledb/ierrorrecordsimpl-geterrorhelpfile.md)|Získá úplnou cestu k souboru nápovědy z záznam chyby.|  
|[Geterrorsource –](../../data/oledb/ierrorrecordsimpl-geterrorsource.md)|Získá zdroj kód chyby z záznam chyby.|  
  
### <a name="interface-methods"></a>Metody rozhraní  
  
|||  
|-|-|  
|[AddErrorRecord](../../data/oledb/ierrorrecordsimpl-adderrorrecord.md)|Přidá záznam objektu Chyba OLE DB.|  
|[GetBasicErrorInfo](../../data/oledb/cdberrorinfo-getbasicerrorinfo.md)|Vrátí základní informace o této chybě, např. Návratový kód a číslo chyby specifický pro zprostředkovatele.|  
|[GetCustomErrorObject](../../data/oledb/cdberrorinfo-getcustomerrorobject.md)|Vrací ukazatel na rozhraní na objekt vlastní chyby.|  
|[GetErrorInfo](../../data/oledb/cdberrorinfo-geterrorinfo.md)|Vrátí [IErrorInfo](https://msdn.microsoft.com/en-us/library/ms718112.aspx) ukazatel rozhraní na zadaný záznam.|  
|[GetErrorParameters](../../data/oledb/cdberrorinfo-geterrorparameters.md)|Vrátí parametry chyby.|  
|[GetRecordCount](../../mfc/reference/cdaorecordset-class.md#getrecordcount)|Vrátí počet záznamů v objektu záznamů technologie OLE DB.|  
  
### <a name="data-members"></a>Datové členy  
  
|||  
|-|-|  
|[m_rgErrors](../../data/oledb/ierrorrecordsimpl-m-rgerrors.md)|Pole záznamy o chybách.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)