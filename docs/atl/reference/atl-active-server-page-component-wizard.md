---
title: Průvodce komponentami stránka ATL Active Server | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.asp.overview
dev_langs:
- C++
helpviewer_keywords:
- ASP components, creating in ATL
- ATL Active Server Page Component Wizard
ms.assetid: 5a5cb904-dbbf-44ea-ad3d-2ddd14c1d3c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8a87b2ba1e846ce995a987379ae6f30567a39773
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053809"
---
# <a name="atl-active-server-page-component-wizard"></a>Průvodce komponentami stránka ATL Active Server

Tento průvodce se vloží do projektu jako součást stránky ASP (Active Server). Microsoft Internetové informační služby (IIS) používá jako součást jeho architektuře vývoj rozšířená webová stránka ASP součásti.

Pomocí tohoto průvodce můžete určit, že se že procesu komponenty modelu a jeho podporu agregace. Můžete také určit podporu pro rozhraní informace o chybě, spojovací body a volných vláken zařazování.

> [!WARNING]
> V sadě Visual Studio 2017 verze 15.9 průvodce tento kód je zastaralá a v budoucí verzi systému Visual Studio se odebere. Tento průvodce je používána zřídka. Obecné podpory knihovny ATL a MFC nemá žádný vliv, odebráním tohoto průvodce. Pokud chcete sdílet svůj názor na toto vyřazení, vyplňte prosím [tento průzkum](https://www.surveymonkey.com/r/QDWKKCN). Vaše zpětná vazba záleží na nás.

## <a name="remarks"></a>Poznámky

Od verze Visual Studio 2008, registrace skriptu vytvářených Tento průvodce zaregistruje jeho komponenty modelu COM v **HKEY_CURRENT_USER** místo **HKEY_LOCAL_MACHINE**. Chcete-li toto chování změnit, nastavte **registrace komponenty pro všechny uživatele** možnost ATL průvodce.

## <a name="names"></a>Názvy

Zadejte názvy objektů, rozhraní a třídy, které se přidají do vašeho projektu. S výjimkou **krátký název**, všechna ostatní pole lze upravit nezávisle na ostatních. Pokud se změní text pro **krátký název**, změny se projeví v názvech všechna ostatní pole na této stránce.

Pokud změníte **Coclass** název v oddílu modelu COM, tato změna se projeví v **typ** a **ProgID** polí, ale **rozhraní** název nezmění. Toto chování je navržené tak, aby všechny názvy jednoduše rozpoznatelným názvem za vás při vývoji ovládacího prvku.

### <a name="c"></a>C++

Poskytuje informace pro třídu C++ vytvořené pro objekt.

- **Krátký název**

   Nastaví název kořenového objektu. Název, který zadáte, určuje `Class` a **Coclass** názvy, **soubor .cpp** a **souboru .h** názvy, **rozhraní**název, **typ** názvy a **ProgID**, pokud nezměníte těchto polí samostatně.

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

## <a name="see-also"></a>Viz také

[Komponenta knihovny ATL Active Server Page](../../atl/reference/adding-an-atl-active-server-page-component.md)
