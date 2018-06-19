---
title: ODBC – základy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC cursor library [ODBC], ODBC components
- ODBC components
- ODBC components, required components
- ODBC, about ODBC
- ODBC, components
ms.assetid: ec529702-0fb2-4754-b8de-d1efa8eca18f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 69b3694292171f00e03cdb941def27fd9e8ffc84
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090296"
---
# <a name="odbc-basics"></a>ODBC – základy
Toto téma obsahuje základní informace o připojení ODBC (Open Database):  
  
-   [Způsob práce s třídami databází rozhraní ODBC](../../data/odbc/odbc-and-the-database-classes.md)  
  
-   [Možnosti ovladače ODBC pro práci s dynamické sady](../../data/odbc/odbc-driver-requirements-for-dynasets.md)  
  
-   [Jaké součásti ODBC, budete muset znovu distribuovat s vašimi aplikacemi](../../data/odbc/redistributing-odbc-components-to-your-customers.md)  
  
 Budete také chtít přečíst téma související [ODBC: knihovny kurzorů ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).  
  
> [!NOTE]
>  Zdroje dat ODBC jsou přístupné prostřednictvím třídy knihovny MFC rozhraní ODBC, jak je popsáno v tomto tématu nebo třídy MFC objekt DAO (Data Access).  
  
> [!NOTE]
>  Třídy MFC rozhraní ODBC podporují kódování Unicode a více vláken. Další informace o podpoře multithreadingu najdete v tématu [ODBC – třídy a vlákna](../../data/odbc/odbc-classes-and-threads.md)  
  
 Rozhraní ODBC je rozhraní úrovně volání, které umožňuje aplikacím přístup k datům v všechny databáze, pro kterou je ovladač ODBC. Pomocí rozhraní ODBC, můžete vytvořit databázové aplikace s přístupem k jakékoli databázi, pro které má váš koncový uživatel ovladače ODBC. ODBC poskytuje rozhraní API, která umožňuje aplikacím za nezávislé zdrojového systému správy databáze (databázového systému).  
  
 Rozhraní ODBC je část databáze systému Microsoft Windows otevřete služby architektura (WOSA), což je rozhraní, které umožňuje založené na Windows aplikací klasické pracovní plochy pro připojení k několika výpočetních prostředí bez přepsání aplikace pro každou platformu.  
  
 Tady jsou součástí rozhraní ODBC:  
  
-   ROZHRANÍ API ODBC  
  
     Knihovna funkce volá sadu kódy chyb a standard [SQL](../../data/odbc/sql.md) syntaxe pro přístup k datům v systémech DBMS.  
  
-   Správce ovladačů ODBC  
  
     Dynamická knihovna (Odbc32.dll), který načítá ovladače ODBC databáze jménem aplikace. Je transparentní pro vaše aplikace tuto knihovnu DLL.  
  
-   ODBC – ovladače databáze  
  
     Jeden nebo více knihovny DLL, které zpracovávají volání funkcí rozhraní ODBC pro konkrétní systémy DBMS. Seznam dodaných ovladačů najdete v tématu [seznam ovladačů ODBC](../../data/odbc/odbc-driver-list.md).  
  
-   [Knihovna kurzorů rozhraní ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md)  
  
     Dynamická knihovna (Odbccr32.dll), který se nachází mezi správce ovladačů ODBC a ovladače a zpracování posouvání data.  
  
-   [Správce rozhraní ODBC](../../data/odbc/odbc-administrator.md)  
  
     Nástroj používaný pro konfiguraci databázového systému a zpřístupněte ji jako zdroj dat pro aplikaci.  
  
 Aplikace dosáhne nezávislost na systémech DBMS pracovní prostřednictvím ovladače ODBC napsané konkrétně pro databázového systému spíše než práce přímo se databázového systému. Ovladač přeloží volání do příkazů, že jeho databázového systému můžete použít ke zjednodušení práce vývojáře a zpřístupnění široké škály datových zdrojů.  
  
 Databázové třídy podporují libovolný zdroj dat, pro které máte ovladače ODBC. Například to může zahrnovat relační databázi, databázi indexované sekvenční přístup – metoda (ISAM), tabulky aplikace Microsoft Excel nebo textového souboru. Ovladače ODBC spravovat připojení ke zdroji dat a SQL slouží k výběru záznamy z databáze.  
  
 Seznam ovladačů ODBC zahrnuté v této verzi systému Visual C++ a informace o získání dalších ovladačů najdete v části [seznam ovladačů ODBC](../../data/odbc/odbc-driver-list.md).  
  
## <a name="see-also"></a>Viz také  
 [Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)