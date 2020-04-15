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
ms.openlocfilehash: e09a7bd274c44df2da48bbc007a95802fadd8cf0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365416"
---
# <a name="setting-the-mode-of-a-cstatusbarctrl-object"></a>Nastavení režimu objektu CStatusBarCtrl

Existují dva režimy `CStatusBarCtrl` pro objekt: jednoduché a nonsimple. Ve většině případů bude mít ovládací prvek stavového řádku jednu nebo více částí spolu s textem a možná i ikonou nebo ikonami. Tento režim se nazývá nejednoduchý režim. Další informace o tomto režimu naleznete [v tématu Inicializace částí objektu CStatusBarCtrl](../mfc/initializing-the-parts-of-a-cstatusbarctrl-object.md).

Existují však případy, kdy stačí zobrazit pouze jeden řádek textu. V tomto případě je jednoduchý režim je dostačující pro vaše potřeby. Chcete-li změnit `CStatusBarCtrl` režim objektu na jednoduché, proveďte volání [SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple) členské funkce. Jakmile je ovládací prvek stavového řádku v jednoduchém režimu, nastavte text voláním `SetText` členské funkce a předejte 255 jako hodnotu parametru *nPane.*

Funkci [IsSimple](../mfc/reference/cstatusbarctrl-class.md#issimple) můžete použít k určení, v jakém režimu se `CStatusBarCtrl` objekt nachází.

> [!NOTE]
> Pokud se objekt stavového řádku mění z nejednoduchého na jednoduchý nebo naopak, okno se okamžitě překreslí a případně se automaticky obnoví všechny definované součásti.

## <a name="see-also"></a>Viz také

[Používání atributu CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
