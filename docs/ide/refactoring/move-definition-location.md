---
title: Přesunout umístění definice | Microsoft Docs
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: c6d507ac-c61e-4da2-95c8-d504b42e2520
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 44211105429e33c136999a7877ac6ee42af29f17
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "33327837"
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
