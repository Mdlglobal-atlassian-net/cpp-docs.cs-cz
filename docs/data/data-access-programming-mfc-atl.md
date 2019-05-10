---
title: Přístup k datům programování (MFC-ATL)
ms.date: 11/16/2018
helpviewer_keywords:
- MFC [C++], data access applications
- databases [C++], MFC
- OLE DB [C++], data access technologies
- data [C++], data access technologies
- data access [C++], class libraries for databases
ms.assetid: def97b2c-b5a6-445f-afeb-308050fd4852
ms.openlocfilehash: e71e16bef29239e0c6a391b2d5e2129042cd52fa
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221842"
---
# <a name="data-access-programming-mfcatl"></a>Přístup k datům programování knihovny MFC nebo ATL)

V průběhu let Visual C++ poskytuje několik způsobů, jak pracovat s databází. V roce 2011 společnost Microsoft oznámila, že ho jako preferované technologie pro přístup k systému SQL Server produkty z nativního kódu je zarovnání na připojení ODBC (Open Database). ODBC je oborový standard, a pomocí něj získat maximální přenositelnost kódu nad velkým množstvím platforem a zdroje dat. Většinu produktů, které databáze SQL a NoSQL výrobky podpora rozhraní ODBC. Rozhraní ODBC můžete použít přímo pomocí volání rozhraní ODBC API nízké úrovně, nebo můžete použít obálkové třídy knihovny MFC rozhraní ODBC nebo knihovny třetích stran obálky C++.

OLE DB je nízké úrovně, vysoce výkonné rozhraní API podle specifikace modelu COM a je podporován pouze na Windows. Použít technologie OLE DB, pokud je přístup k programu [propojené servery](/sql/relational-databases/linked-servers/linked-servers-database-engine). Knihovna ATL poskytuje šablony technologie OLE DB, které usnadňují vytvářel Vlastní zprostředkovatelé technologie OLE DB a spotřebitele. Aktuální zprostředkovatel pro Microsoft SQL Server najdete v dokumentaci k [ovladač technologie OLE DB pro SQL Server](/sql/connect/oledb/oledb-driver-for-sql-server).

## <a name="porting-data-applications"></a>Přenos datových aplikací

Pokud starší aplikace používá technologie OLE DB nebo vyšší úrovně rozhraní ADO pro připojení k serveru SQL Server, měli byste zvážit, migrace na nejnovější verzi [ovladač technologie OLE DB pro SQL Server](/sql/connect/oledb/oledb-driver-for-sql-server) aby bylo možné využívat nejnovější funkce SQL Server. Další možnost, pokud požadujete přenositelnost napříč platformami nebo nejnovější funkce SQL serveru, pravděpodobně můžete zprostředkovatele Microsoft OLE DB pro rozhraní ODBC (MSDASQL).  MSDASQL umožňuje aplikacím, které jsou postavené na technologie OLE DB a ADO (který interně používá OLEDB) pro přístup ke zdrojům dat prostřednictvím ovladače rozhraní ODBC. Stejně jako u jakékoli transakční vrstva MSDASQL může ovlivnit výkon databáze. Měli byste otestovat zjistit, jestli dopad je důležité pro vaši aplikaci. MSDASQL se dodává s operačním systémem Windows a Windows Server 2008 a Windows Vista SP1 se že první Windows verze na 64bitovou verzi technologie patří.

Pokud vaše C++ aplikace se připojí k serveru SQL Server nebo databázi SQL Azure pomocí rozhraní ODBC, měla by používat [nejnovější ovladač ODBC](/sql/connect/odbc/download-odbc-driver-for-sql-server).

Pokud používáte C++/rozhraní příkazového řádku, můžete nadále používat jako vždy ADO.NET. Další informace najdete v tématu [Data přístupu pomocí ADO.NET (C++vyhodnocovací)](../dotnet/data-access-using-adonet-cpp-cli.md), a [přístup k datům v sadě Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).

- Kromě obálkové třídy ODBC MFC také poskytuje obálkové třídy objektů DAO (Data Access) pro připojení k přístupu k databázím.  Rozhraní DAO, ale je zastaralé. Jakýkoli kód, na základě CDaoDatabase nebo CDaoRecordset by měl upgradovat.

Další informace o historii technologií přístupu k datům v Microsoft Windows najdete v tématu [Microsoft Data Access Components (Wikipedia)](https://en.wikipedia.org/wiki/Microsoft_Data_Access_Components).

## <a name="see-also"></a>Viz také:

[Přístup k datům](data-access-in-cpp.md)<br/>
[Připojení k databázi Microsoft Open (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc)<br/>
