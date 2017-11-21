---
title: "Přístup k datům programování (MFC – knihovny ATL) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC [C++], data access applications
- databases [C++], MFC
- OLE DB [C++], data access technologies
- data [C++], data access technologies
- data access [C++], class libraries for databases
ms.assetid: def97b2c-b5a6-445f-afeb-308050fd4852
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b6a7d07941e15fad7d1b58560fb6efeb7d41c90d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="data-access-programming-mfcatl"></a>Přístup k datům programování (MFC/ATL)
V průběhu let Visual C++ poskytl několik způsobů, jak pracovat s databází. V 2011 Microsoft oznámila, že ho je zarovnání na ODBC jako upřednostňovaný technologie pro přístup k systému SQL Server produkty z nativního kódu. Rozhraní ODBC je standardní a použití získat maximální přenositelnost kódu přes více platforem a zdroje dat. Většina produktů databáze SQL a mnoho NoSQL produkty podporují ODBC. Můžete použít rozhraní ODBC přímo ve volání nízké úrovně rozhraní API ODBC, nebo můžete použít obálkové třídy knihovny MFC rozhraní ODBC nebo obálky knihovny C++ třetích stran. 

OLE DB je nízké úrovně, vysoce výkonné rozhraní API podle specifikace COM a je podporována pouze v systému Windows. Použijte OLE DB, pokud je přístup k vaší program [propojené servery](https://msdn.microsoft.com/library/ms188279.aspx). ATL poskytuje šablony technologie OLE DB, které usnadňují vytváření vlastního zprostředkovatele OLE DB a spotřebitelé. Nejnovější verzi technologie OLE DB poskytuje 11 Nativní klient SQL.  

Pokud starší verze aplikace používá pro připojení k systému SQL Server OLE DB nebo vyšší úrovně rozhraní ADO a přístup k odkazované servery nepoužíváte, zvažte migraci na rozhraní ODBC v blízké budoucnosti. Pokud nechcete, aby napříč platformami přenositelnost nebo nejnovější funkce SQL Server, můžete případně použít zprostředkovatele Microsoft OLE DB pro ODBC (MSDASQL).  MSDASQL umožňuje aplikacím, které jsou vytvořené v OLE DB a ADO (který interně používá OLEDB) pro přístup ke zdrojům dat prostřednictvím ovladače ODBC. Stejně jako u vrstvy jakékoli překlad může ovlivnit MSDASQL performace databáze. Měli byste otestovat k určení, zda dopad signifant pro vaši aplikaci. MSDASQL se dodává s verzí operačního systému Windows a Windows Server 2008 a Windows Vista SP1 se, že první Windows verzí obsahovat 64bitovou verzi technologie.

Nativní klient SQL součást (SNAC), které balíčky ovladače OLE DB a ODBC v jednom knihovny DLL, se již nepoužívá, pro aplikace rozhraní ODBC. Verze SQL Server 2012 SNAC (SQLNCLI11. Knihovny DLL) se dodává s SQL Server 2016, protože na ní závisí další součásti systému SQL Server. Však měli použít nové aplikace C++, která se připojují k systému SQL Server nebo Azure SQL Database přes rozhraní ODBC [nejnovější ovladače ODBC](https://docs.microsoft.com/en-us/sql/connect/odbc/download-odbc-driver-for-sql-server). Další informace najdete v tématu [SQL serveru Nativní klient programování](https://msdn.microsoft.com/en-us/library/ms130892.aspx)

Pokud používáte C + +/ CLI, můžete nadále používat jako vždy ADO.NET. Další informace najdete v tématu [Data Access pomocí ADO.NET (C + +/ CLI)](../dotnet/data-access-using-adonet-cpp-cli.md), a [přístup k datům v sadě Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).  
  
-   Kromě obálkové třídy rozhraní ODBC MFC také nabízí Data přístup je rozhraní DAO Obálka – třídy pro připojení k databázím přístup.  Ale DAO je zastaralé. Kód, na základě CDaoDatabase nebo CDaoRecordset je potřeba upgradovat. 

Další informace o historii technologie přístup k datům v systému Windows najdete v tématu [Microsoft Data Access Components (Wikipedia)](https://en.wikipedia.org/wiki/Microsoft_Data_Access_Components).  

## <a name="see-also"></a>Viz také  
 [Přístup k datům](data-access-in-cpp.md) [Microsoft Open Database Connectivity (ODBC)](https://docs.microsoft.com/sql/odbc/microsoft-open-database-connectivity-odbc) [technologie silniční mapu jako přístup k datům](https://msdn.microsoft.com/en-us/library/ms810810.aspx)