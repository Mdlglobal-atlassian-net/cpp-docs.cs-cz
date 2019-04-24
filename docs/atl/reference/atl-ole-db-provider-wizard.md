---
title: Průvodce zprostředkovatelem ATL OLE DB
ms.date: 10/03/2018
f1_keywords:
- vc.codewiz.class.atl.provider.overview
helpviewer_keywords:
- ATL OLE DB Provider Wizard
- ATL projects, adding ATL OLE DB providers
ms.assetid: cf91ba78-01d1-4d12-b673-e95d96bfbebe
ms.openlocfilehash: 3f8ff69fd80056bc2ac5a52cf3f42c69f8e8c543
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62248260"
---
# <a name="atl-ole-db-provider-wizard"></a>Průvodce zprostředkovatelem ATL OLE DB

Tento průvodce vytvoří třídy, které tvoří zprostředkovatele OLE DB.

> [!WARNING]
> V sadě Visual Studio 2017 verze 15.9 průvodce tento kód je zastaralá a v budoucí verzi systému Visual Studio se odebere. Tento průvodce je používána zřídka. Obecné podpory knihovny ATL a MFC nemá žádný vliv, odebráním tohoto průvodce. Pokud chcete sdílet svůj názor na toto vyřazení, vyplňte prosím [tento průzkum](https://www.surveymonkey.com/r/QDWKKCN). Vaše zpětná vazba záleží na nás.

## <a name="remarks"></a>Poznámky

Od verze Visual Studio 2008, registrace skriptu vytvářených Tento průvodce zaregistruje jeho komponenty modelu COM v **HKEY_CURRENT_USER** místo **HKEY_LOCAL_MACHINE**. Chcete-li toto chování změnit, nastavte **registrace komponenty pro všechny uživatele** možnost ATL průvodce.

Následující tabulka popisuje možnosti pro Průvodce zprostředkovatelem ATL OLE DB:

- **Krátký název**

   Zadejte krátký název zprostředkovatele, který se má vytvořit. Upravit pole v Průvodci se automaticky vyplní podle vás zadejte sem. Pokud chcete, můžete upravit ostatní.

- **Coclass**

   Název třídy typu coclass. Název ProgID se změní tak, aby odpovídaly tento název.

- **S atributy**

   Tato možnost určuje, zda má průvodce vytvořit pomocí atributů nebo deklarací šablony třídy zprostředkovatele. Když vyberete tuto možnost, Průvodce místo deklarací šablony (Toto je výchozí možnost, pokud jste vytvořili projekt s atributy) používá atributy. Když zrušíte zaškrtnutí tohoto políčka, používá Průvodce místo atributů (Toto je výchozí možnost, pokud jste vytvořili projekt bez atributů) deklarace šablony.

   Pokud vyberete tuto možnost, při vytváření projektu bez atributů, Průvodce zobrazí upozornění, že projekt bude převeden do projektu s atributy a zeptá, jestli se má pokračovat nebo ne.

- **ProgID**

   ProgID, neboli programový identifikátor, je textový řetězec, který vaše aplikace může používat místo identifikátoru GUID. Název ProgID má tvar *Projectname.Coclassname*.

- **Verze**

   Číslo verze vašeho zprostředkovatele. Výchozí hodnota je 1.

- **Třída zdroje dat**

   Název třídy zdroje dat formuláře C*Shortname*zdroje.

- **Soubor .h zdroje dat**

   Hlavičkový soubor pro třídu zdroje data. Můžete upravit tento název souboru nebo vybrat existující hlavičkový soubor.

- **Třída relace**

   Název třídy relace ve formátu jazyka C*Shortname*relace.

- **Soubor .h relace**

   Hlavičkový soubor pro třídu relace. Můžete upravit tento název souboru nebo vybrat existující hlavičkový soubor.

- **Třídy příkazů**

   Název třídy příkazu ve formátu jazyka C*Shortname*příkazu.

- **Soubor .h příkazů**

   Hlavičkový soubor pro třídu příkazu. Tento název nejde upravit a závisí na názvu hlavičkového souboru sady řádků.

- **Třídy sady řádků**

   Název třídy sady řádků ve formátu jazyka C*Shortname*sady řádků.

- **Soubor .h sady řádků**

   Hlavičkový soubor pro třídu sady řádků. Můžete upravit tento název souboru nebo vybrat existující hlavičkový soubor.

- **Soubor .cpp sady řádků**

   Implementační soubor zprostředkovatele. Můžete upravit tento název souboru nebo vybrat existující implementační soubor.

## <a name="see-also"></a>Viz také:

[Zprostředkovatel knihovny ATL technologie OLE DB](../../atl/reference/adding-an-atl-ole-db-provider.md)
