---
title: "Přístup k datům v jazyce Visual C++ | Microsoft Docs"
ms.custom: 
ms.date: 03/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, data access applications
- databases [C++]
- OLE DB [C++], data access technologies
- data [C++], data access technologies
- data access [C++], class libraries for databases
ms.assetid: 95da6237-bbe2-480a-ae50-3a520051ceff
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: eaefb5f3ed8bd0c586e42527d47918dbb0dd5a57
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="data-access-in-visual-c"></a>Přístup k datům v jazyce Visual C++

Téměř všechny produkty databáze SQL a NoSQL, poskytují rozhraní pro nativních aplikací C++. Standardní rozhraní odvětví je ODBC, který nepodporuje všechny produkty hlavní databáze SQL a mnoho NoSQL produkty. Pro produkty Microsoft získáte od výrobce pro další informace. Knihovny třetích stran s různými licenční podmínky jsou k dispozici.

Vzhledem k tomu, že 2011 Microsoft má zarovnán na ODBC jako standardní pro nativní aplikace pro připojení k databázím serveru Microsoft SQL Server, jak místně a v cloudu. Další informace najdete v tématu [programovací přístup dat \(MFC ATL\)](data-access-programming-mfc-atl.md). C + +/ CLI knihovny můžete použít buď nativní ODBC – ovladače nebo ADO.NET. Další informace najdete v tématu [Data Access pomocí ADO.NET (C + +/ CLI)](/dotnet/data-access-using-adonet-cpp-cli.md) a [přístup k datům v sadě Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/accessing-data-in-visual-studio).

## <a name="in-this-section"></a>V tomto oddílu
[Data přístup programování (MFC/ATL)](data-access-programming-mfc-atl.md) popisuje starší data přístup k programování s Visual C++, kde je upřednostňovaný způsob použít jednu z knihovny tříd jako aktivní šablony třídy knihovny (ATL) nebo knihovna Microsoft Foundation Class (MFC), které zjednodušují práci s databází rozhraní API.

[Otevřete připojení k databázi (ODBC)](odbc/open-database-connectivity-odbc.md) knihovna Microsoft Foundation třídy (MFC) poskytuje třídy pro programování s připojením ODBC (Open Database).

[Programování technologie OLE DB](oledb/ole-db-programming.md) většinou starší verze rozhraní, což je stále nutné v některých scénářích, konkrétně v případě, že jsou programové ošetření propojené servery.

## <a name="related-topics"></a>Související témata
[Připojit k databázi SQL pomocí C a C++](/azure/sql-database/sql-database-develop-cplusplus-simple) připojit k databázi SQL Azure z aplikací jazyka C nebo C++.

[Microsoft Azure Klientská knihovna pro úložiště pro jazyk C++](https://github.com/Azure/azure-storage-cpp)
[Azure Storage](/azure/storage/storage-introduction) je řešení cloudového úložiště pro moderní aplikace, které jsou závislé na odolnost, dostupnost a škálovatelnost, aby splňovaly potřeby jejich Zákazníci. Připojte k úložišti Azure z jazyka C++ pomocí klientské knihovny pro úložiště Azure pro jazyk C++.

[13.1 ovladač ODBC pro SQL Server – vydání Windows](https://blogs.msdn.microsoft.com/sqlnativeclient/2016/08/01/announcing-the-odbc-driver-13-1-for-sql-server) nejnovější ovladače ODBC pro C/C++ na základě aplikací poskytuje robustní data přístup k Microsoft SQL Server 2016 Microsoft Azure SQL Database. Poskytuje podporu pro funkce, včetně vždycky šifrovaná, Azure Active Directory a skupiny dostupnosti AlwaysOn. Dostupné taky pro systému MacOS a Linux.     
 
[SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client-programming) SQL Server Native Client je samostatné data přístupu aplikace programovací rozhraní (API), použít pro OLE DB a rozhraní ODBC, který podporuje SQL Server 2005 prostřednictvím SQL Server 2014. Nové aplikace by měly používat 13.1 ovladač ODBC systému SQL Server.

[Microsoft Azure C a C++ Developer Center](https://azure.microsoft.com/develop/cpp/) Azure usnadňuje vytváření aplikací C++ s vyšší flexibilitu, škálovatelnost a spolehlivost pomocí nástrojů, které vám rádi.    

[Používání úložiště Blob z jazyka C++](https://docs.microsoft.com/azure/storage/storage-c-plus-plus-how-to-use-blobs) Azure Blob storage je služba, která ukládá Nestrukturovaná data v cloudu jako objekty nebo objekty BLOB. Úložiště objektů BLOB můžete ukládat jakýkoli typ textu nebo binárních dat, jako je například dokument, soubor média nebo instalační program aplikace. Úložiště objektů blob se také označuje jako úložiště objektů.

[Referenční informace pro programátory ODBC](https://docs.microsoft.com/sql/odbc/reference/odbc-programmer-s-reference) rozhraní ODBC je určen k použití pomocí programovacího jazyka C. Použití rozhraní ODBC zahrnuje tři oblasti: příkazy SQL, rozhraní ODBC funkce volání a C programování.

## <a name="see-also"></a>Viz také
[Visual C++](../visual-cpp-in-visual-studio.md)
