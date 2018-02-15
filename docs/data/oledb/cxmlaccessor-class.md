---
title: "CXMLAccessor – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CXMLAccessor
- CXMLAccessor
- ATL.CXMLAccessor
dev_langs:
- C++
helpviewer_keywords:
- CXMLAccessor class
ms.assetid: c88c082c-ec2f-4351-8947-a330b15e448a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 00d9caa5c49d47eb005e85bdd715864651634a5a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="cxmlaccessor-class"></a>CXMLAccessor – třída
Umožňuje přístup ke zdrojům dat jako řetězce data, když nemáte žádné znalosti schéma úložiště dat (podkladová struktura).  
  
## <a name="syntax"></a>Syntaxe

```cpp
class CXMLAccessor : public CDynamicStringAccessorW  
```  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[GetXMLColumnData](../../data/oledb/cxmlaccessor-getxmlcolumndata.md)|Načte informace o sloupci.|  
|[GetXMLRowData](../../data/oledb/cxmlaccessor-getxmlrowdata.md)|Načte celý obsah tabulky po řádcích.|  
  
## <a name="remarks"></a>Poznámky  
 Ale `CXMLAccessor` se liší od `CDynamicStringAccessorW` , převede ji všechna data z úložiště dat jako (s příznakem) data ve formátu XML. To je užitečné zejména pro výstup na používajícím XML webové stránky. Názvy značek XML bude co nejblíže odpovídat úložiště dat názvy sloupců.  
  
 Použití `CDynamicAccessor` metody získat informace o sloupci. Tato informace o sloupci použijete k vytvoření dynamicky přistupujícího objektu v době běhu.  
  
 Informace o sloupci je uložen do vyrovnávací paměti, vytvořit a spravovat touto třídou. Získání informací pomocí sloupce [GetXMLColumnData –](../../data/oledb/cxmlaccessor-getxmlcolumndata.md) nebo získat data sloupce po řádcích pomocí [GetXMLRowData –](../../data/oledb/cxmlaccessor-getxmlrowdata.md).  
  
## <a name="example"></a>Příklad  
 [!code-cpp[NVC_OLEDB_Consumer#14](../../data/oledb/codesnippet/cpp/cxmlaccessor-class_1.cpp)]  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví**: také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace šablony příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor – třída](../../data/oledb/caccessor-class.md)   
 [CDynamicAccessor – třída](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicParameterAccessor – třída](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CDynamicStringAccessor – třída](../../data/oledb/cdynamicstringaccessor-class.md)   
 [CDynamicStringAccessorA – třída](../../data/oledb/cdynamicstringaccessora-class.md)   
 [CDynamicStringAccessorW – třída](../../data/oledb/cdynamicstringaccessorw-class.md)   
 [CManualAccessor – třída](../../data/oledb/cmanualaccessor-class.md)