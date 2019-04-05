---
title: ODBC – základy
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC cursor library [ODBC], ODBC components
- ODBC components
- ODBC components, required components
- ODBC, about ODBC
- ODBC, components
ms.assetid: ec529702-0fb2-4754-b8de-d1efa8eca18f
ms.openlocfilehash: e14f5d051b9684cd79a34f5fb50feeb785d2f927
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59033238"
---
# <a name="odbc-basics"></a>ODBC – základy

Toto téma obsahuje základní informace o připojení ODBC (Open Database):

- [Způsob práce s databázovými třídami rozhraní ODBC](../../data/odbc/odbc-and-the-database-classes.md)

- [Možnosti ovladače rozhraní ODBC pro práci s dynamické sady](../../data/odbc/odbc-driver-requirements-for-dynasets.md)

- [Jaké součástí rozhraní ODBC budete muset znovu distribuovat s vašimi aplikacemi](../../data/odbc/redistributing-odbc-components-to-your-customers.md)

Budete také chtít přečíst související téma [ODBC: Knihovna kurzorů rozhraní ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).

> [!NOTE]
> Zdroje dat rozhraní ODBC jsou přístupné prostřednictvím třídy knihovny MFC rozhraní ODBC, jak je popsáno v tomto tématu, nebo třídy knihovny MFC objekt DAO (Data Access).

> [!NOTE]
> Třídy knihovny MFC rozhraní ODBC podporu kódování Unicode a multithreadingu. Další informace o podpoře multithreadingu naleznete v tématu [ODBC – třídy a vlákna](../../data/odbc/odbc-classes-and-threads.md)

ODBC je úroveň volání rozhraní, které umožňuje aplikacím přistupovat k datům v jakékoli databázi, pro kterou je ovladač rozhraní ODBC. Pomocí rozhraní ODBC, můžete vytvořit databázových aplikací s přístupem k jakékoli databázi, pro kterou má koncový uživatel ovladač rozhraní ODBC. ODBC poskytuje rozhraní API, která umožňuje vaší aplikaci, která bude nezávisle na zdrojový systém správy databáze (DBMS).

ODBC je část databáze systému Microsoft Windows otevřete služby architektury (WOSA), což je rozhraní, které umožňuje založené na Windows desktopových aplikací pro připojení k více výpočetní prostředí bez přepsání aplikace pro každou platformu.

Tady jsou součástí rozhraní ODBC:

- ODBC API

   Knihovna volání funkcí, sada kódů chyb a standardní [SQL](../../data/odbc/sql.md) syntaxi pro přístup k datům v systémech DBMS.

- Správce ovladačů ODBC

   Dynamická knihovna (Odbc32.dll), který načte ovladače rozhraní ODBC databáze jménem aplikace. Tato knihovna DLL je transparentní pro vaši aplikaci.

- Databáze ovladače rozhraní ODBC

   Jeden nebo více knihovny DLL, které zpracovávají volání funkcí rozhraní ODBC pro konkrétní systémy DBMS. Seznam dodaných ovladačů najdete v tématu [seznam ovladačů ODBC](../../data/odbc/odbc-driver-list.md).

- [Knihovna kurzorů rozhraní ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md)

   Dynamickou knihovnu (Odbccr32.dll), který se nachází mezi správcem ovladačů rozhraní ODBC a ovladači a zpracování dat posouvání.

- [Správce rozhraní ODBC](../../data/odbc/odbc-administrator.md)

   Nástroj, který se používá ke konfiguraci DBMS, aby byla k dispozici jako zdroj dat pro aplikaci.

Aplikace dosáhne nezávislost na systémy DBMS pracovní prostřednictvím ovladače rozhraní ODBC psány konkrétně pro DBMS spíše než práci přímo s DBMS. Ovladač překládá volání na příkazy jeho DBMS můžete zjednodušit práci pro vývojáře a zpřístupnění pro širokou škálu zdrojů dat.

Databázové třídy podporu libovolný zdroj dat, pro který máte ovladač rozhraní ODBC. Například to může zahrnovat relační databázi, databázi indexované sekvenční přístup – metoda (ISAM), tabulky Microsoft Excel nebo textový soubor. ODBC – ovladače spravovat připojení ke zdroji dat a SQL slouží k výběru záznamů z databáze.

Seznam ovladačů ODBC zahrnuté v této verzi systému Visual C++ a informace o získání dalších ovladačů najdete v tématu [seznam ovladačů ODBC](../../data/odbc/odbc-driver-list.md).

## <a name="see-also"></a>Viz také:

[ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)