---
title: Implementace čistý Virtuals | Microsoft Docs
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
ms.openlocfilehash: afce516f2718a76658846ed4f992aeabff75330b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "33328023"
---
# <a name="implement-pure-virtuals"></a>Čistý Virtuals implementace
**Co:** umožňuje okamžitě generování kódu potřebnou k implementaci všech čistý virtuální metody ve třídě. 

**Kdy:** chcete použít dědění ze třídy s čistě virtuální funkce.  

**Důvod:** ručně může implementovat všechny čistý virtuální funkce jeden po druhém, ale tato funkce bude automaticky generovat všechny podpisy metoda.

**Postupy:**

1. Umístěte kurzor text nebo myši nad třídu, ve kterém chcete implementovat čistý virtuální funkce základní třídy.

   ![Zvýrazněný kód](images/virtuals_highlight.png)

1. Dále proveďte jednu z následujících akcí:
   * **Klávesnice**
     * Stiskněte klávesu **Ctrl +.** k aktivační události **rychlé akce a refaktoring** nabídku a vyberte **implementovat všechny čistý Virtuals pro třídu*ClassName*'** z kontextové nabídky, kde  *Název třídy* je název vybrané třídy.
   * **Myš**
     * Klikněte pravým tlačítkem a vyberte **rychlé akce a refaktoring** nabídku a vyberte **implementovat všechny čistý Virtuals pro třídu*ClassName*'** z kontextové nabídky, kde  *Název třídy* je název vybrané třídy.

1. Podpisy čistý virtuální metoda bude automaticky vytvořený, připraveno k implementaci.

   ![Implementace čistý Virtuals výsledek](images/virtuals_result.png)
