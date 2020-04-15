---
title: Průvodce komponentami ATL COM+ 1.0
ms.date: 05/08/2019
helpviewer_keywords:
- ATL projects, adding components
ms.assetid: 11670681-8671-4122-96a4-2e52f8dadce0
ms.openlocfilehash: d5c0c0c8edb6b698d3d8f50736121d987af98492
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321689"
---
# <a name="atl-com-10-component-wizard"></a>Průvodce komponentami ATL COM+ 1.0

::: moniker range="vs-2019"

Tento průvodce není k dispozici v sadě Visual Studio 2019 a novějších.

::: moniker-end

::: moniker range="<=vs-2017"

Tento průvodce slouží k přidání objektu do projektu, který podporuje služby modelu COM+ 1.0, včetně transakcí.

Můžete určit, zda objekt podporuje duální rozhraní a automatizace. Můžete také označit podporu pro rozhraní s informacemi o chybě, rozšířené řízení objektů, transakce a asynchronní řízení front zpráv.

## <a name="remarks"></a>Poznámky

Počínaje visual studio 2008, registrační skript vytvořený tímto průvodcem zaregistruje své součásti modelu COM pod **HKEY_CURRENT_USER** namísto **HKEY_LOCAL_MACHINE**. Chcete-li toto chování změnit, nastavte **komponentu Register pro všechny uživatele** v Průvodci zápisem ATL.

## <a name="names"></a>Názvy

Zadejte názvy objektu, rozhraní a tříd, které mají být přidány do projektu. S výjimkou **zkráceného názvu**lze všechna ostatní pole upravovat nezávisle na ostatních. Pokud změníte text pro **Krátký název**, projeví se změna v názvech všech ostatních polí na této stránce. Pokud změníte název **coclass** v části COM, změna se projeví v **type** a **ProgID** pole, ale název **rozhraní** se nezmění. Toto chování pojmenování je navržen tak, aby všechny názvy snadno identifikovatelné pro vás při vývoji ovládacího prvku.

- **Krátký název**

   Nastaví zkrácený název objektu. Zadaný název určuje `Class` názvy `Coclass` a, **názvy souborů CPP** a **H,** název **rozhraní,** názvy **typů** a **progID**, pokud tato pole nezměníte jednotlivě.

- **Soubor H**

   Nastaví název souboru záhlaví pro třídu nového objektu. Ve výchozím nastavení je tento název založen na názvu, který zadáte v **části Krátký název**. Kliknutím na tlačítko se třemi tečkami uložte název souboru do zvoleného umístění nebo připojíte deklaraci třídy k existujícímu souboru. Pokud zvolíte existující soubor, průvodce jej neuloží do vybraného umístění, dokud v průvodci neklepnete na **tlačítko Dokončit.**

   Průvodce nepřepíše soubor. Pokud vyberete název existujícího souboru, průvodce po klepnutí na tlačítko **Dokončit**zobrazí výzvu, abyste oznamovali, zda má být deklarace třídy připojena k obsahu souboru. Chcete-li soubor připojit, klepněte na tlačítko **Ano.** Klepnutím na tlačítko **Ne** se vrátíte do průvodce a zadejte jiný název souboru.

- **Třída**

   Nastaví název třídy, která má být vytvořena. Tento název je založen na názvu, který zadáte v **části Krátký název**, před nímž je uvedeno "C", což je typická předpona pro název třídy.

- **Soubor CPP**

   Nastaví název souboru implementace pro třídu nového objektu. Ve výchozím nastavení je tento název založen na názvu, který zadáte v **části Krátký název**. Kliknutím na tlačítko se třemi tečkami uložte název souboru do zvoleného umístění. Soubor není uložen do vybraného umístění, dokud v průvodci neklepnete na **tlačítko Dokončit.**

   Průvodce nepřepíše soubor. Pokud vyberete název existujícího souboru, průvodce po klepnutí na tlačítko **Dokončit**zobrazí výzvu k označení, zda má být implementace třídy připojena k obsahu souboru. Chcete-li soubor připojit, klepněte na tlačítko **Ano.** Klepnutím na tlačítko **Ne** se vrátíte do průvodce a zadejte jiný název souboru.

- **Připsat**

   Označuje, zda objekt používá atributy. Pokud přidáváte objekt do projektu přiřazeného knihovny ATL, je tato možnost vybrána a není k dispozici ke změně. To znamená, že do projektu vytvořeného s podporou atributů můžete přidat pouze přiřazené objekty.

   Pokud vyberete tuto možnost pro projekt knihovny ATL, který nemá podporu atributů, průvodce vás vyzve k určení, zda chcete přidat podporu atributů do projektu.

   Všechny objekty, které přidáte po nastavení této možnosti, jsou ve výchozím nastavení označeny jako přiřazené (je zaškrtnuto políčko). Toto pole můžete vymazat a přidat objekt, který nepoužívá atributy.

   Další informace naleznete v [tématu Nastavení aplikací, Průvodce projektem knihovny ATL](../../atl/reference/application-settings-atl-project-wizard.md) a [Základní mechanika atributů.](../../windows/basic-mechanics-of-attributes.md)

### <a name="com"></a>Model COM

Obsahuje informace o funkci COM pro objekt.

- **Coclass**

   Nastaví název třídy komponenty, která obsahuje seznam rozhraní podporovaných objektem.

> [!NOTE]
> Pokud vytvoříte projekt pomocí atributů nebo pokud na této stránce průvodce označíte, že komponenta modelu COM+ 1.0 používá atributy, nelze tuto možnost změnit, protože knihovna `coclass` ATL atribut neobsahuje.

- **Typ**

   Nastaví popis objektu, který se zobrazí v registru.

- **Rozhraní**

   Nastaví rozhraní, které vytvoříte pro svůj objekt. Toto rozhraní obsahuje vlastní metody.

- **Identifikátor progid**

   Nastaví název, který kontejnery můžete použít namísto CLSID objektu.

::: moniker-end

## <a name="see-also"></a>Viz také

[Součást ATL COM+ 1.0](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)
