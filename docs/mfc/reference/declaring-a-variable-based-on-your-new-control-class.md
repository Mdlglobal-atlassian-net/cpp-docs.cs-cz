---
title: Deklarace proměnné založené na nové třídě ovládacího prvku
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.classes.control.variable
helpviewer_keywords:
- variables [MFC], control classes
- control classes [MFC], variables
- classes [MFC], declaring variables based on
ms.assetid: 5722dc38-c0eb-40bd-93da-67a808140d03
ms.openlocfilehash: f79ecb6edec58d26042818d647a0ea121dd41a55
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595686"
---
# <a name="declaring-a-variable-based-on-your-new-control-class"></a>Deklarace proměnné založené na nové třídě ovládacího prvku

Po vytvoření třídy ovládacího prvku knihovny MFC, je možné deklarovat proměnnou na jejím základě. Pro poskytnutí kontextu pro nové proměnné, musíte otevřít editor dialogového okna a dialogových oken, ve které chcete použít opakovaně použitelné ovládací prvek upravit. Dialogové okno musí mít také již třídy s ním spojená. Informace o použití editoru dialogových oken, naleznete v tématu [editoru dialogového okna](../../windows/dialog-editor.md).

### <a name="to-declare-a-variable-based-on-your-reusable-class"></a>Chcete-li deklarovat proměnné založené na opakovaně použitelné třídy

1. Při úpravách dialogových oken, přetáhněte ovládací prvek stejného typu jako základní třída nového ovládacího prvku z panelu nástrojů ovládacích prvků do dialogových oken.

1. Umístěte ukazatel myši nad vynechaných ovládací prvek.

1. Stiskněte klávesu CTRL a poklepejte na ovládací prvek.

   [Přidat členskou proměnnou](../../ide/add-member-variable-wizard.md) zobrazí se dialogové okno.

1. V **přístup** vyberte správný přístup pro ovládací prvek.

1. Klikněte na tlačítko **řídicí proměnná** zaškrtávací políčko.

1. V **název proměnné** zadejte název.

1. V části **kategorie**, klikněte na tlačítko **ovládací prvek**.

1. V **ID ovládacího prvku** seznamu, vyberte ovládací prvek, který jste přidali. **Typ proměnné** seznam by měl zobrazit správný typ proměnné a **ovládací prvek typu** pole zobrazeno správný typ ovládacího prvku.

9. V **komentář** přidejte všechny komentáře, které se mají zobrazit ve vašem kódu.

10. Klikněte na tlačítko **OK**.

## <a name="see-also"></a>Viz také

[Mapování zpráv na funkce](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[Přidání funkce pomocí průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Přidání třídy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Přidání členské funkce](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Přidání členské proměnné](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Přepisování virtuální funkce](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Popisovače zpráv knihovny MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Navigace strukturou třídy](../../ide/navigating-the-class-structure-visual-cpp.md)
