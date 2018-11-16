---
title: Přepsání virtuální funkce
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.virtualfunc.override
helpviewer_keywords:
- virtual functions, overriding
- base classes, overriding virtual functions defined in
- Properties window, overriding virtual functions in
ms.assetid: 2d8c76f2-7a6b-4c9c-8de5-4282ce7755b6
ms.openlocfilehash: 9bb3fd34bbfa14cce1595ed586c4e1b66518e7b7
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694020"
---
# <a name="override-a-virtual-function"></a>Přepsání virtuální funkce

Můžete přepsat virtuální funkce definované v základní třídě ze sady Visual Studio [okno vlastností](/visualstudio/ide/reference/properties-window).

**Chcete-li přepsat virtuální funkci v okně Vlastnosti:**

1. V zobrazení tříd vyberte třídu.

1. V okně Vlastnosti vyberte **přepíše** tlačítko.

   > [!NOTE]
   > **Přepíše** tlačítko je k dispozici při výběru názvu třídy v zobrazení tříd nebo když vyberete v okně zdroje.

   V levém sloupci jsou uvedeny virtuální funkce. Pokud název virtuální funkce se také zobrazí v pravém sloupci, pak přepsání již byl implementován.

1. Pokud funkce nemá žádné přepsání, pak vyberte buňku v pravém sloupci v okně Vlastnosti, chcete-li zobrazit navrhovaný název funkce přepsat jako \<Přidat >*FuncName*.

1. Vyberte navrhovaný název pro přidání provizorního kódu pro funkci.

1. Chcete-li upravit přepisující funkce, dvakrát klikněte na název funkce v zobrazení tříd a úpravy kódu v okně zdroje.

Chcete-li odebrat přepsání, vyberte název funkce přepsání v pravém sloupci a vyberte \<odstranit >*FuncName*. Je zakomentovaný, kód vaší funkce.
