---
title: "CDynamicStringAccessor – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDynamicStringAccessor
dev_langs:
- C++
helpviewer_keywords:
- CDynamicStringAccessor class
ms.assetid: 138dc4de-c7c3-478c-863e-431e48249027
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 72ca3d1626b22f286a7e1ca9a276582d68cd7619
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="cdynamicstringaccessor-class"></a>CDynamicStringAccessor – třída
Umožňuje přístup ke zdroji dat, pokud nemáte žádné znalosti schématu databáze (podkladová struktura databáze).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      template< typename BaseType, DBTYPEENUM OleDbType >  
class CDynamicStringAccessorT : public CDynamicAccessor  
```  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[GetString –](../../data/oledb/cdynamicstringaccessor-getstring.md)|Načte zadaný sloupec dat jako řetězec.|  
|[SetString –](../../data/oledb/cdynamicstringaccessor-setstring.md)|Nastaví zadaný sloupec data jako řetězec.|  
  
## <a name="remarks"></a>Poznámky  
 Při [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) požadavku na data v nativním formátu hlášené poskytovatelem, `CDynamicStringAccessor` požadavky, že zprostředkovatel načíst všechna data z úložiště dat jako řetězce data. To je zvlášť vhodné pro jednoduché úlohy, které nevyžadují výpočet hodnot v úložišti dat, například zobrazení nebo tisk úložiště dat obsah.  
  
 Nativní typu dat sloupce v úložišti dat nezáleží; tak dlouho, dokud zprostředkovatel může podporovat převod dat, bude zadejte data ve formátu řetězce. Pokud zprostředkovatel nepodporuje převod nativní datový typ řetězec (který není běžné), vyžádá volání vrátí hodnotu úspěch **DB_S_ERRORSOCCURED**, a stav pro odpovídající sloupec indikovat problém převod s **DBSTATUS_E_CANTCONVERTVALUE**.  
  
 Použití `CDynamicStringAccessor` metody získat informace o sloupci. Tato informace o sloupci použijete k vytvoření dynamicky přistupujícího objektu v době běhu.  
  
 Informace o sloupci je uložen do vyrovnávací paměti, vytvořit a spravovat touto třídou. Získání dat z vyrovnávací paměti pomocí [GetString](../../data/oledb/cdynamicstringaccessor-getstring.md), nebo jej uložte do vyrovnávací paměti pomocí [SetString –](../../data/oledb/cdynamicstringaccessor-setstring.md).  
  
 Se zabývat a příklady použití dynamického přístupového objektu třídy najdete v tématu [použití dynamických přístupových objektů](../../data/oledb/using-dynamic-accessors.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví**: také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace šablony příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor – třída](../../data/oledb/caccessor-class.md)   
 [CDynamicParameterAccessor – třída](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CManualAccessor – třída](../../data/oledb/cmanualaccessor-class.md)   
 [CDynamicAccessor – třída](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicStringAccessorA – třída](../../data/oledb/cdynamicstringaccessora-class.md)   
 [CDynamicStringAccessorW – třída](../../data/oledb/cdynamicstringaccessorw-class.md)   
 [CXMLAccessor – třída](../../data/oledb/cxmlaccessor-class.md)