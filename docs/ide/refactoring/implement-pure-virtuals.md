---
title: 'Implementace čistě virtuálních funkcí:'
ms.date: 11/16/2016
ms.assetid: ea9b4719-34a3-474a-b4ec-05b1859f80f1
ms.openlocfilehash: 59e4519f57a1d9bd9ba1cee1ed6ae41bea785a9f
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2018
ms.locfileid: "51692659"
---
# <a name="implement-pure-virtuals"></a>Implementace čistě virtuálních funkcí:

**Co:** umožňuje okamžitě generování kódu nutné implementovat všechny čistě virtuální metody ve třídě.

**Kdy:** chcete dědit ze třídy s čistě virtuální funkce.

**Důvod, proč:** ručně může implementovat všechny čistě virtuální funkce jeden po druhém, ale tato funkce automaticky vygeneruje všechny podpisy metod.

**Jak:**

1. Umístěte ukazatel myši text nebo myši nad třídy, ve kterém chcete implementovat čistě virtuální funkce základní třídy.

   ![Zvýrazněný kód](images/virtuals_highlight.png)

1. Dále proveďte jednu z následujících akcí:
   * **Klávesnice**
     * Stisknutím klávesy **Ctrl +.** aktivační událost **rychlé akce a Refaktoringy** nabídky a vybereme **implementovat všechny čistě virtuální funkce pro třídy*ClassName*"** v místní nabídce, kde  *ClassName* je název vybrané třídy.
   * **Myši**
     * Klikněte pravým tlačítkem a vyberte **rychlé akce a Refaktoringy** nabídky a vybereme **implementovat všechny čistě virtuální funkce pro třídy*ClassName*"** v místní nabídce, kde  *ClassName* je název vybrané třídy.

1. Podpisy čistě virtuální metody budou automaticky vytvořený a jestli je připravená k implementaci.

   ![Implementace čistě virtuálních funkcí: výsledek](images/virtuals_result.png)
