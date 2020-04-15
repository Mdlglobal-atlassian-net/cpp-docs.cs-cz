---
title: Průvodce stránkou vlastností ATL
ms.date: 05/09/2019
f1_keywords:
- vc.codewiz.class.atl.ppg.overview
helpviewer_keywords:
- ATL projects, adding property pages
- ATL Property Page Wizard
ms.assetid: 6113e325-facd-4f68-b491-144d75209922
ms.openlocfilehash: eaf070d5a98a05dbe3102afac8317ffd59298ad2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321681"
---
# <a name="atl-property-page-wizard"></a>Průvodce stránkou vlastností ATL

::: moniker range="vs-2019"

Tento průvodce není k dispozici v sadě Visual Studio 2019 a novějších.

::: moniker-end

::: moniker range="<=vs-2017"

Tento průvodce [přidá stránku vlastností do projektu knihovny ATL](../../atl/reference/adding-an-atl-property-page.md) nebo do projektu knihovny MFC s podporou knihovny ATL. Stránka vlastností knihovny ATL poskytuje uživatelské rozhraní pro nastavení vlastností (nebo volání metod) jednoho nebo více objektů MODELU COM.

## <a name="remarks"></a>Poznámky

Počínaje visual studio 2008, registrační skript vytvořený tímto průvodcem zaregistruje své součásti modelu COM pod **HKEY_CURRENT_USER** namísto **HKEY_LOCAL_MACHINE**. Chcete-li toto chování změnit, nastavte **komponentu Register pro všechny uživatele** v Průvodci zápisem ATL.

## <a name="names"></a>Názvy

Zadejte názvy objektu, rozhraní a tříd, které mají být přidány do projektu. S výjimkou **zkráceného názvu**lze všechna ostatní pole upravovat nezávisle. Pokud změníte text pro **Krátký název**, projeví se změna v názvech všech ostatních polí na této stránce. Pokud změníte název **coclass** v části COM, změna se projeví v polích **Typ** a **ProgID.** Toto chování pojmenování je navržen tak, aby všechny názvy snadno identifikovatelné pro vás při vývoji stránky vlastností.

> [!NOTE]
> **Coclass** lze upravovat pouze u nepřiřazených projektů. Pokud je projekt přiřazen, nelze upravit **coclass**.

### <a name="c"></a>C++

Obsahuje informace pro třídu C++ vytvořenou k implementaci objektu.

|||
|-|-|
|Označení|Definice|
|**Krátký název**|Nastaví zkrácený název objektu. Zadaný název určuje názvy tříd **a tříd,** názvy souborů (**CPP** a **.h**), název **Typu** a **ProgID**, pokud tato pole nezměníte jednotlivě.|
|**Soubor H**|Nastaví název souboru záhlaví pro třídu nového objektu. Ve výchozím nastavení je tento název založen na názvu, který zadáte v **části Krátký název**. Kliknutím na tlačítko se třemi tečkami uložte název souboru do zvoleného umístění nebo připojíte deklaraci třídy k existujícímu souboru. Pokud vyberete existující soubor, průvodce jej neuloží do vybraného umístění, dokud v průvodci neklepnete na **tlačítko Dokončit.**<br /><br /> Průvodce nepřepíše soubor. Pokud vyberete název existujícího souboru, průvodce po klepnutí na tlačítko **Dokončit**zobrazí výzvu, abyste oznamovali, zda má být deklarace třídy připojena k obsahu souboru. Chcete-li soubor připojit, klepněte na tlačítko **Ano.** Klepnutím na tlačítko **Ne** se vrátíte do průvodce a zadejte jiný název souboru.|
|**Třída**|Nastaví název třídy, která implementuje objekt. Tento název je založen na názvu, který zadáte v **short name**, před nímž je "C", typická předpona pro název třídy.|
|**Soubor CPP**|Nastaví název souboru implementace pro třídu nového objektu. Ve výchozím nastavení je tento název založen na názvu, který zadáte v **části Krátký název**. Kliknutím na tlačítko se třemi tečkami uložte název souboru do zvoleného umístění. Soubor není uložen do vybraného umístění, dokud v průvodci neklepnete na **tlačítko Dokončit.**<br /><br /> Průvodce nepřepíše soubor. Pokud vyberete název existujícího souboru, průvodce po klepnutí na tlačítko **Dokončit**zobrazí výzvu k označení, zda má být implementace třídy připojena k obsahu souboru. Chcete-li soubor připojit, klepněte na tlačítko **Ano.** Klepnutím na tlačítko **Ne** se vrátíte do průvodce a zadejte jiný název souboru.|
|**Připsat**|Označuje, zda objekt používá atributy. Pokud přidáváte objekt do projektu přiřazeného knihovny ATL, je tato možnost vybrána a není k dispozici pro změnu, to znamená, že do projektu vytvořeného s podporou atributů můžete přidat pouze přiřazené objekty.<br /><br /> Přiřazený objekt můžete přidat pouze do projektu knihovny ATL, který používá atributy. Pokud vyberete tuto možnost pro projekt knihovny ATL, který nemá podporu atributů, průvodce vás vyzve k určení, zda chcete přidat podporu atributů do projektu.<br /><br /> Ve výchozím nastavení jsou všechny objekty, které přidáte po nastavení této možnosti, označeny jako přiřazené (je zaškrtnuto políčko). Toto pole můžete vymazat a přidat objekt, který nepoužívá atributy.<br /><br /> Další informace naleznete v [tématu Nastavení aplikací, Průvodce projektem knihovny ATL](../../atl/reference/application-settings-atl-project-wizard.md) a [Základní mechanika atributů.](../../windows/basic-mechanics-of-attributes.md)|

### <a name="com"></a>Model COM

Obsahuje informace o funkci COM pro objekt.

- **Coclass**

   Nastaví název třídy komponenty, která obsahuje seznam rozhraní podporovaných objektem.

   > [!NOTE]
   > Pokud vytvoříte projekt pomocí atributů nebo pokud na této stránce průvodce označíte, že stránka vlastností `coclass` používá atributy, nelze tuto možnost změnit, protože knihovna ATL atribut neobsahuje.

- **Typ**

   Nastaví popis objektu, který se zobrazí v registru.

- **Identifikátor progid**

   Nastaví název, který kontejnery můžete použít namísto CLSID objektu.

::: moniker-end

## <a name="see-also"></a>Viz také

[Možnosti, Průvodce stránkou vlastností atl](../../atl/reference/options-atl-property-page-wizard.md)<br/>
[Řetězce, Průvodce stránkou vlastností atl](../../atl/reference/strings-atl-property-page-wizard.md)<br/>
[Příklad: Implementace stránky vlastností](../../atl/example-implementing-a-property-page.md)
