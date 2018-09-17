---
title: Průvodce jednoduchým objektem ATL | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.simple.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding objects
- ATL Simple Object Wizard
ms.assetid: f7f85741-9aad-4543-a917-a29b996364da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 871e27b4a28299e6a3c96f7249f4636f412001d8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723616"
---
# <a name="atl-simple-object-wizard"></a>Průvodce jednoduchým objektem ATL

Tento průvodce se vloží do projektu objekt modelu COM minimální. Na této stránce průvodce nazvat, které identifikují třídy jazyka C++ a soubory pro váš objekt a jeho funkcí modelu COM.

Použití [možnosti](../../atl/reference/options-atl-simple-object-wizard.md) podporují stránce tohoto průvodce k určení modelu vláken objektu, jeho agregace a zda podporuje duální rozhraní a automatizace. Můžete také určit podporu pro rozhraní informace o chybě, spojovací body, Internet Explorer podporují a volných vláken zařazování.

## <a name="remarks"></a>Poznámky

Od verze Visual Studio 2008, registrace skriptu vytvářených Tento průvodce zaregistruje jeho komponenty modelu COM v **HKEY_CURRENT_USER** místo **HKEY_LOCAL_MACHINE**. Chcete-li toto chování změnit, nastavte **registrace komponenty pro všechny uživatele** možnost ATL průvodce.

## <a name="names"></a>Názvy

Zadejte názvy objektů, rozhraní a třídy, které se přidají do vašeho projektu. S výjimkou **krátký název**, všechna ostatní pole lze upravit nezávisle na ostatních. Pokud se změní text pro **krátký název**, změny se projeví v názvech všechna ostatní pole na této stránce. Pokud změníte **Coclass** název v oddílu modelu COM, tato změna se projeví v **typ** a **ProgID** polí, ale **rozhraní** název nezmění. Toto chování je navržené tak, aby všechny názvy jednoduše rozpoznatelným názvem za vás při vývoji ovládacího prvku.

> [!NOTE]
>  **Coclass** lze upravit pouze bez atributové projektů. Pokud váš projekt s atributy, nelze upravovat **Coclass**.

## <a name="c"></a>C++

Poskytuje informace pro třídu C++ vytvořené pro objekt.

- **Krátký název**

   Nastaví zkrácený název pro objekt. Název, který zadáte, určuje `Class` a `Coclass` názvy, **soubor .cpp** a **souboru .h** názvy, **rozhraní** název, **Typ** názvy a **ProgID**, pokud nezměníte těchto polí samostatně.

- **soubor .h**

   Nastaví název hlavičkového souboru pro nový objekt třídy. Ve výchozím nastavení, tento název je založen na název, který jste zadali v **krátký název**. Klikněte na tlačítko se třemi tečkami uložení názvu souboru do umístění podle vaší volby, nebo připojit k existujícímu souboru deklaraci třídy. Pokud vyberete existující soubor, Průvodce neuloží se do vybraného umístění dokud kliknutím **Dokončit** v průvodci.

   Průvodce nepřepisuje soubor. Pokud jste vybrali název existujícího souboru, po kliknutí na **Dokončit**, Průvodce vás vyzve k označení, zda by měla být k obsah souboru připojen deklaraci třídy. Klikněte na tlačítko **Ano** pro připojení k souboru, klikněte na tlačítko **ne** pro návrat do průvodce a zadejte jiný název souboru.

- **Třída**

   Nastaví název třídy, který se má vytvořit. Tento název je založen na název, který jste zadali v **krátký název**, předchází "C", typická předpona pro název třídy.

- **soubor .cpp**

   Nastaví název implementačního souboru pro nový objekt třídy. Ve výchozím nastavení, tento název je založen na název, který jste zadali v **krátký název**. Klikněte na tlačítko se třemi tečkami se uložit název souboru do umístění podle vašeho výběru. Soubor se neukládá do vybraného umístění, dokud nekliknete na tlačítko **Dokončit** v průvodci.

   Průvodce nepřepisuje soubor. Pokud jste vybrali název existujícího souboru, po kliknutí na **Dokončit**, Průvodce vás vyzve k označení, zda má být připojen implementace třídy do obsahu souboru. Klikněte na tlačítko **Ano** pro připojení k souboru, klikněte na tlačítko **ne** pro návrat do průvodce a zadejte jiný název souboru.

- **S atributy**

   Označuje, zda objekt používá atributy. Při přidávání objektu do projektu knihovny ATL, tato možnost je vybraný a nelze ji změnit. To znamená můžete přidat pouze objekty s atributy do projektu vytvořeného s podporou atribut.

   Objekt s atributy lze přidat pouze do projektu ATL používající atributy. Pokud vyberete tuto možnost pro projekty ATL, který nemá atribut podporují, Průvodce zobrazí výzvu k určení, zda chcete přidat do projektu podporu atributů.

   Ve výchozím nastavení, všechny objekty, přidejte po nastavení této možnosti jsou označeny jako s přidělenými atributy (zaškrtnuto zaškrtávací políčko). Toto políčko Přidat objekt, který nepoužívá atributy.

   Zobrazit [nastavení aplikace, Průvodce projektem ATL](../../atl/reference/application-settings-atl-project-wizard.md) a [základní mechanismy atributů](../../windows/basic-mechanics-of-attributes.md) Další informace.

## <a name="com"></a>Model COM

Poskytuje informace o funkcích, které modelu COM pro objekt.

- **Coclass**

   Nastaví název třídy komponenty, který obsahuje seznam podporovaných v objektu rozhraní.

   > [!NOTE]
   > Pokud vytváříte projekt pomocí atributů nebo pokud na této stránce průvodce určujete, že objekt používá atributy, tuto možnost nelze změnit, protože nezahrnuje ATL `coclass` atribut.

- **Typ**

   Nastaví popis objektu, který se zobrazí v registru

- **Rozhraní**

   Nastaví rozhraní, které vytvoříte pro svůj objekt. Toto rozhraní obsahuje vaše vlastní metody.

- **ProgID**

   Nastaví název, který kontejnery lze použít místo identifikátor CLSID objektu.

## <a name="see-also"></a>Viz také

[Jednoduchý objekt knihovny ATL](../../atl/reference/adding-an-atl-simple-object.md)

