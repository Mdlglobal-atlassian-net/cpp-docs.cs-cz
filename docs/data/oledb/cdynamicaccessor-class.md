---
title: "CDynamicAccessor – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CDynamicAccessor
- ATL::CDynamicAccessor
- CDynamicAccessor
dev_langs: C++
helpviewer_keywords: CDynamicAccessor class
ms.assetid: 374b13b7-1f09-457d-9e6b-df260ff4d178
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f88c3eff9c8160a0e322c93dacf6985dc7b8a20b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cdynamicaccessor-class"></a>CDynamicAccessor – třída
Umožňuje přístup ke zdroji dat, pokud nemáte žádné znalosti schématu databáze (podkladová struktura databáze).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDynamicAccessor : public CAccessorBase  
```  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[AddBindEntry –](../../data/oledb/cdynamicaccessor-addbindentry.md)|Přidá položku vazby ke sloupcům výstup při přepisování výchozí přistupující objekt.|  
|[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)|Vytvoří a inicializuje `CDynamicAccessor` objektu.|  
|[Zavřete](../../data/oledb/cdynamicaccessor-close.md)|Odpojuje všechny sloupce, uvolňuje přidělenou paměť a uvolní [IAccessor](https://msdn.microsoft.com/en-us/library/ms719672.aspx) ukazatel rozhraní ve třídě.|  
|[GetBookmark –](../../data/oledb/cdynamicaccessor-getbookmark.md)|Načte záložku pro aktuální řádek.|  
|[Getblobhandling –](../../data/oledb/cdynamicaccessor-getblobhandling.md)|Načte objekt BLOB zpracování hodnotu pro aktuální řádek.|  
|[Getblobsizelimit –](../../data/oledb/cdynamicaccessor-getblobsizelimit.md)|Načte maximální velikost objektu BLOB v bajtech.|  
|[Getcolumncount –](../../data/oledb/cdynamicaccessor-getcolumncount.md)|Načte počet sloupců v sadě řádků.|  
|[Getcolumnflags –](../../data/oledb/cdynamicaccessor-getcolumnflags.md)|Načte vlastnosti sloupce.|  
|[GetColumnInfo –](../../data/oledb/cdynamicaccessor-getcolumninfo.md)|Načte metadata sloupce.|  
|[Getcolumnname –](../../data/oledb/cdynamicaccessor-getcolumnname.md)|Načte název zadaný sloupec.|  
|[Getcolumntype –](../../data/oledb/cdynamicaccessor-getcolumntype.md)|Načte datový typ zadaný sloupec.|  
|[GetLength –](../../data/oledb/cdynamicaccessor-getlength.md)|Načte maximální délce sloupec v bajtech.|  
|[Getordinal –](../../data/oledb/cdynamicaccessor-getordinal.md)|Načte index sloupce, který je zadaný název sloupce.|  
|[GetStatus –](../../data/oledb/cdynamicaccessor-getstatus.md)|Načte stav zadaný sloupec.|  
|[GetValue](../../data/oledb/cdynamicaccessor-getvalue.md)|Načte data z vyrovnávací paměti.|  
|[Setblobhandling –](../../data/oledb/cdynamicaccessor-setblobhandling.md)|Nastaví objekt BLOB zpracování hodnotu pro aktuální řádek.|  
|[Setblobsizelimit –](../../data/oledb/cdynamicaccessor-setblobsizelimit.md)|Nastaví maximální velikost objektu BLOB v bajtech.|  
|[SetLength](../../data/oledb/cdynamicaccessor-setlength.md)|Nastaví délku sloupce v bajtech.|  
|[SetStatus](../../data/oledb/cdynamicaccessor-setstatus.md)|Nastaví stav zadaný sloupec.|  
|[SetValue](../../data/oledb/cdynamicaccessor-setvalue.md)|Ukládá data do vyrovnávací paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Použití `CDynamicAccessor` metody získat informace o sloupci například názvy sloupců, počet sloupců, datový typ a tak dále. Pak tyto informace sloupec použít k vytvoření dynamicky přistupujícího objektu v době běhu.  
  
 Informace o sloupci je uložen do vyrovnávací paměti, který je vytvořen a spravován společností tuto třídu. Získání dat z vyrovnávací paměti pomocí [GetValue](../../data/oledb/cdynamicaccessor-getvalue.md).  
  
 Se zabývat a příklady použití dynamického přístupového objektu třídy najdete v tématu [použití dynamických přístupových objektů](../../data/oledb/using-dynamic-accessors.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví**: také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace šablony příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor – třída](../../data/oledb/caccessor-class.md)   
 [CDynamicParameterAccessor – třída](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CManualAccessor – třída](../../data/oledb/cmanualaccessor-class.md)