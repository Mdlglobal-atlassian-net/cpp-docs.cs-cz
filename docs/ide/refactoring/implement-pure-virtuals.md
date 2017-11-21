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
ms.openlocfilehash: e753654ebada3c508858ff0ceb3d840e4a592c4c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
