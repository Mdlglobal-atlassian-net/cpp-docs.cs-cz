---
title: Přístup k datům v jazyce Visual C++
ms.date: 03/28/2017
helpviewer_keywords:
- Visual C++, data access applications
- databases [C++]
- OLE DB [C++], data access technologies
- data [C++], data access technologies
- data access [C++], class libraries for databases
ms.assetid: 95da6237-bbe2-480a-ae50-3a520051ceff
ms.openlocfilehash: a68c4a9df3b439ae641c5e4cbe6f3fbc8b8e6355
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222533"
---
# <a name="data-access-in-visual-c"></a>Přístup k datům v jazyce Visual C++

Téměř všechny databáze, SQL a NoSQL, a nabízejí rozhraní pro nativní aplikace C++. Standardní rozhraní odvětví je rozhraní ODBC, které podporuje všechny hlavní produkty SQL database a řada produktů NoSQL. Pro produkty jiných výrobců najdete dodavatele pro další informace. Knihovny třetích stran s různými podmínkami licence jsou také k dispozici.

Microsoft má od roku 2011 zarovnány na rozhraní ODBC jako standard pro nativní aplikace pro připojení k databázím serveru Microsoft SQL Server, v místním prostředí i v cloudu. Další informace najdete v tématu [programování přístupu dat \(MFC-ATL\)](data-access-programming-mfc-atl.md). C++/ Rozhraní příkazového řádku knihovny můžete použít buď nativních ovladačů rozhraní ODBC nebo ADO.NET. Další informace najdete v tématu [Data přístupu pomocí ADO.NET (C++vyhodnocovací)](../dotnet/data-access-using-adonet-cpp-cli.md) a [přístup k datům v sadě Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/accessing-data-in-visual-studio).

## <a name="in-this-section"></a>V tomto oddílu

[Přístup k datům programování knihovny MFC nebo ATL)](data-access-programming-mfc-atl.md)<br/>
Popisuje programování s jazykem Visual C++, kde je upřednostňovaným způsobem pomocí knihoven tříd, jako je například aktivní šablony třídy knihovny (ATL) nebo knihovny Microsoft Foundation Class (MFC), které zjednodušují práci s databází rozhraní API přístupu k datům starší verze.

[Open Database Connectivity (ODBC)](odbc/open-database-connectivity-odbc.md)<br/>
Knihovny Microsoft Foundation Classes (MFC) poskytuje třídy pro programování s připojením ODBC (Open Database).

[Programování v architektuře OLE DB](oledb/ole-db-programming.md)<br/>
Většinou starší verze rozhraní, které se stále vyžaduje v některých případech, zejména pokud jsou programové ošetření propojené servery.

## <a name="related-topics"></a>Související témata

[Připojení k SQL Database pomocí jazyka C a C++](/azure/sql-database/sql-database-develop-cplusplus-simple)<br/>
Připojení ke službě Azure SQL Database v aplikacích jazyka C nebo C++.

[Klientská knihovna pro úložiště Microsoft Azure pro jazyk C++](https://github.com/Azure/azure-storage-cpp)<br/>
[Azure Storage](/azure/storage/storage-introduction) je řešení cloudového úložiště pro moderní aplikace, které spoléhají na odolnost, dostupnost a škálovatelnost pro potřeby svých zákazníků. Připojení ke službě Azure Storage z jazyka C++ s využitím klientské knihovny Azure Storage pro C++.

[Ovladač ODBC pro SQL Server](/sql/connect/odbc/microsoft-odbc-driver-for-sql-server)<br/>
Nejnovější ovladač ODBC poskytuje robustní datové přístup k systému Microsoft SQL Server a Microsoft Azure SQL Database pro C /C++ aplikací založených na. Poskytuje podporu pro funkce, včetně funkcí always encrypted, Azure Active Directory a skupin dostupnosti AlwaysOn. Také k dispozici pro MacOS a Linux.

[Ovladač technologie OLE DB pro SQL Server](/sql/connect/oledb/oledb-driver-for-sql-server)<br/>
Nejnovější ovladače OLE DB je samostatné datové přístup aplikačního programovacího rozhraní (API), který podporuje Microsoft SQL Server a Microsoft Azure SQL Database.

[Středisko pro vývojáře v C++ a C Microsoft Azure](https://azure.microsoft.com/develop/cpp/)<br/>
Azure usnadňuje vývoj aplikací v C++ se zvýšenou flexibilitou, škálovatelností a spolehlivostí za použití oblíbených nástrojů.

[Používání úložiště Blob z jazyka C++](https://docs.microsoft.com/azure/storage/storage-c-plus-plus-how-to-use-blobs)<br/>
Azure Blob storage je služba, která ukládá Nestrukturovaná data v cloudu jako objektů BLOB. BLOB storage dokáže ukládat jakýkoli druh textu nebo binárních dat, jako je například dokument, soubor médií nebo instalační program aplikace. Úložiště objektů blob se taky označuje jako úložiště objektů.

[ Referenční informace pro programátory ODBC](https://docs.microsoft.com/sql/odbc/reference/odbc-programmer-s-reference)<br/>
Rozhraní ODBC je určen pro použití s programovací jazyk C. Použití rozhraní ODBC zahrnuje tři oblasti: Příkazy SQL, volání funkcí rozhraní ODBC a programování v jazyce C.

## <a name="see-also"></a>Viz také:

[Visual C++](../overview/visual-cpp-in-visual-studio.md)
