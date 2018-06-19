---
title: OLE DB – programování | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB [C++]
- data access [C++], OLE DB programming
- OLE DB [C++], about OLE DB
ms.assetid: 52a80d66-17a9-43a1-9b90-392ae43cea2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fb77c5b7d7f6de91f74e83c395d0fcc13ebf70e0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33107175"
---
# <a name="ole-db-programming"></a>OLE DB – programování
Microsoft OLE DB je starší verze technologie; pro nové aplikace je požadovaná data přístup k rozhraní API pro odkazované servery SQL. Všechny ostatní nové aplikace by měly použití rozhraní ODBC. Aktuální zprostředkovatel OLE DB pro SQL Server je SQLNCLI11. KNIHOVNY DLL. Zprostředkovatel je stále přesouvání v SQL serveru 2016. Tato dokumentace je určena pro vývojáře, kteří jsou zachování existující aplikace, které už používají OLE DB.
  
 Šablony technologie OLE DB jsou C++ šablony, které usnadňují databázové technologie OLE DB vysoce výkonné použití tím, že poskytuje třídy, které implementují mnoha běžně používaných rozhraní OLE DB. Tato knihovna šablon je rozdělené do šablony příjemce a šablony zprostředkovatele.  
  
 Visual C++ má také podpora průvodce pro vytváření aplikací OLE DB starter.  
  
 Kromě toho můžete atributy implementovat šablony příjemce technologie OLE DB.  
  
|Další informace o|Další informace naleznete v tématu|  
|-------------------------|---------|  
|Pomocí šablony příjemce technologie OLE DB (koncepční témata)|[Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)|  
|Pomocí šablony zprostředkovatele technologie OLE DB (koncepční témata)|[Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)|  
|Třídy šablony technologie OLE DB a makra|[Referenční dokumentace šablony OLE DB](../../data/oledb/ole-db-templates.md) (Visual C++)|  
|Atributy příjemce technologie OLE DB|[Atributy příjemce technologie OLE DB](../../windows/ole-db-consumer-attributes.md)|  
|Rozhraní OLE DB|[Referenční informace pro programátory OLE DB](https://msdn.microsoft.com/en-us/library/ms713643.aspx) (ve Windows SDK)|  
|Ukázky šablon OLE DB|[Ukázky šablon OLE DB](http://msdn.microsoft.com/en-us/08958863-0b5f-41ad-ae99-fca7440c553c)| 
|Přístup k datům programování – přehled (Visual C++)|[Programování pro přístup k datům](../../data/data-access-programming-mfc-atl.md)|  
|Koncepční témata rozhraní ODBC|[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)|  

  
## <a name="see-also"></a>Viz také  
 [Přístup k datům](../data-access-in-cpp.md)