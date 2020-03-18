---
title: Nastavení režimu objektu CStatusBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- simple mode and status bar controls
- IsSimple method, using
- SetSimple method [MFC]
- status bar controls [MFC], simple and nonsimple modes
- non-simple mode and status bar controls
- CStatusBarCtrl class [MFC], simple and nonsimple modes
ms.assetid: ca6076e5-1501-4e33-8d35-9308941e46c0
ms.openlocfilehash: 79b499533196447898ce62ea9dc86c1674fc0302
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446421"
---
# <a name="setting-the-mode-of-a-cstatusbarctrl-object"></a>Nastavení režimu objektu CStatusBarCtrl

Existují dva režimy pro objekt `CStatusBarCtrl`: jednoduchá a nejednoduchá. Ve většině případů bude ovládací prvek stavového řádku obsahovat jednu nebo více částí, společně s textem a případně ikonu nebo ikony. Nazývá se to nejednoduchý režim. Další informace o tomto režimu naleznete v tématu [inicializace částí objektu CStatusBarCtrl](../mfc/initializing-the-parts-of-a-cstatusbarctrl-object.md).

Existují však případy, kdy potřebujete pouze zobrazit pouze jeden řádek textu. V takovém případě je jednoduchý režim dostačující pro vaše potřeby. Chcete-li změnit režim objektu `CStatusBarCtrl` na jednoduché, proveďte volání členské funkce [SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple) . Jakmile je ovládací prvek stavového řádku v jednoduchém režimu, nastavte text voláním členské funkce `SetText` a předáním 255 jako hodnoty pro parametr *nPane* .

K určení, v jakém režimu je objekt `CStatusBarCtrl`, můžete použít funkci [zjednodušená](../mfc/reference/cstatusbarctrl-class.md#issimple) .

> [!NOTE]
>  Pokud se objekt stavového řádku mění z nejednoduchého na jednoduchý, nebo naopak, okno se ihned překreslí a v případě potřeby se automaticky obnoví i jakékoli definované části.

## <a name="see-also"></a>Viz také

[Používání atributu CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
