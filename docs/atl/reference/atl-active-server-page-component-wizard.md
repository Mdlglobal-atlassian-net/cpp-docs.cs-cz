---
title: Průvodce komponentami stránka ATL Active Server
ms.date: 05/09/2019
helpviewer_keywords:
- ASP components, creating in ATL
ms.assetid: 5a5cb904-dbbf-44ea-ad3d-2ddd14c1d3c5
ms.openlocfilehash: a78beeab663ef1b467cdec32ca51132e8134a9b2
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707043"
---
# <a name="atl-active-server-page-component-wizard"></a>Průvodce komponentami stránka ATL Active Server

::: moniker range="vs-2019"

Tento průvodce není k dispozici v aplikaci Visual Studio 2019 a novějším.

::: moniker-end

::: moniker range="<=vs-2017"

Tento průvodce se vloží do projektu jako součást stránky ASP (Active Server). Microsoft Internetové informační služby (IIS) používá jako součást jeho architektuře vývoj rozšířená webová stránka ASP součásti.

Pomocí tohoto průvodce můžete určit, že se že procesu komponenty modelu a jeho podporu agregace. Můžete také určit podporu pro rozhraní informace o chybě, spojovací body a volných vláken zařazování.

## <a name="remarks"></a>Poznámky

Od verze Visual Studio 2008, registrace skriptu vytvářených Tento průvodce zaregistruje jeho komponenty modelu COM v **HKEY_CURRENT_USER** místo **HKEY_LOCAL_MACHINE**. Chcete-li toto chování změnit, nastavte **registrace komponenty pro všechny uživatele** možnost ATL průvodce.

## <a name="names"></a>Názvy

Zadejte názvy objektů, rozhraní a třídy, které se přidají do vašeho projektu. S výjimkou **krátký název**, všechna ostatní pole lze upravit nezávisle na ostatních. Pokud se změní text pro **krátký název**, změny se projeví v názvech všechna ostatní pole na této stránce.

Pokud změníte **Coclass** název v oddílu modelu COM, tato změna se projeví v **typ** a **ProgID** polí, ale **rozhraní** název nezmění. Toto chování je navržené tak, aby všechny názvy jednoduše rozpoznatelným názvem za vás při vývoji ovládacího prvku.

### <a name="c"></a>C++

Poskytuje informace pro třídu C++ vytvořené pro objekt.

- **Krátký název**

   Nastaví název kořenového objektu. Název, který zadáte, určuje `Class` a **Coclass** názvy, **soubor .cpp** a **souboru .h** názvy, **rozhraní**název, **typ** názvy a **ProgID**, pokud nezměníte těchto polí samostatně.

- **.h file**

   Nastaví název hlavičkového souboru pro nový objekt třídy. Ve výchozím nastavení, tento název je založen na název, který jste zadali v **krátký název**. Klikněte na tlačítko se třemi tečkami uložení názvu souboru do umístění podle vaší volby, nebo připojit k existujícímu souboru deklaraci třídy. Pokud vyberete existující soubor, Průvodce neuloží se do vybraného umístění dokud kliknutím **Dokončit** v průvodci.

   Průvodce nepřepisuje soubor. Pokud jste vybrali název existujícího souboru, po kliknutí na **Dokončit**, Průvodce vás vyzve k označení, zda by měla být k obsah souboru připojen deklaraci třídy. Klikněte na tlačítko **Ano** pro připojení k souboru, klikněte na tlačítko **ne** pro návrat do průvodce a zadejte jiný název souboru.

- **Třída**

   Nastaví název třídy, který se má vytvořit. Tento název je založen na název, který jste zadali v **krátký název**, předchází "C", typická předpona pro název třídy.

- **soubor .cpp**

   Nastaví název implementačního souboru pro nový objekt třídy. Ve výchozím nastavení, tento název je založen na název, který jste zadali v **krátký název**. Klikněte na tlačítko se třemi tečkami se uložit název souboru do umístění podle vašeho výběru. Soubor se neukládá do vybraného umístění, dokud nekliknete na tlačítko **Dokončit** v průvodci.

   Průvodce nepřepisuje soubor. Pokud jste vybrali název existujícího souboru, po kliknutí na **Dokončit**, Průvodce vás vyzve k označení, zda má být připojen implementace třídy do obsahu souboru. Klikněte na tlačítko **Ano** pro připojení k souboru, klikněte na tlačítko **ne** pro návrat do průvodce a zadejte jiný název souboru.

- **S atributy**

   Označuje, zda objekt používá atributy. Při přidávání objektu do projektu knihovny ATL, tato možnost je vybraný a nelze ji změnit. To znamená můžete přidat pouze objekty s atributy do projektu vytvořeného s podporou atribut.

   Pokud vyberete tuto možnost pro projekty ATL, který nemá atribut podporují, Průvodce zobrazí výzvu k určení, zda chcete přidat do projektu podporu atributů.

   Ve výchozím nastavení bez atributových projektů, všechny objekty, přidejte po nastavení této možnosti jsou označeny jako s přidělenými atributy (zaškrtnuto zaškrtávací políčko). Toto políčko Přidat objekt, který nepoužívá atributy.

   Zobrazit [nastavení aplikace, Průvodce projektem ATL](../../atl/reference/application-settings-atl-project-wizard.md) a [základní mechanismy atributů](../../windows/basic-mechanics-of-attributes.md) Další informace.

### <a name="com"></a>Model COM

Poskytuje informace o funkcích, které modelu COM pro objekt.

- **Coclass**

   Nastaví název třídy komponenty, který obsahuje seznam podporovaných v objektu rozhraní. Pokud váš projekt nebo tento objekt používá atributy, tuto možnost nelze změnit, protože nezahrnuje ATL **coclass** atribut.

- **Typ**

   Nastaví popis objektu, který se zobrazí v registru pro coclass.

- **Rozhraní**

   Nastaví rozhraní, které vytvoříte pro svůj objekt. Toto rozhraní obsahuje vaše vlastní metody.

- **ProgID**

   Nastaví název, který kontejnery lze použít místo identifikátor CLSID objektu.

::: moniker-end

## <a name="see-also"></a>Viz také:

[Komponenta knihovny ATL Active Server Page](../../atl/reference/adding-an-atl-active-server-page-component.md)
