---
title: Ošetření tlačítka Použít
ms.date: 11/04/2016
helpviewer_keywords:
- Apply button in property sheet
- property sheets, Apply button
ms.assetid: 7e977015-59b8-406f-b545-aad0bfd8d55b
ms.openlocfilehash: 30ee549a334a684deeb4a845f2fc49ee8bbe11db
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62240584"
---
# <a name="handling-the-apply-button"></a>Ošetření tlačítka Použít

Seznamy vlastností mají funkce, která standardní dialogová okna nepodporují: Povolit uživateli nastavit změny provedené před jeho zavřením seznam vlastností. To se provádí pomocí tlačítko použít. Tento článek popisuje metody, které můžete použít k implementaci této funkce správně.

Modálních dialogových oken obvykle použití nastavení na externí objekt, když uživatel klikne na tlačítko OK zavřete dialogové okno. Totéž platí pro seznam vlastností: Když uživatel klikne na tlačítko OK, nové nastavení v seznamu vlastností se projeví.

Můžete však uživateli umožňují uložit nastavení bez nutnosti zavřít dialogové okno seznam vlastností. Toto je funkce tlačítko použít. Tlačítko použít aktuální nastavení ve všech stránek vlastností platí pro externí objekt, na rozdíl od použití pouze aktuální nastavení aktuálně aktivní stránkou.

Ve výchozím nastavení je vždy zakázáno na tlačítko použít. Je nutné napsat kód, který chcete povolit tlačítko použít ve vhodných chvílích. proto je nutné napsat kód pro implementaci efekt použít, jak je popsáno níže.

Pokud nechcete, aby nabízel funkci použít pro uživatele, není nutné použít tlačítko Odebrat. Můžete nechat je zakázaná, protože budou běžné mezi aplikacemi, které používají standardní vlastnosti list podpory k dispozici v budoucích verzích Windows.

Chcete-li stránka jako upravené sestavy a povolit tlačítko použít, zavolejte `CPropertyPage::SetModified( TRUE )`. Případné upravovaného stránek sestavy, bude zůstat zapnuté, bez ohledu na to, zda byl změněn na aktivní stránce tlačítko použít.

Měli byste zavolat [CPropertyPage::SetModified](../mfc/reference/cpropertypage-class.md#setmodified) vždy, když uživatel změní nastavení na stránce. K implementaci obslužné rutiny oznámení změn pro všechny ovládací prvky na stránce vlastností, jako je jeden způsob, jak zjistit, kdy uživatel změní nastavení na stránce **EN_CHANGE** nebo **BN_CLICKED**.

K implementaci vliv na tlačítko použít, seznam vlastností zjistit její vlastník nebo jiné externí objekt v aplikaci, aby mohl použít aktuální nastavení na stránkách vlastností. Seznam vlastností ve stejnou dobu, měli zakázat tlačítko použít voláním `CPropertyPage::SetModified( FALSE )` pro všechny stránky, které použije jejich změny do externího objektu.

Příklad tohoto procesu, najdete v ukázce MFC Obecné [PROPDLG](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Viz také:

[Seznamy vlastností](../mfc/property-sheets-mfc.md)
