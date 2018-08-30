---
title: OLE DB – programování | Dokumentace Microsoftu
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
ms.openlocfilehash: 5d5804a7437dabd688abab04ebdd50a79decbaaa
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43198766"
---
# <a name="ole-db-programming"></a>OLE DB – programování
Microsoft OLE DB je starou technologií; pro nové aplikace je požadovaná data přístup k rozhraní API pro propojené servery SQL. Všechny nové aplikace by měl použití rozhraní ODBC. Aktuální zprostředkovatel OLE DB pro SQL Server je SQLNCLI11. KNIHOVNY DLL. Zprostředkovatel se stále dodává v SQL serveru 2016. Tato dokumentace je určená pro vývojáře, kteří jsou udržování existujících aplikací, které už používají OLE DB.
  
 Šablony technologie OLE DB jsou šablony jazyka C++, které usnadňují databázové technologie OLE DB výkonné použití tím, že poskytuje třídy, které implementují mnoho běžně používaných rozhraní OLE DB. Tato knihovna šablon je rozdělen na poskytovatele šablony a – šablony příjemce.  
  
 Visual C++ obsahuje také podpora průvodce pro vytváření aplikací OLE DB starter.  
  
 Kromě toho můžete použít atributy k implementaci šablony příjemců OLE DB.  
  
|Další informace o|Další informace naleznete v tématu|  
|-------------------------|---------|  
|Pomocí šablony příjemce technologie OLE DB (koncepční témata)|[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)|  
|Pomocí šablony zprostředkovatele OLE DB (koncepční témata)|[Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)|  
|Třídy šablon technologie OLE DB a makra|[Referenční dokumentace k šablonám OLE DB](../../data/oledb/ole-db-templates.md) (Visual C++)|  
|Atributy příjemce technologie OLE DB|[Atributy příjemce technologie OLE DB](../../windows/ole-db-consumer-attributes.md)|  
|Rozhraní technologie OLE DB|[Referenční informace pro programátory OLE DB](/previous-versions/windows/desktop/ms713643\(v=vs.85\)) (v sadě Windows SDK)|  
|Ukázky šablon technologie OLE DB|[OLE DB – Ukázky šablon](https://msdn.microsoft.com/08958863-0b5f-41ad-ae99-fca7440c553c)| 
|Přístup k datům programování přehled (Visual C++)|[Programování přístupu k datům](../../data/data-access-programming-mfc-atl.md)|  
|Koncepční témata ODBC|[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)|  

## <a name="see-also"></a>Viz také  
 [Přístup k datům](../data-access-in-cpp.md)