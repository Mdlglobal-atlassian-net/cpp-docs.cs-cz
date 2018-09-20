---
title: 'Implementace čistě virtuálních funkcí: | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: ea9b4719-34a3-474a-b4ec-05b1859f80f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 234ae9a67bcbc60ea156fbacb5169d0bd1573a91
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442757"
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
