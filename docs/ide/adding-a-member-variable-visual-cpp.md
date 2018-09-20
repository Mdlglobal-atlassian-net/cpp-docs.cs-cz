---
title: Přidání členské proměnné (Visual C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.classes.member.variable
dev_langs:
- C++
helpviewer_keywords:
- member variables, adding
- member variables
ms.assetid: 437783bd-8eb4-4508-8b73-7380116e9d71
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ec9409067793da0e0a89be668f57e86588bdc2d8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46447313"
---
# <a name="adding-a-member-variable--visual-c"></a>Přidání členské proměnné (Visual C++)

Členské proměnné můžete přidat do třídy pomocí zobrazení tříd. Členské proměnné může být buď pro [výměny dat a ověřování dat](../mfc/dialog-data-exchange-and-validation.md), nebo mohou být obecné. Průvodce data členské proměnné je speciálně navržen pro relevantní informace a použít ho ke vkládání prvků ve zdrojových souborech na příslušných místech. Můžete přidat členskou proměnnou z [editoru dialogového okna](../windows/dialog-editor.md) v [zobrazení prostředků](../windows/resource-view-window.md), nebo z [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code).

> [!NOTE]
>  Při navrhování a implementace dialogového okna, může pro vás výhodnější používat dialogové okno editor k přidávání ovládacích prvků dialogového okna pole a potom implementovat ovládací prvky členské proměnné.

### <a name="to-add-a-member-variable-for-a-dialog-control-in-resource-view-using-the-add-member-variable-wizard"></a>Přidání členské proměnné pro ovládací prvek dialogového okna v okně zobrazení prostředků pomocí Průvodce přidáním členské proměnné

1. V okně zobrazení prostředků rozbalte uzel projektu a uzel dialogové okno k zobrazení seznamu projektu dialogových oknech.

1. Dvakrát klikněte na panel dialogových oken, ke kterému chcete přidat členskou proměnnou a otevře se v editoru dialogového okna.

1. V dialogovém okně zobrazí v editoru dialogového okna klikněte pravým tlačítkem na ovládací prvek, ke kterému chcete přidat členskou proměnnou.

1. V místní nabídce klikněte na tlačítko **přidat proměnnou** zobrazíte [Průvodce přidáním členské proměnné](../ide/add-member-variable-wizard.md).

   > [!NOTE]
   > Výchozí hodnota je již součástí **ID ovládacího prvku**.

1. Zadání informací do polí příslušné průvodce. Zobrazit [ovládací prvky dialogového okna a typy proměnných](../ide/dialog-box-controls-and-variable-types.md) Další informace.

1. Klikněte na tlačítko **Dokončit** definice a implementace kódu přidejte do projektu a zavřete průvodce.

### <a name="to-add-a-member-variable-from-class-view-using-the-add-member-variable-wizard"></a>Přidání členské proměnné ze zobrazení tříd pomocí Průvodce přidáním členské proměnné

1. V [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code), rozbalte uzel projektu pro zobrazení tříd v projektu.

1. Klikněte pravým tlačítkem na třídu, ke kterému chcete přidat proměnnou.

1. V místní nabídce klikněte na tlačítko **přidat**a potom klikněte na tlačítko **přidat proměnnou** zobrazíte Průvodce přidáním členské proměnné.

1. Zadání informací do polí příslušné průvodce. Zobrazit [Průvodce přidáním členské proměnné](../ide/add-member-variable-wizard.md) podrobnosti.

1. Klikněte na tlačítko **Dokončit** definice a implementace kódu přidejte do projektu a zavřete průvodce.

## <a name="see-also"></a>Viz také

[Přidání funkce pomocí průvodců kódem](../ide/adding-functionality-with-code-wizards-cpp.md)<br>
[Přidání třídy](../ide/adding-a-class-visual-cpp.md)<br>
[Přidání členské funkce](../ide/adding-a-member-function-visual-cpp.md)<br>
[Popisovače zpráv knihovny MFC](../mfc/reference/adding-an-mfc-message-handler.md)<br>
[Navigace strukturou třídy](../ide/navigating-the-class-structure-visual-cpp.md)