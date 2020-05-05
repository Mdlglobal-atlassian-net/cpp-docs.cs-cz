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
ms.openlocfilehash: 42c36259b14a7f0341e383bb3a7f2760bab165aa
ms.sourcegitcommit: fcc3aeb271449f8be80348740cffef39ba543407
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2020
ms.locfileid: "82538585"
---
# <a name="data-access-in-visual-c"></a>Přístup k datům v jazyce Visual C++

Prakticky všechny databázové produkty, SQL a NoSQL poskytují rozhraní pro nativní aplikace v jazyce C++. Oborové standardní rozhraní je rozhraní ODBC, které podporuje všechny hlavní produkty SQL Database a mnoho NoSQLch produktů. V případě produktů jiných výrobců se obraťte na dodavatele, kde najdete další informace. K dispozici jsou také knihovny třetích stran s různými licenčními podmínkami.

Od 2011 Společnost Microsoft zarovnává rozhraní ODBC jako standard pro nativní aplikace pro připojení k Microsoft SQL Server databázím v místním prostředí i v cloudu. Další informace naleznete v tématu [programování \(přístupu k datům MFC –\)ATL](data-access-programming-mfc-atl.md). Knihovny C++/CLI můžou používat buď nativní ovladače ODBC, nebo ADO.NET. Další informace najdete v tématech [přístup k datům pomocí ADO.NET (C++/CLI)](../dotnet/data-access-using-adonet-cpp-cli.md) a [přístup k datům v aplikaci Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/accessing-data-in-visual-studio).

## <a name="in-this-section"></a>V tomto oddílu

[Programování přístupu k datům (MFC/ATL)](data-access-programming-mfc-atl.md)<br/>
Popisuje programování starších verzí pro přístup k datům pomocí Visual C++, kde preferovaným způsobem je použití jedné z knihoven tříd, jako je knihovna ATL (Active Template Class Library) nebo knihovna MFC (Microsoft Foundation Class), která zjednodušuje práci s databázovými rozhraními API.

[Připojení Open Database (ODBC)](odbc/open-database-connectivity-odbc.md)<br/>
Knihovna Microsoft Foundation Classes (MFC) poskytuje třídy pro programování s rozhraním ODBC (Open Database Connectivity).

[OLE DB – programování](oledb/ole-db-programming.md)<br/>
Většinou starší verze rozhraní, které je v některých scénářích stále potřeba, konkrétně při programování proti odkazovaným serverům.

## <a name="related-topics"></a>Související témata

[Připojení k SQL Database pomocí jazyka C a C++](/azure/sql-database/sql-database-develop-cplusplus-simple)<br/>
Připojení k Azure SQL Database z aplikací v jazyce C nebo C++.

[Klientská knihovna Microsoft Azure Storage pro C++](https://github.com/Azure/azure-storage-cpp)<br/>
[Azure Storage](/azure/storage/common/storage-introduction) je řešení cloudového úložiště pro moderní aplikace, které spoléhají na odolnost, dostupnost a škálovatelnost, aby splňovaly potřeby svých zákazníků. Připojte se k Azure Storage z jazyka C++ pomocí Azure Storage klientské knihovny pro C++.

[Ovladač ODBC pro SQL Server](/sql/connect/odbc/microsoft-odbc-driver-for-sql-server)<br/>
Nejnovější ovladač ODBC poskytuje robustní přístup k datům Microsoft SQL Server a Microsoft Azure SQL Database pro aplikace založené na jazyce C/C++. Poskytuje podporu pro funkce, včetně vždycky šifrovaných, Azure Active Directory a Skupiny dostupnosti AlwaysOn. K dispozici také pro MacOS a Linux.

[OLE DB ovladače pro SQL Server](/sql/connect/oledb/oledb-driver-for-sql-server)<br/>
Nejnovější ovladač OLE DB je samostatné rozhraní API pro přístup k datům, které podporuje Microsoft SQL Server a Microsoft Azure SQL Database.

[Microsoft Azure středisko pro vývojáře v jazyce C a C++](https://azure.microsoft.com/develop/cpp/)<br/>
Azure usnadňuje sestavování aplikací C++ se zvýšenou flexibilitou, škálovatelností a spolehlivostí pomocí nástrojů, které máte rádi.

[Použití Blob Storage z C++](https://docs.microsoft.com/azure/storage/storage-c-plus-plus-how-to-use-blobs)<br/>
Úložiště objektů blob v Azure je služba, která ukládá nestrukturovaná data v cloudu jako objekty nebo objekty blob. Do Blob storage se dá ukládat jakýkoli druh textu nebo binárních dat, jako je dokument, soubor médií nebo instalátor aplikace. Blob storage se také nazývá úložiště objektů.

[Reference programátora ODBC](https://docs.microsoft.com/sql/odbc/reference/odbc-programmer-s-reference)<br/>
Rozhraní ODBC je určené pro použití s programovacím jazykem C. Použití rozhraní ODBC zahrnuje tři oblasti: příkazy SQL, volání funkcí rozhraní ODBC a programování v jazyce C.

## <a name="see-also"></a>Viz také

[C++ v aplikaci Visual Studio](../overview/visual-cpp-in-visual-studio.md)
