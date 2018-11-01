---
title: Úpravy rozhraní modelu COM
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.com.editing.interfaces
helpviewer_keywords:
- methods [C++], adding to COM interfaces
- COM interfaces, editing
- properties [C++], adding to COM interfaces
ms.assetid: 6c2909e0-af2d-4a37-bb39-ed372e6129cf
ms.openlocfilehash: 338782cbf7cc302c285e8e778389ae28e20f2b14
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50657363"
---
# <a name="editing-a-com-interface"></a>Úpravy rozhraní modelu COM

Pomocí příkazů v místní nabídce Zobrazení tříd můžete definovat nové metody a vlastnosti pro rozhraní modelu COM v projektech Visual C++. Kromě toho z panelu nástrojů můžete definovat události pro ovládací prvky ActiveX.

Pro třídy objektů knihovny ATL a MFC-založené na modelu COM můžete upravit implementace třídy ve stejnou dobu, abyste upravili rozhraní.

> [!NOTE]
>  Pro rozhraní, které jste definovali mimo **přidat třídu** dialogovém okně Visual C++ přidá do souboru IDL metody nebo vlastnosti, a přidá do třídy, které implementují metody, i když rozhraní přidáváte ručně.

Následující tři průvodce vám umožní přizpůsobit existující rozhraní. Jsou k dispozici ze zobrazení tříd:

|Průvodce|Typ projektu|
|------------|------------------|
|[Průvodce přidáním vlastnosti](../ide/names-add-property-wizard.md)|Projekty knihovny ATL nebo MFC podpůrné knihovny ATL. Klikněte pravým tlačítkem na rozhraní, ke kterému chcete přidat vlastnost.<br /><br />Visual C++ zjistí tento typ projektů a odpovídajícím způsobem mění možnosti v průvodci Přidat vlastnost:<br /><br />-Pro odesílacích rozhraních v projekty vytvořené pomocí [Průvodce aplikací knihovny MFC](../mfc/reference/mfc-application-wizard.md), vyvolání Průvodce přidáním vlastnosti poskytuje možnosti konkrétní ke knihovně MFC.<br />-Pro rozhraní ovládací prvek ActiveX knihovny MFC Průvodce přidáním vlastnosti obsahuje seznam uložených metod a vlastností, které můžete použít podle nebo upravit pro ovládací prvek.<br />-Pro všechny ostatní rozhraní Průvodci přidat vlastnost poskytují možnosti užitečné ve většině situací.|
|[Průvodce přidáním metody](../ide/add-method-wizard.md)|Projekty knihovny ATL nebo MFC podpůrné knihovny ATL. Klikněte pravým tlačítkem na rozhraní, ke kterému chcete přidat metodu.<br /><br />Visual C++ zjistí tento typ projektů a odpovídajícím způsobem mění možnosti Průvodce přidáním metody:<br /><br />-Pro odesílacích rozhraních v projekty vytvořené pomocí [Průvodce aplikací knihovny MFC](../mfc/reference/mfc-application-wizard.md), Průvodce přidáním metody vyvolání poskytuje možnosti konkrétní ke knihovně MFC.<br />-Pro rozhraní ovládací prvek ActiveX knihovny MFC Průvodce přidáním metody obsahuje seznam uložených metod a vlastností, které můžete použít podle nebo upravit pro ovládací prvek.<br />-Pro všechny ostatní rozhraní **přidat metodu** průvodci poskytují možnosti užitečné ve většině situací.|

Kromě toho můžete implementovat nové rozhraní ovládacího prvku COM tak, že kliknete pravým tlačítkem objekt třídy ovládacího prvku v zobrazení tříd a kliknete [implementovat rozhraní](../ide/implement-interface-wizard.md).

## <a name="see-also"></a>Viz také

[Práce se zdrojovými soubory](../windows/working-with-resource-files.md)<br>
[Přidání funkce pomocí průvodců kódem](../ide/adding-functionality-with-code-wizards-cpp.md)<br>
[Typy projektů Visual C++](../ide/visual-cpp-project-types.md)