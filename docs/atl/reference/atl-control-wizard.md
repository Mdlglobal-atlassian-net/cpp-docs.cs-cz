---
title: Průvodce ovládacími prvky ATL | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.control.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding controls
- controls [ATL], adding to projects
- ATL Control Wizard
ms.assetid: 991f8e72-ffbc-4382-a4ce-e255acfba5b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dfadbfb887959aaad01c88cba7c3c04ef5f27873
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066127"
---
# <a name="atl-control-wizard"></a>Průvodce ovládacími prvky ATL

Vloží do projektu knihovny ATL (nebo projektu knihovny MFC s podpory knihovny ATL) ovládacího prvku ATL. Tohoto průvodce můžete použít k vložení tři typy ovládacích prvků:

- Standardní ovládací prvek

- Složený ovládací prvek

- Ovládací prvek DHTML

Kromě toho můžete určit minimální ovládací prvek, odebírá se rozhraní z [rozhraní](../../atl/reference/interfaces-atl-control-wizard.md) seznamu, které jsou k dispozici jako výchozí hodnoty pro ovládací prvky otevřete ve většině kontejnerů. Rozhraní, které chcete, aby podporovaných pro ovládací prvek v lze nastavit **rozhraní** stránky průvodce.

## <a name="remarks"></a>Poznámky

Registrační skript vytvářených Tento průvodce zaregistruje jeho komponenty modelu COM v klíči HKEY_CURRENT_USER místo HKEY_LOCAL_MACHINE. Chcete-li toto chování změnit, nastavte **registrace komponenty pro všechny uživatele** možnost ATL průvodce.

## <a name="names"></a>Názvy

Zadejte názvy objektů, rozhraní a třídy, které se přidají do vašeho projektu. S výjimkou **krátký název**, všechna ostatní pole lze změnit nezávisle na sobě. Pokud se změní text pro **krátký název**, změny se projeví v názvech všechna ostatní pole na této stránce. Pokud změníte **Coclass** název v oddílu modelu COM, tato změna se projeví v **typ** pole, ale **rozhraní** název a **ProgID** provést nelze změnit. Toto chování je navržené tak, aby všechny názvy jednoduše rozpoznatelným názvem za vás při vývoji ovládacího prvku.

> [!NOTE]
>  **Coclass** lze upravit pouze bez atributové ovládacích prvků. Pokud váš projekt s atributy, nelze upravovat **Coclass**.

### <a name="c"></a>C++

Poskytuje informace pro třídy C++ vytvořený pro implementaci objektu.

- **Krátký název**

   Nastaví zkrácený název pro objekt. Určuje název, který zadáte, třídy a **Coclass** názvy, souboru (. CPP a. H) názvů, název rozhraní a **typ** názvy, pokud nezměníte těchto polí samostatně.

- **Třída**

   Nastaví název třídy, která implementuje objekt. Tento název je založen na název, který jste zadali v **krátký název**, předchází "C", typická předpona pro název třídy.

- **soubor .h**

   Nastaví název hlavičkového souboru pro nový objekt třídy. Ve výchozím nastavení, tento název je založen na název, který jste zadali v **krátký název**. Klikněte na tlačítko se třemi tečkami uložení názvu souboru do umístění podle vaší volby, nebo připojit k existujícímu souboru deklaraci třídy. Pokud vyberete existující soubor, Průvodce neuloží se do vybraného umístění dokud kliknutím **Dokončit**.

   Průvodce nepřepisuje soubor. Pokud jste vybrali název existujícího souboru, po kliknutí na **Dokončit**, Průvodce vás vyzve k označení, zda by měla být k obsah souboru připojen deklaraci třídy. Klikněte na tlačítko **Ano** pro připojení k souboru, klikněte na tlačítko **ne** pro návrat do průvodce a zadejte jiný název souboru.

- **soubor .cpp**

   Nastaví název implementačního souboru pro nový objekt třídy. Ve výchozím nastavení, tento název je založen na název, který jste zadali v **krátký název**. Klikněte na tlačítko se třemi tečkami se uložit název souboru do umístění podle vašeho výběru. Soubor se neukládá do vybraného umístění, dokud nekliknete na tlačítko **Dokončit** v průvodci.

   Průvodce nepřepisuje soubor. Pokud jste vybrali název existujícího souboru, po kliknutí na **Dokončit**, Průvodce vás vyzve k označení, zda má být připojen implementace třídy do obsahu souboru. Klikněte na tlačítko **Ano** pro připojení k souboru, klikněte na tlačítko **ne** pro návrat do průvodce a zadejte jiný název souboru.

- **S atributy**

   Označuje, zda objekt používá atributy. Při přidávání objektu do projektu knihovny ATL, tato možnost je vybraný a nelze ji změnit. To znamená můžete přidat pouze objekty s atributy do projektu vytvořeného s podporou atribut.

   Objekt s atributy lze přidat pouze do projektu ATL používající atributy. Pokud vyberete tuto možnost pro projekty ATL, který nemá atribut podporují, Průvodce zobrazí výzvu k určení, zda chcete přidat do projektu podporu atributů.

   Ve výchozím nastavení, všechny objekty, přidejte po nastavení této možnosti jsou označeny jako s přidělenými atributy (zaškrtnuto zaškrtávací políčko). Toto políčko Přidat objekt, který nepoužívá atributy.

   Zobrazit [nastavení aplikace, Průvodce projektem ATL](../../atl/reference/application-settings-atl-project-wizard.md) a [základní mechanismy atributů](../../windows/basic-mechanics-of-attributes.md) Další informace.

### <a name="com"></a>Model COM

Poskytuje informace o funkcích, které modelu COM pro objekt.

- **Coclass**

   Nastaví název třídy komponenty, který obsahuje seznam podporovaných v objektu rozhraní.

   > [!NOTE]
   > Pokud vytváříte projekt pomocí atributů nebo pokud na této stránce průvodce určujete, že ovládací prvek používá atributy, tuto možnost nelze změnit, protože nezahrnuje ATL **coclass** atribut.

- **Rozhraní**

   Nastaví název rozhraní pro objekt. Ve výchozím nastavení název rozhraní začíná "I".

- **Typ**

   Nastaví popis objektu, který se zobrazí v registru

- **ProgID**

   Nastaví název, který kontejnery lze použít místo identifikátor CLSID objektu. Toto pole se vyplní automaticky. Pokud toto pole ručně nevyplníte, nemusí být k dispozici s ostatními nástroji ovládacího prvku. Například ovládací prvky ActiveX, které jsou generovány bez `ProgID` nejsou k dispozici v **vložit ovládací prvek ActiveX** dialogové okno. Další informace o dialogovém okně najdete v tématu [Insert Dialog Box ovládacího prvku ActiveX](../../windows/insert-activex-control-dialog-box.md).

## <a name="see-also"></a>Viz také

[Ovládací prvek ATL](../../atl/reference/adding-an-atl-control.md)<br/>
[Přidání funkcí do složeného ovládacího prvku](../../atl/adding-functionality-to-the-composite-control.md)<br/>
[Základy ATL – objekty COM](../../atl/fundamentals-of-atl-com-objects.md)

