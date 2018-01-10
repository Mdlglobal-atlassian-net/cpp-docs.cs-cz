---
title: "Implementace čistý Virtuals | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea9b4719-34a3-474a-b4ec-05b1859f80f1
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f311c2e5832754bfd785084b9aa930b5dbe43845
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
     * Stiskněte klávesu **Ctrl +.** k aktivační události **rychlé akce a refaktoring** nabídku a vyberte  **implementovat všechny čistý Virtuals pro třídu*ClassName*' ** z kontextové nabídky, kde  *Název třídy* je název vybrané třídy.
   * **Myš**
     * Klikněte pravým tlačítkem a vyberte **rychlé akce a refaktoring** nabídku a vyberte  **implementovat všechny čistý Virtuals pro třídu*ClassName*' ** z kontextové nabídky, kde  *Název třídy* je název vybrané třídy.

1. Podpisy čistý virtuální metoda bude automaticky vytvořený, připraveno k implementaci.

   ![Implementace čistý Virtuals výsledek](images/virtuals_result.png)
