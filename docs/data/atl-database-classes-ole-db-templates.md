---
title: ATL – databázové třídy (šablony technologie OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE DB templates [C++], ATL database classes
- database classes [C++], OLE DB
- database classes [C++], ATL
ms.assetid: 219766aa-e18a-405f-9e36-d7a0fdb31b2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fabced79232d17807d252da9dac5b066ddf69f25
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089049"
---
# <a name="atl-database-classes-ole-db-templates"></a>Databázové třídy ATL (šablony OLE DB)
Společnost Microsoft poskytuje několik implementace technologie OLE DB, sadu rozhraní modelu COM, které poskytuje jednotný přístup k datům v různých informačních zdrojů a formáty.  OLE DB je oficiálně zastaralé; Tato dokumentace je pro vývojáře, kteří jsou zachování starší verze kódu. Nové aplikace měla použít rozhraní ODBC pro připojení ke zdrojům dat SQL.
  
 Šablony technologie OLE DB se šablonami C++ v ATL, které usnadňují použití tím, že poskytuje třídy, které implementují mnoho běžně používaných rozhraní OLE DB databázové technologie OLE DB.  
  
 Tato knihovna šablon obsahuje dvě části:  
  
-   [Šablony příjemce technologie OLE DB](../data/oledb/ole-db-consumer-templates-cpp.md) použít k implementaci aplikace klienta (příjemce) technologie OLE DB.  
  
-   [Šablony zprostředkovatele technologie OLE DB](../data/oledb/ole-db-provider-templates-cpp.md) použít k implementaci aplikace serveru (zprostředkovatel) technologie OLE DB.  
  
 Kromě toho [atributy příjemce technologie OLE DB](../windows/ole-db-consumer-attributes.md) poskytují pohodlný způsob pro vytváření OLE DB. Atributy technologie OLE DB vloží kód podle šablony příjemce technologie OLE DB pro vytváření pracovních OLE DB.  
  
 Všimněte si, že knihovna MFC obsahuje jednu třídu, [COleDBRecordView](../mfc/reference/coledbrecordview-class.md), který zobrazí záznamů databáze v ovládacích prvcích. Zobrazení je přímo připojený k zobrazení formuláře `CRowset` objektu a zobrazí pole `CRowset` objektu v ovládacích prvcích šablony dialogového okna.  
  
 Další informace najdete v tématu [programování technologie OLE DB](../data/oledb/ole-db-programming.md) a [OLE DB – Příručka pro vývojáře](http://go.microsoft.com/fwlink/p/?linkid=121548).  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření příjemce technologie OLE DB](../data/oledb/creating-an-ole-db-consumer.md)   
 [Vytvoření zprostředkovatele OLE DB](../data/oledb/creating-an-ole-db-provider.md)   
 [Referenční dokumentace šablony příjemců OLE DB](../data/oledb/ole-db-consumer-templates-reference.md)   
 [Referenční dokumentace šablony zprostředkovatele OLE DB](../data/oledb/ole-db-provider-templates-reference.md)   
 [Ukázky šablon OLE DB](http://msdn.microsoft.com/en-us/08958863-0b5f-41ad-ae99-fca7440c553c)