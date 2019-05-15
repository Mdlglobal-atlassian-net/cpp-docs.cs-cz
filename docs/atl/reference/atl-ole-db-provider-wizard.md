---
title: Průvodce zprostředkovatelem ATL OLE DB
ms.date: 05/09/2019
helpviewer_keywords:
- ATL projects, adding ATL OLE DB providers
ms.assetid: cf91ba78-01d1-4d12-b673-e95d96bfbebe
ms.openlocfilehash: 91384d6c61368ee56ed303622e5c1bdfad09bd8a
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65706967"
---
# <a name="atl-ole-db-provider-wizard"></a>Průvodce zprostředkovatelem ATL OLE DB

::: moniker range="vs-2019"

Tento průvodce není k dispozici v aplikaci Visual Studio 2019 a novějším.

::: moniker-end

::: moniker range="<=vs-2017"

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

::: moniker-end

## <a name="see-also"></a>Viz také:

[Zprostředkovatel knihovny ATL technologie OLE DB](../../atl/reference/adding-an-atl-ole-db-provider.md)
