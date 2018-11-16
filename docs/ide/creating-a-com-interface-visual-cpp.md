---
title: Vytváření rozhraní modelu COM
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.com.creating.interfaces
- vc.codewiz.com.editing.interfaces
helpviewer_keywords:
- COM interfaces, creating
- methods [C++], adding to COM interfaces
- COM interfaces, editing
- properties [C++], adding to COM interfaces
ms.assetid: 1be84d3c-6886-4d1e-8493-56c4d38a96d4
ms.openlocfilehash: dfc4b09f4fa42b179bdef91877e0a004caa69187
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693698"
---
# <a name="create-a-com-interface"></a>Vytváření rozhraní modelu COM

Průvodci a šablony, pokud chcete vytvářet projekty, které používají rozhraní COM a odesílající rozhraní pro objekty COM a automatizační třídy poskytuje jazyk Visual C++.

Použití těchto průvodců a proveďte následující tři běžné úlohy:

- [Přidat podporu ATL do projektu knihovny MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md).

  Přidat podporu ATL do MFC aplikace po vytvoření projektu knihovny MFC pomocí [Průvodce aplikací knihovny MFC](../mfc/reference/mfc-application-wizard.md) a následné spuštění **přidání podpory knihovny ATL do MFC** Průvodce kódem. Tato podpora se vztahuje pouze na jednoduché objekty modelu COM, přidat do spustitelného souboru knihovny MFC ani do projektu knihovny DLL. Tyto objekty knihovny ATL může mít více než jedno rozhraní.

- [Vytvoření ovládacího prvku ActiveX knihovny MFC](../mfc/reference/creating-an-mfc-activex-control.md).

  Otevřít [Průvodce ovládacím prvkem MFC ActiveX](../mfc/reference/mfc-activex-control-wizard.md) vytvoření ovládacího prvku ActiveX dispinterface a mapu událostí definovaných v souboru IDL a třídu ovládacího prvku, v uvedeném pořadí.

- [Přidání ovládacího prvku ATL](../atl/reference/adding-an-atl-control.md).

  Pomocí kombinace [Průvodce projektem ATL](../atl/reference/atl-project-wizard.md) a [Průvodce ovládacími prvky ATL](../atl/reference/atl-control-wizard.md) vytvořit ovládací prvek ActiveX knihovny ATL.

  Můžete také přidat ovládacího prvku ATL do projektu knihovny MFC, do které jste přidali podporu ATL, jak je popsáno výše. Kromě toho pokud vyberete **ovládací prvek ATL** v **přidat třídu** dialogové okno kde ještě nepřidali podporu ATL do projektu knihovny MFC, Visual Studio zobrazí dialogové okno, která potvrzuje přidání podpory knihovny ATL do vaší Projekt knihovny MFC.

  Tento průvodce vygeneruje zdroj IDL a mapy modelu COM ve třídách projektu.

Jakmile projekt knihovny ATL, otevřít, [přidat třídu](../ide/add-class-dialog-box.md) dialogové okno umožňuje volbu Další průvodci a šablony pro přidání rozhraní modelu COM do vašeho projektu. Následující průvodci vám umožňují vytvořit jeden nebo více rozhraní pro objekt:

- [Průvodce komponentami ATL COM + 1.0](../atl/reference/atl-com-plus-1-0-component-wizard.md)
- [Průvodce jednoduchým objektem ATL](../atl/reference/atl-simple-object-wizard.md)
- [Průvodce komponentami ATL active server page](../atl/reference/atl-active-server-page-component-wizard.md)
- [Průvodce ovládacími prvky ATL](../atl/reference/atl-control-wizard.md)

Kromě toho můžete implementovat nové rozhraní ovládacího prvku COM. Stačí klikněte pravým tlačítkem objekt třídy ovládacího prvku v zobrazení tříd a zvolit možnost [implementovat rozhraní](../ide/implement-interface-wizard.md).

> [!NOTE]
> Visual Studio neposkytuje průvodce můžete přidat rozhraní do projektu. Můžete přidat rozhraní do projektu knihovny ATL nebo do [podpory knihovny ATL přidat do projektu knihovny MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) tak Přidání jednoduchého objektu pomocí [Průvodce jednoduchým objektem ATL](../atl/reference/atl-simple-object-wizard.md). Můžete také otevřít soubor .idl projektu a vytvořte rozhraní tak, že zadáte:

```
interface IMyInterface {
};
```

Další informace najdete v tématu [implementovat rozhraní](../ide/implementing-an-interface-visual-cpp.md) a [přidání objektů a ovládacích prvků do projektu ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md).

Visual C++ poskytuje několik způsobů, jak zobrazit a [úpravy rozhraní modelu COM](#edit-a-com-interface) definované pro vaše projekty. [Zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code) zobrazuje ikony pro jakékoli rozhraní nebo dispinterface definované v souboru IDL v projektu jazyka C++.

Zobrazení tříd pro objekt třídy založený na knihovně ATL COM, přečte mapy modelu COM v ATL – třídy zobrazíte vztah mezi ATL – třídy a rozhraní, které implementuje.

V zobrazení tříd a jeho místní nabídky můžete pracovat s rozhraním následujícím způsobem:

- Přidáte objekty knihovny ATL do aplikace založené na knihovně MFC.
- Přidejte metody, vlastnosti a události.
- Dvojitým kliknutím na položku přejít přímo do kódu rozhraní položky.

## <a name="in-this-section"></a>V tomto oddílu

- [Úpravy rozhraní modelu COM](#edit-a-com-interface)

## <a name="edit-a-com-interface"></a>Úpravy rozhraní modelu COM

Pomocí příkazů v místní nabídce Zobrazení tříd můžete definovat nové metody a vlastnosti pro rozhraní modelu COM v projektech Visual C++. Z panelu nástrojů můžete také definovat události pro ovládací prvky ActiveX.

Pro třídy objektů knihovny ATL a MFC-založené na modelu COM můžete upravit implementace třídy ve stejnou dobu, abyste upravili rozhraní.

> [!NOTE]
> Pro rozhraní, které jste definovali mimo **přidat třídu** dialogovém okně Visual C++ přidá do souboru IDL metody nebo vlastnosti, a přidá do třídy, které implementují metody, i když rozhraní přidáváte ručně.

Následující tři průvodce vám umožní přizpůsobit existující rozhraní. Jsou k dispozici ze zobrazení tříd:

|Průvodce|Typ projektu|
|------------|------------------|
|[Průvodce přidáním vlastnosti](../ide/names-add-property-wizard.md)|Projekty knihovny ATL nebo MFC podpůrné knihovny ATL. Klikněte pravým tlačítkem na rozhraní, ke kterému chcete přidat vlastnost.<br /><br />Visual C++ zjistí, že typ projektu a upraví možnosti v Průvodce přidáním vlastnosti podle potřeby:<br /><br />-Pro odesílacích rozhraních v projekty vytvořené pomocí [Průvodce aplikací knihovny MFC](../mfc/reference/mfc-application-wizard.md), vyvolání Průvodce přidáním vlastnosti poskytuje možnosti konkrétní ke knihovně MFC.<br />-Pro rozhraní ovládací prvek ActiveX knihovny MFC Průvodce přidáním vlastnosti obsahuje seznam uložených metod a vlastností, které můžete použít podle nebo upravit pro ovládací prvek.<br />-Pro všechny ostatní rozhraní Průvodci přidat vlastnost poskytují možnosti užitečné ve většině situací.|
|[Průvodce přidáním metody](../ide/add-method-wizard.md)|Projekty knihovny ATL nebo MFC podpůrné knihovny ATL. Klikněte pravým tlačítkem na rozhraní, ke kterému chcete přidat metodu.<br /><br />Visual C++ zjistí, že typ projektu a upraví možnosti v Průvodci přidáním metoda podle potřeby:<br /><br />-Pro odesílacích rozhraních v projekty vytvořené pomocí [Průvodce aplikací knihovny MFC](../mfc/reference/mfc-application-wizard.md), pomocí Průvodce přidáním metody poskytuje možnosti konkrétní ke knihovně MFC.<br />-Pro rozhraní ovládací prvek ActiveX knihovny MFC Průvodce přidáním metody obsahuje seznam uložených metod a vlastností, které můžete použít podle nebo upravit pro ovládací prvek.<br />-Pro všechny ostatní rozhraní **přidat metodu** průvodci poskytují možnosti užitečné ve většině situací.|

Kromě toho můžete implementovat nové rozhraní ovládacího prvku COM. Stačí klikněte pravým tlačítkem objekt třídy ovládacího prvku v zobrazení tříd a zvolit možnost [implementovat rozhraní](../ide/implement-interface-wizard.md).
