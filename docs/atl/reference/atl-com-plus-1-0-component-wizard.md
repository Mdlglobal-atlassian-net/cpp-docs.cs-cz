---
title: Průvodce komponentami ATL COM+ 1.0
ms.date: 05/08/2019
helpviewer_keywords:
- ATL projects, adding components
ms.assetid: 11670681-8671-4122-96a4-2e52f8dadce0
ms.openlocfilehash: eaecd0d4e6e2b024ce3312719e7104298d3f9a66
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075285"
---
# <a name="atl-com-10-component-wizard"></a>Průvodce komponentami ATL COM+ 1.0

::: moniker range="vs-2019"

Tento průvodce není k dispozici v aplikaci Visual Studio 2019 a novějším.

::: moniker-end

::: moniker range="<=vs-2017"

Pomocí tohoto průvodce můžete přidat objekt do projektu, který podporuje služby COM+ 1,0, včetně transakcí.

Můžete určit, zda objekt podporuje duální rozhraní a automatizaci. Můžete také indikovat podporu pro rozhraní informací o chybách, rozšířený ovládací prvek Object, transakce a asynchronní službu Řízení front zpráv.

## <a name="remarks"></a>Poznámky

Počínaje sadou Visual Studio 2008, registrační skript vytvořený tímto průvodcem zaregistruje své komponenty COM v **HKEY_CURRENT_USER** místo **HKEY_LOCAL_MACHINE**. Chcete-li toto chování změnit, nastavte v Průvodci knihovnou ATL možnost **Registrovat komponentu pro všechny uživatele** .

## <a name="names"></a>Jména

Zadejte názvy pro objekt, rozhraní a třídy, které se mají přidat do projektu. S výjimkou **krátkého názvu**lze všechna ostatní pole upravovat nezávisle na ostatních. Pokud změníte text pro **krátký název**, změna se projeví v názvech všech ostatních polí na této stránce. Změníte-li název **třídy coclass** v oddílu com, změna se projeví v polích **typ** a **ProgID** , ale název **rozhraní** se nezmění. Toto chování při pojmenovávání je navržené tak, aby byly všechny názvy snadno identifikovatelné při vývoji ovládacího prvku.

- **Krátký název**

   Nastaví zkrácený název objektu. Název, který zadáte, určuje názvy `Class` a `Coclass`, **soubor. cpp** a názvy **souborů. h** , název **rozhraní** , názvy **typů** a **identifikátor ProgID**, pokud tato pole nezměníte jednotlivě.

- **soubor. h**

   Nastaví název hlavičkového souboru pro novou třídu objektu. Ve výchozím nastavení je tento název založen na názvu, který zadáte v poli **krátký název**. Kliknutím na tlačítko se třemi tečkami uložte název souboru do zvoleného umístění nebo přidejte deklaraci třídy do existujícího souboru. Pokud zvolíte existující soubor, průvodce ho nebude ukládat do vybraného umístění, dokud v průvodci nekliknete na **Dokončit** .

   Průvodce nepřepisuje soubor. Pokud vyberete název existujícího souboru, po kliknutí na tlačítko **Dokončit**vás průvodce vyzve, abyste označili, zda má být deklarace třídy připojena k obsahu souboru. Kliknutím na **Ano** přidejte soubor. Kliknutím na **ne** se vrátíte do průvodce a zadáte jiný název souboru.

- **Deník**

   Nastaví název třídy, která se má vytvořit. Tento název je založen na názvu, který zadáte v poli **krátký název**, před "C", typické předponou pro název třídy.

- **soubor. cpp**

   Nastaví název implementačního souboru pro třídu nového objektu. Ve výchozím nastavení je tento název založen na názvu, který zadáte v poli **krátký název**. Kliknutím na tlačítko se třemi tečkami uložte název souboru do zvoleného umístění. Soubor není uložen do vybraného umístění, dokud nekliknete na tlačítko **Dokončit** v průvodci.

   Průvodce nepřepisuje soubor. Pokud vyberete název existujícího souboru, po kliknutí na tlačítko **Dokončit**vás průvodce vyzve, abyste označili, zda by měla být implementace třídy připojena k obsahu souboru. Kliknutím na **Ano** přidejte soubor. Kliknutím na **ne** se vrátíte do průvodce a zadáte jiný název souboru.

- **S atributy**

   Určuje, zda objekt používá atributy. Pokud přidáváte objekt do projektu ATL s atributy, je tato možnost vybrána a není k dispozici pro změnu. To znamená, že můžete přidat pouze objekty s atributy do projektu vytvořeného pomocí atributu support.

   Pokud vyberete tuto možnost pro projekt ATL, který nemá podporu atributů, Průvodce vás vyzve, abyste určili, zda chcete přidat do projektu podporu atributů.

   Všechny objekty, které přidáte po nastavení této možnosti, jsou označeny jako atributy ve výchozím nastavení (zaškrtávací políčko je zaškrtnuté). Zaškrtnutím tohoto políčka můžete přidat objekt, který nepoužívá atributy.

   Další informace naleznete v tématu [nastavení aplikace, Průvodce projektem ATL](../../atl/reference/application-settings-atl-project-wizard.md) a [základní mechanismy atributů](../../windows/basic-mechanics-of-attributes.md) .

### <a name="com"></a>Model COM

Poskytuje informace o funkcích modelu COM pro daný objekt.

- **Coclass**

   Nastaví název třídy komponenty, která obsahuje seznam rozhraní podporovaných objektem.

> [!NOTE]
>  Pokud vytvoříte projekt pomocí atributů nebo Pokud označíte na této stránce průvodce, že komponenta COM+ 1,0 používá atributy, nemůžete tuto možnost změnit, protože knihovna ATL neobsahuje atribut `coclass`.

- **Typ**

   Nastaví popis objektu, který se zobrazí v registru.

- **Prostředí**

   Nastaví rozhraní, které jste pro svůj objekt vytvořili. Toto rozhraní obsahuje vaše vlastní metody.

- **ProgID**

   Nastaví název, který mohou kontejnery použít místo identifikátoru CLSID objektu.

::: moniker-end

## <a name="see-also"></a>Viz také

[Komponenta ATL COM+ 1,0](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)
