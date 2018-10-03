---
title: ATL COM + 1.0 součást Průvodce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.mts.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding components
- ATL COM+ 1.0 Component Wizard
ms.assetid: 11670681-8671-4122-96a4-2e52f8dadce0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 102ec4f85c8915cf6afb70f03d470cec4e9e807f
ms.sourcegitcommit: d1527eb2d50156bf923f2a32ec3af9efc7fc4304
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2018
ms.locfileid: "48250403"
---
# <a name="atl-com-10-component-wizard"></a>Průvodce komponentami 1.0 knihovny ATL modelu COM +

Tohoto průvodce použijte k přidání objektu do projektu, který podporuje služby COM + 1.0, včetně transakce.

Můžete určit, zda objekt podporuje duální rozhraní a automatizace. Můžete také určit podporu pro rozhraní informace o chybě, vylepšeného objektu ovládacího prvku, transakce a asynchronních zpráv služby Řízení front.

> [!WARNING]
> V sadě Visual Studio 2017 verze 15.9 průvodce tento kód je zastaralá a v budoucí verzi systému Visual Studio se odebere. Tento průvodce je používána zřídka. Obecné podpory knihovny ATL a MFC nemá žádný vliv, odebráním tohoto průvodce. Pokud chcete sdílet svůj názor na toto vyřazení, vyplňte prosím [tento průzkum](https://www.surveymonkey.com/r/QDWKKCN). Vaše zpětná vazba záleží na nás.

## <a name="remarks"></a>Poznámky

Od verze Visual Studio 2008, registrace skriptu vytvářených Tento průvodce zaregistruje jeho komponenty modelu COM v **HKEY_CURRENT_USER** místo **HKEY_LOCAL_MACHINE**. Chcete-li toto chování změnit, nastavte **registrace komponenty pro všechny uživatele** možnost ATL průvodce.

## <a name="names"></a>Názvy

Zadejte názvy objektů, rozhraní a třídy, které se přidají do vašeho projektu. S výjimkou produktů **krátký název**, všechna ostatní pole lze upravit nezávisle na ostatních. Pokud se změní text pro **krátký název**, změny se projeví v názvech všechna ostatní pole na této stránce. Pokud změníte **Coclass** název v oddílu modelu COM, tato změna se projeví v **typ** a **ProgID** polí, ale **rozhraní** název nezmění. Toto chování je navržené tak, aby všechny názvy jednoduše rozpoznatelným názvem za vás při vývoji ovládacího prvku.

- **Krátký název**

   Nastaví zkrácený název pro objekt. Název, který zadáte, určuje `Class` a `Coclass` názvy, **soubor .cpp** a **souboru .h** názvy, **rozhraní** název, **Typ** názvy a **ProgID**, pokud nezměníte těchto polí samostatně.

- **soubor .h**

   Nastaví název hlavičkového souboru pro nový objekt třídy. Ve výchozím nastavení, tento název je založen na název, který jste zadali v **krátký název**. Klikněte na tlačítko se třemi tečkami uložení názvu souboru do umístění podle vaší volby, nebo připojit k existujícímu souboru deklaraci třídy. Pokud zvolíte existující soubor, Průvodce neuloží se do vybraného umístění dokud kliknutím **Dokončit** v průvodci.

   Průvodce nepřepisuje soubor. Pokud jste vybrali název existujícího souboru, po kliknutí na **Dokončit**, Průvodce vás vyzve k označení, zda by měla být k obsah souboru připojen deklaraci třídy. Klikněte na tlačítko **Ano** pro připojení k souboru, klikněte na tlačítko **ne** pro návrat do průvodce a zadejte jiný název souboru.

- **Třída**

   Nastaví název třídy, který se má vytvořit. Tento název je založen na názvu je zadat v **krátký název**, předchází "C", typická předpona pro název třídy.

- **soubor .cpp**

   Nastaví název implementačního souboru pro nový objekt třídy. Ve výchozím nastavení, tento název je založen na názvu je zadat v **krátký název**. Klikněte na tlačítko se třemi tečkami se uložit název souboru do umístění podle vašeho výběru. Soubor se neukládá do vybraného umístění, dokud nekliknete na tlačítko **Dokončit** v průvodci.

   Průvodce nepřepisuje soubor. Pokud jste vybrali název existujícího souboru, po kliknutí na **Dokončit**, Průvodce vás vyzve k označení, zda má být připojen implementace třídy do obsahu souboru. Klikněte na tlačítko **Ano** pro připojení k souboru, klikněte na tlačítko **ne** pro návrat do průvodce a zadejte jiný název souboru.

- **S atributy**

   Označuje, zda objekt používá atributy. Při přidávání objektu do projektu knihovny ATL, tato možnost je vybraný a nelze ji změnit. To znamená můžete přidat pouze objekty s atributy do projektu vytvořeného s podporou atribut.

   Pokud vyberete tuto možnost pro projekty ATL, který nemá atribut podporují, Průvodce zobrazí výzvu k určení, zda chcete přidat do projektu podporu atributů.

   Všechny objekty, přidáte následující nastavení této možnosti jsou označeny jako s atributy ve výchozím nastavení (zaškrtnuto zaškrtávací políčko). Toto políčko Přidat objekt, který nepoužívá atributy.

   Zobrazit [nastavení aplikace, Průvodce projektem ATL](../../atl/reference/application-settings-atl-project-wizard.md) a [základní mechanismy atributů](../../windows/basic-mechanics-of-attributes.md) Další informace.

### <a name="com"></a>Model COM

Poskytuje informace o funkcích, které modelu COM pro objekt.

- **Coclass**

   Nastaví název třídy komponenty, který obsahuje seznam podporovaných v objektu rozhraní.

> [!NOTE]
>  Pokud vytváříte projekt pomocí atributů nebo pokud na této stránce průvodce určujete, že používá komponenty modelu COM + 1.0 atributy, tuto možnost nelze změnit, protože nezahrnuje ATL `coclass` atribut.

- **Typ**

   Nastaví popis objektu, který se zobrazí v registru

- **Rozhraní**

   Nastaví rozhraní, které vytvoříte pro svůj objekt. Toto rozhraní obsahuje vaše vlastní metody.

- **ProgID**

   Nastaví název, který kontejnery lze použít místo identifikátor CLSID objektu.

## <a name="see-also"></a>Viz také

[Komponenta knihovny ATL modelu COM + 1.0](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)

