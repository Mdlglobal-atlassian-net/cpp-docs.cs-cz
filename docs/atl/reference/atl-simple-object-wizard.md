---
title: Průvodce jednoduchého objektu knihovny ATL | Microsoft Docs
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
ms.openlocfilehash: 0ff9648cfc350f724a333e38622d082d8d399b3b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363966"
---
# <a name="atl-simple-object-wizard"></a>Průvodce jednoduchého objektu knihovny ATL
Tento průvodce vloží do projektu minimální objektu COM. Na této stránce průvodce můžete zadat názvy, které identifikují třídami C++ a soubory pro objektu a jeho funkce COM.  
  
 Použití [možnosti](../../atl/reference/options-atl-simple-object-wizard.md) stránce tohoto průvodce k určení modelu vláken objektu, jeho agregace podporují, a zda podporuje duální rozhraní a automatizace. Můžete také indikovat podporu pro rozhraní informace o chybě, spojovací body, podporu aplikace Internet Explorer a volného zařazování vláken.  
  
## <a name="remarks"></a>Poznámky  
 Počínaje verzí Visual Studio 2008, registrace skript vytvořený tímto průvodcem bude registrovat jeho komponenty COM v **HKEY_CURRENT_USER** místo **HKEY_LOCAL_MACHINE**. Chcete-li toto chování změnit, nastavte **zaregistrovat součást pro všechny uživatele** možnost ATL průvodce.  
  
## <a name="names"></a>Názvy  
 Zadejte názvy objektů, rozhraní a třídy, který se má přidat do projektu. S výjimkou **krátký název**, všechna ostatní pole můžete upravovat nezávisle na ostatních. Pokud změníte text pro **krátký název**, změny se projeví v názvech všechna ostatní pole na této stránce. Pokud změníte **třída typu Coclass** název v oddílu modelu COM, změna se odrazí v **typ** a **ProgID** polí, ale **rozhraní** název nezmění. Toto chování je navržená tak, aby bylo možné všechny názvy snadno identifikovat jako vývoje ovládacího prvku.  
  
> [!NOTE]
>  **Třída typu coclass** upravovat pouze neoznačené atributy projektů. Pokud váš projekt s atributy, nelze upravovat **třída typu Coclass**.  
  
## <a name="c"></a>C++  
 Poskytuje informace o třídě C++ vytvořené pro objekt.  
  
 **Krátký název**  
 Nastaví zkrácený název objektu. Název, který zadáte určuje `Class` a **třída typu Coclass** názvy, **souboru** a **soubor h** názvy, **rozhraní**název, **typ** názvy a **ProgID**, pokud nezměníte tato pole jednotlivě.  
  
 **soubor h**  
 Nastaví název hlavičky souboru pro nový objekt třídy. Ve výchozím nastavení, tento název je založen na název, který zadáte v **krátký název**. Klikněte na tlačítko se třemi tečkami uložení názvu souboru do umístění podle vaší volby nebo připojit k existující soubor deklaraci třídy. Pokud vyberete existující soubor, průvodce jej neuloží do vybraného umístění dokud klikněte na tlačítko **Dokončit** v průvodci.  
  
 Průvodce nepřepisuje soubor. Pokud vyberete název existující soubor, po kliknutí na tlačítko **Dokončit**, Průvodce zobrazí výzvu k označení, zda by měl být deklaraci třídy přiložit k obsahu souboru. Klikněte na tlačítko **Ano** pro připojení k souboru; klikněte na tlačítko **ne** se vraťte do průvodce a zadejte jiný název souboru.  
  
 **– Třída**  
 Nastaví název třídy, který se má vytvořit. Tento název je založen na název, který zadáte v **krátký název**, předcházet "C", typická předpona pro název třídy.  
  
 **souboru**  
 Nastaví název souboru implementace pro nový objekt třídu. Ve výchozím nastavení, tento název je založen na název, který zadáte v **krátký název**. Klikněte na tlačítko se třemi tečkami uložíte soubor do umístění podle vaší volby. Soubor se neuloží do vybraného umístění, dokud nekliknete na tlačítko **Dokončit** v průvodci.  
  
 Průvodce nepřepisuje soubor. Pokud vyberete název existující soubor, po kliknutí na tlačítko **Dokončit**, Průvodce zobrazí výzvu k označení, zda by měl být implementaci třídy přiložit k obsahu souboru. Klikněte na tlačítko **Ano** pro připojení k souboru; klikněte na tlačítko **ne** se vraťte do průvodce a zadejte jiný název souboru.  
  
 **S atributy**  
 Označuje, zda objekt používá atributy. Při přidávání objektu do projektu knihovny ATL, tato možnost je vybrané a nelze ji změnit. To znamená můžete přidat pouze objekty s atributy do projektu vytvořeného s podporou atribut.  
  
 Objekt s atributy můžete přidat pouze do projektu knihovny ATL, který používá atributy. Pokud vyberete tuto možnost pro projekt ATL, který nemá atribut podporovat, Průvodce zobrazí výzvu k určení, zda chcete přidat podporu atributů do projektu.  
  
 Ve výchozím nastavení, všechny objekty, přidejte po nastavení této možnosti jsou označeny jako s atributy (je zaškrtnuté políčko). Toto políčko Přidat objekt, který nepoužívá atributy.  
  
 V tématu [nastavení aplikace, Průvodce projektem ATL](../../atl/reference/application-settings-atl-project-wizard.md) a [základní mechanismy atributů](../../windows/basic-mechanics-of-attributes.md) Další informace.  
  
## <a name="com"></a>Model COM  
 Poskytuje informace o funkci COM pro objekt.  
  
 **Třída typu coclass**  
 Nastaví název třídy komponenta, která obsahuje seznam podporovaných objektem rozhraní.  
  
> [!NOTE]
>  Pokud vytvoříte projekt pomocí atributů, nebo pokud jste uvedli na této stránce průvodce, že objekt používá atributy, tuto možnost nelze změnit, protože knihovna ATL nezahrnuje `coclass` atribut.  
  
 **Typ**  
 Nastaví popis objektu, který se zobrazí v registru  
  
 **Rozhraní**  
 Nastaví rozhraní, které vytvoříte pro objekt. Toto rozhraní obsahuje vaše vlastní metody.  
  
 **ProgID**  
 Nastaví název, který můžete použít kontejnery místo CLSID objektu.  
  
## <a name="see-also"></a>Viz také  
 [Jednoduchého objektu knihovny ATL](../../atl/reference/adding-an-atl-simple-object.md)

