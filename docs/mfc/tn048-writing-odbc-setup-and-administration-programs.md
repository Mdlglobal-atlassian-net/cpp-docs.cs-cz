---
title: "TN048: Psaní pro databázové aplikace MFC ODBC nastavení a programy pro správu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.odbc
dev_langs:
- C++
helpviewer_keywords:
- installing ODBC
- ODBC, installing
- setup, ODBC setup programs
- TN048
- ODBC, and MFC
- MFC, database applications
ms.assetid: d456cdd4-0513-4a51-80c0-9132b66115ce
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3ec19e3c03d88fa088622c7ed8a5b4efeed0014b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="tn048-writing-odbc-setup-and-administration-programs-for-mfc-database-applications"></a>TN048: Psaní programů pro nastavení a správu rozhraní ODBC pro databázové aplikace MFC
> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována vzhledem k tomu, že byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata může být zastaralý nebo není správný. Nejnovější informace se doporučuje, vyhledejte téma týkající se v indexu online dokumentaci.  
  
 Aplikace, které používají třídami databází MFC potřebovat instalační program, který nainstaluje komponenty ODBC. Také potřebovat program pro správu rozhraní ODBC, který načte informace o dostupných ovladačů, můžete určit výchozí ovladače a konfigurace zdroje dat. Tato poznámka popisuje použití rozhraní API ODBC Instalační služby pro zápis tyto programy.  
  
##  <a name="_mfcnotes_writing_an_odbc_setup_program"></a>Zápis instalačního programu rozhraní ODBC  
 Databázové aplikace MFC vyžaduje správce ovladačů ODBC (rozhraní ODBC. Knihovny DLL) a se získají ke zdrojům dat, aby ovladače ODBC. Mnoho ovladačů ODBC také vyžadovat další sítě a komunikace knihovny DLL. Většina ovladačů ODBC dodávají spolu s instalační program, který bude instalovat požadované součásti ODBC. Mohou vývojáři aplikace použití databázových tříd MFC:  
  
-   Spoléhají na ovladačem instalační programy pro instalaci součástí rozhraní ODBC. To bude vyžadovat žádné další pracovní na vývojáře pro část – stačí znovu distribuovat ovladače instalační program.  
  
-   Alternativně můžete napsat vlastní instalační program, který bude instalaci správce ovladačů a ovladače.  
  
 Instalační program rozhraní API ODBC slouží k zápisu specifické pro aplikaci instalační programy. Funkce v instalačním programu rozhraní API jsou implementované pomocí Instalační služby rozhraní ODBC knihovny DLL – ODBCINST. Knihovny DLL na 16bitový systém Windows a ODBCCP32. Knihovny DLL na Win32. Aplikace může volat **Funkce SQLInstallODBC** v instalačním programu DLL, která bude instalaci správce ovladačů ODBC, ovladače ODBC a všechny požadované překladatelé. Zaznamenává pak nainstalované ovladače a překladatelé v ODBCINST. Soubor INI (nebo registru, NT). **Funkce SQLInstallODBC** vyžaduje úplnou cestu k rozhraní ODBC. Soubor INF, který obsahuje seznam instalaci ovladačů a popisuje soubory, které tvoří každý ovladač. Obsahuje taky podobné informace o správce ovladačů a překladatelé. ODBC. Souborů INF jsou obvykle poskytuje vývojářům ovladačů.  
  
 Program můžete také nainstalovat jednotlivých součástí rozhraní ODBC. Při instalaci správce ovladačů první program zavolá **SQLInstallDriverManager** v instalačním programu knihovnu DLL k získání cílový adresář pro správce ovladačů. Obvykle je to adresář, ve kterém jsou umístěny knihovny DLL systému Windows. Program pak používá informace v části [správce ovladačů ODBC] ODBC. Soubor INF pro kopírování správce ovladačů a související soubory z instalační disk do tohoto adresáře. Pro instalaci jednotlivých ovladačů, nejprve program zavolá **Funkce SQLInstallDriver** v instalačním programu DLL pro přidání do ODBCINST specifikace ovladačů. Soubor INI (nebo registru, NT). **Funkce SQLInstallDriver** vrátí ovladače cílový adresář – obvykle adresář, ve kterém jsou umístěny knihovny DLL systému Windows. Program pak používá informace v části ovladače ODBC. Soubor INF zkopírujte ovladač DLL a související soubory z instalační disk do tohoto adresáře.  
  
 Další informace o rozhraní ODBC. INF, ODBCINST. INI a pomocí Instalační služby rozhraní API, najdete v části sada SDK rozhraní ODBC *referenční informace pro programátory,* kapitoly 19, instalace softwaru ODBC.  
  
##  <a name="_mfcnotes_writing_an_odbc_administrator"></a>Zápis správce rozhraní ODBC  
 Databázové aplikace MFC můžete nastavit a nakonfigurovat zdroje dat ODBC v jednom ze dvou způsobů, následujícím způsobem:  
  
-   Pomocí Správce rozhraní ODBC (k dispozici jako program nebo některou položku Ovládacích panelů).  
  
-   Vytvořte vlastní aplikaci konfiguraci zdroje dat.  
  
 Program, který konfiguruje zdroje dat, volá funkce DLL Instalační služby. Instalační program DLL volá instalace knihovny DLL pro konfiguraci zdroje dat. Jeden nastavení knihovny DLL pro každý ovladač; To může být ovladač samotné knihovny DLL nebo samostatné knihovny DLL. Instalační program DLL vyzve uživatele k informace, které ovladač potřebuje pro připojení ke zdroji dat a výchozí překladač, pokud podporován. Pak zavolá instalační program, zaznamenejte tyto informace v ODBC knihovny DLL a rozhraní API systému Windows. Soubor INI (nebo registru).  
  
 Pokud chcete zobrazit dialogové okno, pomocí kterého můžete přidat, upravit a odstranit zdroje dat uživatele, program zavolá **SQLManageDataSources** v instalačním programu knihovnu DLL. Tato funkce je voláno, když instalační program knihovny DLL je volána z ovládacích panelů. Chcete-li přidat, upravit nebo odstranit zdroj dat, **SQLManageDataSources** volání **ConfigDSN** v nastavení knihovny DLL pro ovladače, které jsou přidružené k danému zdroji dat. Přímo přidat, upravit nebo odstranit data zdroje, program zavolá **SQLConfigDataSource** v instalačním programu knihovnu DLL. Program předá název zdroje dat a možnost, která určuje akci, kterou trvat. **SQLConfigDataSource** volání **ConfigDSN** v instalačním programu DLL a předává je argumenty z **SQLConfigDataSource**.  
  
 Další informace najdete v tématu ODBC SDK *referenční informace pro programátory,* kapitoly 23, instalační program referenční dokumentace funkcí knihovny DLL a kapitoly 24, odkaz na funkci knihovny DLL Instalační služby.  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

