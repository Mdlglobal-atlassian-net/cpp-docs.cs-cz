---
title: Přenos datových aplikací | Dokumentace Microsoftu
ms.custom: ''
ms.date: 05/12/2017
ms.technology:
- devlang-cpp
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], data access applications
- databases [C++], MFC
- OLE DB [C++], data access technologies
- data [C++], data access technologies
- data access [C++], class libraries for databases
ms.assetid: 8d10c285-c13f-4e6e-a09e-5ee0f2666b44
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 51b041c60cd1bb8f866a6174e3cbb41ad613acc0
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078164"
---
# <a name="porting-data-applications"></a>Přenos datových aplikací
V průběhu let Visual C++ poskytuje několik způsobů, jak pracovat s databází. V roce 2011 společnost Microsoft oznámila, že to je zarovnání na rozhraní ODBC jako preferované technologie pro přístup k systému SQL Server produkty z nativního kódu. ODBC je oborový standard, a pomocí něj získat maximální přenositelnost kódu nad velkým množstvím platforem a zdroje dat. Většinu produktů, které databáze SQL a NoSQL výrobky podpora rozhraní ODBC. Rozhraní ODBC můžete použít přímo pomocí volání rozhraní ODBC API nízké úrovně, nebo můžete použít obálkové třídy knihovny MFC rozhraní ODBC nebo knihovny třetích stran obálky C++.

OLE DB je nízké úrovně, vysoce výkonné rozhraní API podle specifikace modelu COM a je podporován pouze na Windows. Použít technologie OLE DB, pokud je přístup k programu [propojené servery](/sql/relational-databases/linked-servers/linked-servers-database-engine). Knihovna ATL poskytuje šablony technologie OLE DB, které usnadňují vytvářel Vlastní zprostředkovatelé technologie OLE DB a spotřebitele. Překopírujte nejnovější verzi technologie OLE DB poskytuje nativní klient 11 SQL.

Pokud se starší verzí aplikace používá pro připojení k serveru SQL Server OLE DB nebo vyšší úrovně rozhraní ADO a přístup k odkazované servery nepoužíváte, měli byste zvážit, migrace do rozhraní ODBC v blízké budoucnosti. Pokud nechcete, aby přenositelnost napříč platformami nebo nejnovější funkce SQL Server, případně můžete zprostředkovatele Microsoft OLE DB pro rozhraní ODBC (MSDASQL).  MSDASQL umožňuje aplikacím, které jsou postavené na technologie OLE DB a ADO (který interně používá OLEDB) pro přístup ke zdrojům dat prostřednictvím ovladače rozhraní ODBC. Stejně jako u jakékoli transakční vrstva MSDASQL může mít vliv na snížený výkon databáze. Měli byste otestovat k určení, zda se signifant pro vaši aplikaci. MSDASQL se dodává s operačním systémem Windows a Windows Server 2008 a Windows Vista SP1 se že první Windows verze na 64bitovou verzi technologie patří.

Komponentu Nativní klient systému SQL (SNAC), které balíčky OLE DB a ovladače ODBC v jedné knihovně DLL, je zastaralé pro aplikace rozhraní ODBC. Verze systému SQL Server 2012 SNAC (SQLNCLI11. Knihovny DLL) se dodává s SQL Server 2016, protože na ní závisí další součásti systému SQL Server. Však měli použít nové aplikace C++, které se připojují k systému SQL Server nebo databázi SQL Azure pomocí rozhraní ODBC [nejnovější ovladač ODBC](/sql/connect/odbc/download-odbc-driver-for-sql-server). Další informace najdete v tématu [SQL Server nativního klienta programování](/sql/relational-databases/native-client/sql-server-native-client-programming)

Pokud používáte C + +/ CLI, které můžete dál používat ADO.NET jako vždy. Další informace najdete v tématu [Data přístupu pomocí ADO.NET (C + +/ CLI)](../dotnet/data-access-using-adonet-cpp-cli.md), a [přístup k datům v sadě Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).

- Kromě obálkové třídy ODBC MFC také poskytuje přístup objektů DAO (Data) obálkové třídy pro připojení k přístupu k databázím.  Rozhraní DAO, ale je zastaralé. Na základě jakéhokoli kódu `CDaoDatabase` nebo `CDaoRecordset` by měl být upgradovány.

Další informace o historii technologií přístupu k datům v Microsoft Windows najdete v tématu [Microsoft Data Access Components (Wikipedia)](https://en.wikipedia.org/wiki/Microsoft_Data_Access_Components).

## <a name="see-also"></a>Viz také

[Přístup k datům v jazyce Visual C++](../data/data-access-in-cpp.md)<br/>
[Připojení k databázi Microsoft Open (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc)<br/>
[Data Access technologie podrobný popis](https://msdn.microsoft.com/library/ms810810.aspx)