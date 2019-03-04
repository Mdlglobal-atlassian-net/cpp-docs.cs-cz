---
title: Průvodce stránkou vlastností ATL
ms.date: 10/03/2018
f1_keywords:
- vc.codewiz.class.atl.ppg.overview
helpviewer_keywords:
- ATL projects, adding property pages
- ATL Property Page Wizard
ms.assetid: 6113e325-facd-4f68-b491-144d75209922
ms.openlocfilehash: 791901ab3181ad2c8ac862a970980250693d20f7
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57258278"
---
# <a name="atl-property-page-wizard"></a>Průvodce stránkou vlastností ATL

Tento průvodce [přidá stránky vlastností do projektu knihovny ATL](../../atl/reference/adding-an-atl-property-page.md) nebo do projektu MFC pomocí podpory knihovny ATL. Stránky vlastností ATL poskytuje uživatelské rozhraní pro nastavení vlastností (nebo volání metody) z jednoho nebo více objektů COM.

> [!WARNING]
> V sadě Visual Studio 2017 verze 15.9 průvodce tento kód je zastaralá a v budoucí verzi systému Visual Studio se odebere. Tento průvodce je používána zřídka. Obecné podpory knihovny ATL a MFC nemá žádný vliv, odebráním tohoto průvodce. Pokud chcete sdílet svůj názor na toto vyřazení, vyplňte prosím [tento průzkum](https://www.surveymonkey.com/r/QDWKKCN). Vaše zpětná vazba záleží na nás.

## <a name="remarks"></a>Poznámky

Od verze Visual Studio 2008, registrace skriptu vytvářených Tento průvodce zaregistruje jeho komponenty modelu COM v **HKEY_CURRENT_USER** místo **HKEY_LOCAL_MACHINE**. Chcete-li toto chování změnit, nastavte **registrace komponenty pro všechny uživatele** možnost ATL průvodce.

## <a name="names"></a>Názvy

Zadejte názvy objektů, rozhraní a třídy, které se přidají do vašeho projektu. S výjimkou **krátký název**, všechna ostatní pole lze nezávisle upravovat. Pokud se změní text pro **krátký název**, změny se projeví v názvech všechna ostatní pole na této stránce. Pokud změníte **Coclass** název v oddílu modelu COM, tato změna se projeví v **typ** a **ProgID** polí. Toto chování je navržené tak, aby všechny názvy jednoduše rozpoznatelným názvem za vás při vývoji stránky vlastností.

> [!NOTE]
>  **Coclass** lze upravit pouze bez atributové projektů. Pokud váš projekt s atributy, nelze upravovat **Coclass**.

### <a name="c"></a>C++

Poskytuje informace pro třídy C++ vytvořený pro implementaci objektu.

|||
|-|-|
|Termín|Definice|
|**Krátký název**|Nastaví zkrácený název pro objekt. Určuje název, který zadáte, třídy a **Coclass** pojmenuje soubor (**.cpp** a **.h**) názvy, **typ** názvem a  **ProgID**, pokud nezměníte těchto polí samostatně.|
|**.h file**|Nastaví název hlavičkového souboru pro nový objekt třídy. Ve výchozím nastavení, tento název je založen na název, který jste zadali v **krátký název**. Klikněte na tlačítko se třemi tečkami uložení názvu souboru do umístění podle vaší volby, nebo připojit k existujícímu souboru deklaraci třídy. Pokud vyberete existující soubor, Průvodce neuloží se do vybraného umístění dokud kliknutím **Dokončit** v průvodci.<br /><br /> Průvodce nepřepisuje soubor. Pokud jste vybrali název existujícího souboru, po kliknutí na **Dokončit**, Průvodce vás vyzve k označení, zda by měla být k obsah souboru připojen deklaraci třídy. Klikněte na tlačítko **Ano** pro připojení k souboru, klikněte na tlačítko **ne** pro návrat do průvodce a zadejte jiný název souboru.|
|**Třída**|Nastaví název třídy, která implementuje objekt. Tento název je založen na název, který jste zadali v **krátký název**, předchází "C", typická předpona pro název třídy.|
|**soubor .cpp**|Nastaví název implementačního souboru pro nový objekt třídy. Ve výchozím nastavení, tento název je založen na název, který jste zadali v **krátký název**. Klikněte na tlačítko se třemi tečkami se uložit název souboru do umístění podle vašeho výběru. Soubor se neukládá do vybraného umístění, dokud nekliknete na tlačítko **Dokončit** v průvodci.<br /><br /> Průvodce nepřepisuje soubor. Pokud jste vybrali název existujícího souboru, po kliknutí na **Dokončit**, Průvodce vás vyzve k označení, zda má být připojen implementace třídy do obsahu souboru. Klikněte na tlačítko **Ano** pro připojení k souboru, klikněte na tlačítko **ne** pro návrat do průvodce a zadejte jiný název souboru.|
|**S atributy**|Označuje, zda objekt používá atributy. Pokud přidáváte objektu do projektu knihovny ATL, je vybraná tato možnost a nelze ji změnit, to znamená, můžete přidat pouze s atributy objektů do projektu vytvořeného s podporou atribut.<br /><br /> Objekt s atributy lze přidat pouze do projektu ATL používající atributy. Pokud vyberete tuto možnost pro projekty ATL, který nemá atribut podporují, Průvodce zobrazí výzvu k určení, zda chcete přidat do projektu podporu atributů.<br /><br /> Ve výchozím nastavení, všechny objekty, přidejte po nastavení této možnosti jsou označeny jako s přidělenými atributy (zaškrtnuto zaškrtávací políčko). Toto políčko Přidat objekt, který nepoužívá atributy.<br /><br /> Zobrazit [nastavení aplikace, Průvodce projektem ATL](../../atl/reference/application-settings-atl-project-wizard.md) a [základní mechanismy atributů](../../windows/basic-mechanics-of-attributes.md) Další informace.|

### <a name="com"></a>Model COM

Poskytuje informace o funkcích, které modelu COM pro objekt.

- **Coclass**

   Nastaví název třídy komponenty, který obsahuje seznam podporovaných v objektu rozhraní.

   > [!NOTE]
   > Pokud vytváříte projekt pomocí atributů nebo pokud na této stránce průvodce určujete, že na stránce vlastností používá atributy, tuto možnost nelze změnit, protože nezahrnuje ATL `coclass` atribut.

- **Typ**

   Nastaví popis objektu, který se zobrazí v registru

- **ProgID**

   Nastaví název, který kontejnery lze použít místo identifikátor CLSID objektu.

## <a name="see-also"></a>Viz také:

[Možnosti Průvodce stránkou vlastností ATL](../../atl/reference/options-atl-property-page-wizard.md)<br/>
[Řetězce, Průvodce stránkou vlastností ATL](../../atl/reference/strings-atl-property-page-wizard.md)<br/>
[Příklad: Implementace stránky vlastností](../../atl/example-implementing-a-property-page.md)
