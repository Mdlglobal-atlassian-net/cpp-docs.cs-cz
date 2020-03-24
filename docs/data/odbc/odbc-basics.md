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
ms.openlocfilehash: 042b1ce6d12e4f4a2be57c0e2e8e01d9750f5357
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213209"
---
# <a name="odbc-basics"></a>ODBC – základy

V tomto tématu najdete základy používání rozhraní ODBC (Open Database Connectivity):

- [Jak funguje rozhraní ODBC s databázovými třídami](../../data/odbc/odbc-and-the-database-classes.md)

- [Jak fungují ovladače rozhraní ODBC s dynamickou sadou](../../data/odbc/odbc-driver-requirements-for-dynasets.md)

- [Jaké komponenty rozhraní ODBC potřebujete k distribuci svých aplikací.](../../data/odbc/redistributing-odbc-components-to-your-customers.md)

Budete také chtít přečíst související téma [ODBC: Knihovna kurzorů rozhraní ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).

> [!NOTE]
> Zdroje dat ODBC jsou přístupné prostřednictvím tříd knihovny MFC rozhraní ODBC, jak je popsáno v tomto tématu, nebo prostřednictvím tříd DAO (Data Access Object) knihovny MFC.

> [!NOTE]
> Třídy knihovny MFC rozhraní ODBC podporují kódování Unicode a multithreading. Další informace o podpoře multithreadingu naleznete v tématu [třídy a vlákna rozhraní ODBC](../../data/odbc/odbc-classes-and-threads.md)

Rozhraní ODBC je rozhraní na úrovni volání, které umožňuje aplikacím přístup k datům v libovolné databázi, pro kterou je k dispozici ovladač ODBC. Pomocí rozhraní ODBC můžete vytvořit databázové aplikace s přístupem k libovolné databázi, pro kterou má koncový uživatel ovladač ODBC. Rozhraní ODBC poskytuje rozhraní API, které umožňuje, aby vaše aplikace byla nezávislá na systému správy zdrojových databází (DBMS).

Rozhraní ODBC je databázová část architektury Microsoft Windows Open Services (WOSA), což je rozhraní, které umožňuje aplikacím pro stolní počítače se systémem Windows připojit se k několika výpočetním prostředím bez nutnosti přepisovat aplikaci pro každou platformu.

Následují komponenty rozhraní ODBC:

- ODBC API

   Knihovna volání funkcí, sada kódů chyb a standardní syntaxe [SQL](../../data/odbc/sql.md) pro přístup k datům v systémech DBMS.

- Správce ovladačů rozhraní ODBC

   Dynamická knihovna (Odbc32. dll), která v zastoupení aplikace načítá ovladače databáze ODBC. Tato knihovna DLL je pro vaši aplikaci transparentní.

- ODBC – ovladače databáze

   Jedna nebo více knihoven DLL, které zpracovávají volání funkcí rozhraní ODBC pro konkrétní systémy DBMS. Seznam dodaných ovladačů najdete v tématu [seznam ovladačů ODBC](../../data/odbc/odbc-driver-list.md).

- [Knihovna kurzorů rozhraní ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md)

   Dynamická knihovna (ODBCCR32. dll), která se nachází mezi správcem ovladače ODBC a ovladači a zpracovává procházení dat.

- [Správce rozhraní ODBC](../../data/odbc/odbc-administrator.md)

   Nástroj, který slouží ke konfiguraci systému DBMS, aby byl dostupný jako zdroj dat pro aplikaci.

Aplikace dosahuje nezávislostí ze systémů DBMS tím, že pracuje s ovladačem ODBC zapsaným speciálně pro systém DBMS namísto práce přímo se systémem DBMS. Ovladač překládá volání do příkazů, které může použít DBMS, zjednodušuje práci vývojářů a zpřístupní ji pro nejrůznější zdroje dat.

Třídy databáze podporují libovolný zdroj dat, pro který máte ovladač ODBC. To může například zahrnovat relační databázi, databázi ISAM (s indexem), tabulku Microsoft Excel nebo textový soubor. Ovladače rozhraní ODBC spravují připojení ke zdroji dat a SQL slouží k výběru záznamů z databáze.

Seznam ovladačů rozhraní ODBC, které jsou součástí této verze sady Visual C++ , a informace o získání dalších ovladačů naleznete v tématu [seznam ovladačů rozhraní ODBC](../../data/odbc/odbc-driver-list.md).

## <a name="see-also"></a>Viz také

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
