---
title: Průvodce ovládacími prvky ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.control.overview
helpviewer_keywords:
- ATL projects, adding controls
- controls [ATL], adding to projects
- ATL Control Wizard
ms.assetid: 991f8e72-ffbc-4382-a4ce-e255acfba5b6
ms.openlocfilehash: a10c5c358901122dda37b395c1f0fa5cdc30ce30
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321702"
---
# <a name="atl-control-wizard"></a>Průvodce ovládacími prvky ATL

Vloží do projektu knihovny ATL (nebo projektu knihovny MFC s podporou knihovny ATL) ovládací prvek knihovny ATL. Pomocí tohoto průvodce můžete vložit jeden ze tří druhů ovládacích prvků:

- Standardní řízení

- Kompozitní ovládací prvek

- Ovládací prvek DHTML

Kromě toho můžete zadat minimální ovládací prvek, odebrání rozhraní ze seznamu [rozhraní,](../../atl/reference/interfaces-atl-control-wizard.md) které jsou k dispozici jako výchozí pro ovládací prvky otevřít ve většině kontejnerů. Rozhraní, která chcete podporovat, můžete nastavit pro ovládací prvek na stránce **Rozhraní** průvodce.

## <a name="remarks"></a>Poznámky

Registrační skript vytvořený tímto průvodcem zaregistruje své součásti modelu COM pod HKEY_CURRENT_USER namísto HKEY_LOCAL_MACHINE. Chcete-li toto chování změnit, nastavte **komponentu Register pro všechny uživatele** v Průvodci zápisem ATL.

## <a name="names"></a>Názvy

Zadejte názvy objektu, rozhraní a tříd, které mají být přidány do projektu. S výjimkou **zkráceného názvu**lze všechna ostatní pole měnit nezávisle. Pokud změníte text pro **Krátký název**, projeví se změna v názvech všech ostatních polí na této stránce. Pokud změníte název **coclass** v části COM, změna se projeví v poli **Typ,** ale název **rozhraní** a **ProgID** se nezmění. Toto chování pojmenování je navržen tak, aby všechny názvy snadno identifikovatelné pro vás při vývoji ovládacího prvku.

> [!NOTE]
> **Coclass** lze upravovat pouze u nepřiřazených ovládacích prvků. Pokud je projekt přiřazen, nelze upravit **coclass**.

### <a name="c"></a>C++

Obsahuje informace pro třídu C++ vytvořenou k implementaci objektu.

- **Krátký název**

   Nastaví zkrácený název objektu. Název, který zadáte určuje třídy a **coclass** názvy, soubor (. CPP a . H) názvy, název rozhraní a **názvy typů,** pokud tato pole nezměníte jednotlivě.

- **Třída**

   Nastaví název třídy, která implementuje objekt. Tento název je založen na názvu, který zadáte v **short name**, před nímž je "C", typická předpona pro název třídy.

- **Soubor H**

   Nastaví název souboru záhlaví pro třídu nového objektu. Ve výchozím nastavení je tento název založen na názvu, který zadáte v **části Krátký název**. Kliknutím na tlačítko se třemi tečkami uložte název souboru do zvoleného umístění nebo připojíte deklaraci třídy k existujícímu souboru. Pokud vyberete existující soubor, průvodce jej neuloží do vybraného umístění, dokud neklepnete na tlačítko **Dokončit**.

   Průvodce nepřepíše soubor. Pokud vyberete název existujícího souboru, průvodce po klepnutí na tlačítko **Dokončit**zobrazí výzvu, abyste oznamovali, zda má být deklarace třídy připojena k obsahu souboru. Chcete-li soubor připojit, klepněte na tlačítko **Ano.** Klepnutím na tlačítko **Ne** se vrátíte do průvodce a zadejte jiný název souboru.

- **Soubor CPP**

   Nastaví název souboru implementace pro třídu nového objektu. Ve výchozím nastavení je tento název založen na názvu, který zadáte v **části Krátký název**. Kliknutím na tlačítko se třemi tečkami uložte název souboru do zvoleného umístění. Soubor není uložen do vybraného umístění, dokud v průvodci neklepnete na **tlačítko Dokončit.**

   Průvodce nepřepíše soubor. Pokud vyberete název existujícího souboru, průvodce po klepnutí na tlačítko **Dokončit**zobrazí výzvu k označení, zda má být implementace třídy připojena k obsahu souboru. Chcete-li soubor připojit, klepněte na tlačítko **Ano.** Klepnutím na tlačítko **Ne** se vrátíte do průvodce a zadejte jiný název souboru.

- **Připsat**

   Označuje, zda objekt používá atributy. Pokud přidáváte objekt do projektu přiřazeného knihovny ATL, je tato možnost vybrána a není k dispozici ke změně. To znamená, že do projektu vytvořeného s podporou atributů můžete přidat pouze přiřazené objekty.

   Přiřazený objekt můžete přidat pouze do projektu knihovny ATL, který používá atributy. Pokud vyberete tuto možnost pro projekt knihovny ATL, který nemá podporu atributů, průvodce vás vyzve k určení, zda chcete přidat podporu atributů do projektu.

   Ve výchozím nastavení jsou všechny objekty, které přidáte po nastavení této možnosti, označeny jako přiřazené (je zaškrtnuto políčko). Toto pole můžete vymazat a přidat objekt, který nepoužívá atributy.

   Další informace naleznete v [tématu Nastavení aplikací, Průvodce projektem knihovny ATL](../../atl/reference/application-settings-atl-project-wizard.md) a [Základní mechanika atributů.](../../windows/basic-mechanics-of-attributes.md)

### <a name="com"></a>Model COM

Obsahuje informace o funkci COM pro objekt.

- **Coclass**

   Nastaví název třídy komponenty, která obsahuje seznam rozhraní podporovaných objektem.

   > [!NOTE]
   > Pokud vytvoříte projekt pomocí atributů nebo pokud na této stránce průvodce označíte, že ovládací prvek používá atributy, nelze tuto možnost změnit, protože knihovna ATL neobsahuje atribut **coclass.**

- **Rozhraní**

   Nastaví název rozhraní pro objekt. Ve výchozím nastavení je název rozhraní předřazený "I".

- **Typ**

   Nastaví popis objektu, který se zobrazí v registru.

- **Identifikátor progid**

   Nastaví název, který kontejnery můžete použít namísto CLSID objektu. Toto pole není automaticky vyplněno. Pokud toto pole nenaplníte ručně, nemusí být ovládací prvek k dispozici pro jiné nástroje. Například ovládací prvky ActiveX, `ProgID` které jsou generovány bez a, nejsou k dispozici v dialogovém okně **Vložit ovládací prvek ActiveX.** Další informace o dialogovém okně naleznete v [tématu Vložení ovládacího dialogového okna ActiveX](../../windows/insert-activex-control-dialog-box.md).

## <a name="see-also"></a>Viz také

[Řízení atl](../../atl/reference/adding-an-atl-control.md)<br/>
[Přidání funkcí do složeného ovládacího prvku](../../atl/adding-functionality-to-the-composite-control.md)<br/>
[Základy objektů ATL COM](../../atl/fundamentals-of-atl-com-objects.md)
