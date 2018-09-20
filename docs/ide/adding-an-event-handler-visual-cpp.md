---
title: Přidání obslužné rutiny události (Visual C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.eventhandler.overview
dev_langs:
- C++
helpviewer_keywords:
- event handlers, adding
- properties [Visual Studio], MSBuild
- MSBuild, properties
ms.assetid: 050bebf0-a9e0-474b-905c-796fe5ac8fc3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cd16628c48c30f6f554a842b70c5217753e305f3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430303"
---
# <a name="adding-an-event-handler-visual-c"></a>Přidání obslužné rutiny události (Visual C++)

Z editoru prostředků, můžete přidat novou obslužnou rutinu události nebo upravit existující obslužné rutiny události pomocí ovládacího prvku pole dialogového okna [Průvodce obslužnou rutinou události](../ide/event-handler-wizard.md).

Událost můžete přidat do třídy implementující pomocí dialogového okna pole [okno vlastností](/visualstudio/ide/reference/properties-window). Pokud chcete do třídy než třídy dialogového okna Přidat událost, použijte Průvodce obslužnou rutinou události.

### <a name="to-add-an-event-handler-to-a-dialog-box-control"></a>Chcete-li přidat obslužnou rutinu události pro ovládací prvek dialogového okna

1. Dvakrát klikněte na pole prostředku dialogového okna v [zobrazení prostředků](../windows/resource-view-window.md) otevřete dialogové okno prostředků pole, která obsahuje ovládací prvek v [editoru dialogového okna](../windows/dialog-editor.md).

1. Klikněte pravým tlačítkem na ovládací prvek, pro kterou chcete zpracovat událost oznámení.

1. V místní nabídce klikněte na tlačítko **přidat obslužnou rutinu události** zobrazíte Průvodce obslužnou rutinou události.

1. Vybrat událost v **typ zprávy** pole můžete přidat do třídy vybraný v **seznamu tříd** pole.

1. Přijměte výchozí název v **název obslužné funkce** pole, nebo zadejte název podle vašeho výběru.

1. Klikněte na tlačítko **přidat a upravit** přidat obslužnou rutinu události do projektu a otevřete textový editor v nové funkci přidat kód pro obslužnou rutinu události.

   Pokud je zvolený typ zpráv, už obslužnou rutinu události pro vybranou třídu **přidat a upravit** není k dispozici, a **upravit kód** je k dispozici. Klikněte na tlačítko **upravit kód** otevřete textový editor v existující funkce.

Alternativně můžete přidat obslužné rutiny událostí z [okno vlastností](/visualstudio/ide/reference/properties-window). Zobrazit [přidání obslužné rutiny události pro ovládací prvky dialogového okna](../windows/adding-event-handlers-for-dialog-box-controls.md) Další informace.

## <a name="see-also"></a>Viz také

[Přidání funkce pomocí průvodců kódem](../ide/adding-functionality-with-code-wizards-cpp.md)<br>
[Přidání třídy](../ide/adding-a-class-visual-cpp.md)<br>
[Přidání členské proměnné](../ide/adding-a-member-variable-visual-cpp.md)<br>
[Přidání členské funkce](../ide/adding-a-member-function-visual-cpp.md)<br>
[Popisovače zpráv knihovny MFC](../mfc/reference/adding-an-mfc-message-handler.md)<br>
[Navigace strukturou třídy](../ide/navigating-the-class-structure-visual-cpp.md)