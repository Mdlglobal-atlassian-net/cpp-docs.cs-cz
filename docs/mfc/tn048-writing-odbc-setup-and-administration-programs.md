---
title: 'TN048: Psaní programů pro nastavení a správu rozhraní ODBC pro databázové aplikace MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- installing ODBC
- ODBC, installing
- setup, ODBC setup programs
- TN048
- ODBC, and MFC
- MFC, database applications
ms.assetid: d456cdd4-0513-4a51-80c0-9132b66115ce
ms.openlocfilehash: d25520c4ffc805701dfe6b51192f8078e2fa300f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365483"
---
# <a name="tn048-writing-odbc-setup-and-administration-programs-for-mfc-database-applications"></a>TN048: Psaní programů pro nastavení a správu rozhraní ODBC pro databázové aplikace MFC

> [!NOTE]
> Následující technická poznámka nebyla aktualizována od doby, kdy byla poprvé zahrnuta do online dokumentace. V důsledku toho mohou být některé postupy a témata zastaralé nebo nesprávné. Chcete-li získat nejnovější informace, doporučujeme vyhledat téma zájmu v online indexu dokumentace.

Aplikace používající třídy databáze knihovny MFC budou potřebovat instalační program, který nainstaluje součásti ROZHRANÍ ODBC. Mohou také potřebovat program pro správu ODBC, který bude načítat informace o dostupných ovladačích, určit výchozí ovladače a konfigurovat zdroje dat. Tato poznámka popisuje použití rozhraní API instalačního programu ROZHRANÍ ODBC k zápisu těchto programů.

## <a name="writing-an-odbc-setup-program"></a><a name="_mfcnotes_writing_an_odbc_setup_program"></a>Zápis instalačního programu ODBC

Databázová aplikace knihovny MFC vyžaduje správce ovladačů ROZHRANÍ ODBC (ODBC. DLL) a ovladače ODBC, aby se mohli dostat ke zdrojům dat. Mnoho ovladačů ODBC také vyžaduje další síťové a komunikační knihovny DLL. Většina ovladačů ROZHRANÍ ODBC je dodávána s instalačním programem, který nainstaluje požadované součásti ROZHRANÍ ODBC. Vývojáři aplikací používající třídy databáze knihovny MFC mohou:

- Při instalaci součástí ROZHRANÍ ODBC se můžete spolehnout na instalační programy specifické pro daný ovladač. To nebude vyžadovat žádnou další práci na straně vývojáře - stačí redistribuovat instalační program ovladače.

- Případně můžete napsat vlastní instalační program, který nainstaluje správce ovladačů a ovladač.

Rozhraní API instalačního programu ROZHRANÍ ODBC lze použít k zápisu instalačních programů specifických pro aplikaci. Funkce v rozhraní API instalačního programu jsou implementovány knihovnou DLL instalačního programu ODBC – ODBCINST. Knihovna DLL v 16bitovém systému Windows a rozhraní ODBCCP32. DLL na Win32. Aplikace může `SQLInstallODBC` volat knihovnu DLL instalačního programu, která nainstaluje správce ovladačů ODBC, ovladače ODBC a všechny požadované překladače. Poté zaznamená nainstalované ovladače a překladatele v ODBCINST. INI (nebo registr, na NT). `SQLInstallODBC`vyžaduje úplnou cestu k rozhraní ODBC. SOUBOR INF, který obsahuje seznam ovladačů, které mají být nainstalovány a popisuje soubory, které tvoří každý ovladač. Obsahuje také podobné informace o správci řidičů a překladatelích. Odbc. Soubory INF jsou obvykle dodávány vývojáři ovladačů.

Program může také nainstalovat jednotlivé součásti ROZHRANÍ ODBC. Chcete-li nainstalovat Správce ovladačů, program nejprve zavolá `SQLInstallDriverManager` do instalační služby DLL, aby získal cílový adresář správce ovladačů. Obvykle se jedná o adresář, ve kterém se nacházejí knihovny DLL systému Windows. Program pak použije informace v části [SPRÁVCE OVLADAČŮ ODBC] rozhraní ODBC. soubor INF pro kopírování Správce ovladačů a souvisejících souborů z instalačního disku do tohoto adresáře. Chcete-li nainstalovat jednotlivé ovladače, `SQLInstallDriver` program nejprve volá v knihovně DLL instalačního programu a přidá specifikaci ovladače do rozhraní ODBCINST. INI (nebo registr, na NT). `SQLInstallDriver`vrátí cílový adresář ovladače – obvykle adresář, ve kterém jsou umístěny knihovny DLL systému Windows. Program pak použije informace v části ovladače ODBC. soubor INF pro kopírování dll ovladače a souvisejících souborů z instalačního disku do tohoto adresáře.

Další informace o rozhraní ODBC. INF, ODBCINST. INI a pomocí rozhraní API instalačního programu naleznete *v tématu Odkaz na programátora* ODBC SDK, kapitola 19, Instalace softwaru ODBC.

## <a name="writing-an-odbc-administrator"></a><a name="_mfcnotes_writing_an_odbc_administrator"></a>Zápis správce odhlašování ODBC

Databázová aplikace knihovny MFC může nastavit a nakonfigurovat zdroje dat ROZHRANÍ ODBC jedním ze dvou způsobů následujícím způsobem:

- Použijte správce rozhraní ODBC (k dispozici jako program nebo jako položku ovládacího panelu).

- Vytvořte si vlastní program pro konfiguraci zdrojů dat.

Program, který konfiguruje zdroje dat, provádí volání funkce do dll instalačního programu. Instalační dll volá instalační dll pro konfiguraci zdroje dat. Pro každý ovladač existuje jedna instalační dll. může se jedná o samotnou dll ovladače nebo samostatnou dll. Instalační dll vyzve uživatele k zadání informací, které ovladač potřebuje připojit ke zdroji dat a výchozí překladač, pokud je podporován. Potom volá knihovnu DLL instalačního programu a rozhraní API systému Windows k zaznamenání těchto informací v rozhraní ODBC. INI (nebo registr).

Chcete-li zobrazit dialogové okno, pomocí kterého může uživatel přidávat, `SQLManageDataSources` upravovat a odstraňovat zdroje dat, program volá v dll instalačního programu. Tato funkce je vyvolána, když je instalační dll volána z Ovládacích panelů. Chcete-li přidat, upravit nebo `SQLManageDataSources` odstranit `ConfigDSN` zdroj dat, volání v instalační dll pro ovladač přidružený k tomuto zdroji dat. Chcete-li přímo přidávat, upravovat nebo odstraňovat zdroje dat, program volá `SQLConfigDataSource` v instalační dll. Program předá název zdroje dat a možnost, která určuje akci, která má být vykonat. `SQLConfigDataSource`volá `ConfigDSN` v instalační dll a předá `SQLConfigDataSource`argumenty z .

Další informace naleznete v *tématu Odkaz na programátora sady* ODBC SDK, kapitola 23, Odkaz na funkci instalační knihovny DLL a kapitola 24, Reference funkce knihovny DLL instalačního programu.

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
