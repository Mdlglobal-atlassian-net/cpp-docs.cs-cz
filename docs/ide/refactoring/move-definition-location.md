---
title: "Přesunout umístění definice | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6d507ac-c61e-4da2-95c8-d504b42e2520
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 838f3d01f5e6d8612948304b80b79cf9c7cb4720
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="move-definition-location"></a>Přesunutí definice umístění
**Co:** umožňuje okamžitě přesunout do odpovídající soubor hlaviček definici funkce.

**Kdy:** máte funkci, která chcete přesunout do záhlaví souboru.  

**Důvod:** může ručně přesunout funkce, ale tato funkce se přesune se automaticky, vytváření soubor hlaviček, pokud je to nutné.

**Postupy:**

1. Umístěte kurzor text nebo myši nad funkce, pro který chcete přesunout.

   ![Zvýrazněný kód](images/movedefinition_highlight.png)

1. Dále proveďte jednu z následujících akcí:
   * **Klávesnice**
     * Stiskněte klávesu **Ctrl +.** spuštění **rychlé akce a refaktoring** nabídku a vyberte **přesunout umístění definice** v místní nabídce.
   * **Myš**
     * Klikněte pravým tlačítkem a vyberte **rychlé akce a refaktoring** nabídku a vyberte **přesunout umístění definice** v místní nabídce.

1. Funkce přesunou do odpovídající záhlaví souboru, který se zobrazí v automaticky otevřeném okně okně preview.  Pokud soubor hlaviček neexistuje, bude také vytvořit a umístit do projektu.

   ![Vytvořit deklaraci / způsobit definice](images/movedefinition_result.png)
