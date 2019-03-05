---
title: 'TN048: Zápis nastavení rozhraní ODBC a programy pro správu pro databázové aplikace MFC'
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.odbc
helpviewer_keywords:
- installing ODBC
- ODBC, installing
- setup, ODBC setup programs
- TN048
- ODBC, and MFC
- MFC, database applications
ms.assetid: d456cdd4-0513-4a51-80c0-9132b66115ce
ms.openlocfilehash: 2904ceb626fd1bfad0b24026deb08f2c5dcbcd4a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283888"
---
# <a name="tn048-writing-odbc-setup-and-administration-programs-for-mfc-database-applications"></a>TN048: Zápis nastavení rozhraní ODBC a programy pro správu pro databázové aplikace MFC

> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována, protože byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata mohou být nesprávné nebo zastaralé. Nejnovější informace se doporučuje vyhledat téma zájmu v dokumentaci online index.

Použití databázových tříd MFC aplikace potřebovat instalační program, který nainstaluje součástí rozhraní ODBC. Také potřebovat program pro správu rozhraní ODBC, který načte informace o dostupných ovladačů, můžete určit výchozí ovladačů a nakonfigurovat datové zdroje. Tato poznámka popisuje použití rozhraní API ODBC instalačního programu k zápisu těchto programů.

##  <a name="_mfcnotes_writing_an_odbc_setup_program"></a> Zápis instalační Program rozhraní ODBC

Správce ovladačů ODBC (rozhraní ODBC vyžaduje databázových aplikacích MFC. Knihovny DLL) a být schopní dostat k zdroje dat ODBC – ovladače. Mnoho ovladačů ODBC také vyžadovat další sítě a komunikačních knihoven DLL. Většina ovladače rozhraní ODBC jsou dodávány s instalační program, který bude instalace požadovaných součástí rozhraní ODBC. Použití databázových tříd MFC vývojářům aplikací umožňuje:

- Spolehněte se na specifický ovladač instalační programy pro instalaci součástí rozhraní ODBC. To bude vyžadovat žádná další práce na část pro vývojáře – stačí znovu distribuovat ovladače instalační program.

- Alternativně můžete napsat vlastní instalační program, který bude instalaci správce ovladačů a ovladače.

Instalační program rozhraní API ODBC je možné zapsat specifické pro aplikaci instalační programy. Funkce v instalačním programu API jsou implementované pomocí Instalační služby rozhraní ODBC knihovny DLL – ODBCINST. Knihovna DLL na Windows 16 bitů a ODBCCP32. Knihovny DLL v systému Win32. Aplikace může volat `SQLInstallODBC` v instalačním programu knihovny DLL, který bude instalaci správce ovladačů ODBC, ovladače rozhraní ODBC a všechny požadované překladače. V ODBCINST pak zaznamenává nainstalovaných ovladačů a překladatele. Soubor INI (nebo registru, NT). `SQLInstallODBC` vyžaduje úplnou cestu k rozhraní ODBC. Soubor INF, který obsahuje seznam instalaci ovladačů a popisuje soubory, které tvoří každou ovladače. Také obsahuje podobné informace o správce ovladačů a překladatele. ROZHRANÍ ODBC. Soubory INF jsou obvykle dodávány vývojáři ovladačů.

Program můžete také nainstalovat jednotlivých součástí rozhraní ODBC. K instalaci správce ovladačů, program nejprve zavolá `SQLInstallDriverManager` v instalačním programu knihovnu DLL k získání cílový adresář pro správce ovladačů. Obvykle se jedná o adresář, ve kterém jsou umístěny Windows knihovny DLL. Program použije informace v části [správce ovladačů ODBC] rozhraní ODBC. Soubor INF zkopírovat správce ovladačů a související soubory z instalačního disku do tohoto adresáře. Pro instalaci jednotlivých ovladačů, program nejprve zavolá `SQLInstallDriver` v instalačním programu přidat specifikaci ovladač ODBCINST knihovny DLL. Soubor INI (nebo registru, NT). `SQLInstallDriver` Vrátí ovladače cílový adresář – obvykle na adresář, ve kterém jsou umístěny Windows knihovny DLL. Program použije informace v části ovladače rozhraní ODBC. Soubor INF zkopírujte ovladač knihovny DLL a související soubory z instalačního disku do tohoto adresáře.

Další informace o rozhraní ODBC. INF, ODBCINST. INI a pomocí instalačního programu rozhraní API, najdete v části sada SDK rozhraní ODBC *referenční informace pro programátory* kapitole 19, instalace softwaru ODBC.

##  <a name="_mfcnotes_writing_an_odbc_administrator"></a> Zápis správce rozhraní ODBC

Databázové aplikace MFC lze nastavení a konfigurace zdroje dat ODBC v jedné ze dvou způsobů, následujícím způsobem:

- Pomocí Správce rozhraní ODBC (k dispozici jako program nebo v Ovládacích panelech).

- Vytvořte vlastní program k nakonfigurovat datové zdroje.

Program, který konfiguruje zdroje dat, provede volání funkce do instalačního programu knihovny DLL. Instalační program knihovnu DLL zavolá instalace knihovny DLL pro zdroj dat nakonfigurovat. Existuje jedna instalace knihovny DLL pro každý ovladač; může být ovladač samotná knihovna DLL nebo samostatné knihovny DLL. Instalace knihovny DLL vyzve uživatele k informace, které ovladače potřebuje pro připojení ke zdroji dat a výchozí překladač, pokud se podporuje. Poté zavolá knihovny DLL a rozhraní API Windows zaznamenávat tyto informace v rozhraní ODBC Instalační služby. Soubor INI (nebo registru).

Chcete-li zobrazit dialogové okno, pomocí kterého můžete uživatele přidat, upravit a odstranit zdroje dat, program zavolá `SQLManageDataSources` v instalačním programu knihovny DLL. Tato funkce je vyvolán při instalační program knihovny DLL volání z ovládacích panelů. K přidání, úprava nebo odstranění zdroje dat, `SQLManageDataSources` volání `ConfigDSN` v rámci instalace knihovny DLL ovladače přidružené k danému zdroji dat. Přímo přidat, upravit nebo odstranit data zdroje, program zavolá `SQLConfigDataSource` v instalačním programu knihovny DLL. Program předává název zdroje dat a možnost, která určuje akce má být provedena. `SQLConfigDataSource` volání `ConfigDSN` v nastavení knihovny DLL a předává je argumenty z `SQLConfigDataSource`.

Další informace najdete v tématu rozhraní ODBC SDK *referenční informace pro programátory* kapitoly 23, instalační program referenční dokumentace funkcí knihovny DLL a kapitoly 24, instalační program referenční dokumentace funkcí knihovny DLL.

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
