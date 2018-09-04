---
title: ATL – databázové třídy (šablony technologie OLE DB) | Dokumentace Microsoftu
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
ms.openlocfilehash: 6df13353b61347455cc5d707f099086429d46f6f
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43677866"
---
# <a name="atl-database-classes-ole-db-templates"></a>Databázové třídy ATL (šablony OLE DB)
Společnost Microsoft poskytuje několik implementace technologie OLE DB, sadu rozhraní modelu COM, které poskytují jednotný přístup k datům v rozličnými zdroji informací a formátů.  OLE DB je oficiálně zastaralé; Tato dokumentace je pro vývojáře, kteří jsou zachování starší verze kódu. Nové aplikace měla použít pro připojení ke zdrojům dat SQL ODBC.
  
 Šablony technologie OLE DB jsou šablony C++ v ATL, které usnadňují použití tím, že poskytuje třídy, které implementují mnoho běžně používaných rozhraní OLE DB databázové technologie OLE DB.  
  
 Tato šablona knihovny obsahuje dvě části:  
  
-   [OLE DB – šablony příjemce](../data/oledb/ole-db-consumer-templates-cpp.md) používaný k implementaci aplikace klienta (příjemce) technologie OLE DB.  
  
-   [Šablony zprostředkovatele OLE DB](../data/oledb/ole-db-provider-templates-cpp.md) používaný k implementaci aplikace serveru (poskytovatel) technologie OLE DB.  
  
 Kromě toho [atributy příjemce technologie OLE DB](../windows/ole-db-consumer-attributes.md) poskytují pohodlný způsob, jak vytvořit příjemci knihovny OLE DB. OLE DB atributy vloží kód založený na šablony příjemců OLE DB pro vytváření pracovních technologie OLE DB.  
  
 Všimněte si, že knihovna MFC obsahuje jednu třídu, [COleDBRecordView](../mfc/reference/coledbrecordview-class.md), který zobrazuje záznamy databáze v ovládacích prvcích. Zobrazení je připojený přímo k zobrazení formuláře `CRowset` který zobrazuje pole `CRowset` objektu v ovládacích prvcích šablony dialogového okna.  
  
 Další informace najdete v tématu [programování technologie OLE DB](../data/oledb/ole-db-programming.md) a [Příručka programátora technologie OLE DB](/previous-versions/windows/desktop/ms713643\(v=vs.85\)).  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření příjemce technologie OLE DB](../data/oledb/creating-an-ole-db-consumer.md)   
 [Vytvoření zprostředkovatele OLE DB](../data/oledb/creating-an-ole-db-provider.md)   
 [Reference šablony příjemce technologie OLE DB](../data/oledb/ole-db-consumer-templates-reference.md)   
 [Reference šablon zprostředkovatele OLE DB](../data/oledb/ole-db-provider-templates-reference.md)   
 [OLE DB – Ukázky šablon](https://github.com/Microsoft/VCSamples)