---
title: Extrahování funkce | Microsoft Docs
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: e31d1249-9705-4511-acbd-9f6fe73bdf2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7fc4d48c972bca9352f326085574e4cf4df83aea
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "33333154"
---
# <a name="extract-function"></a>Extrahování – funkce
**Co:** umožňuje zapnout fragment kódu do své vlastní funkce.

**Kdy:** máte fragment kódu existující v některé funkce, která musí být volána z jiné funkce.  

**Důvod:** vám může zkopírujte a vložte tento kód, ale které by vedlo k duplikaci.  Lepší řešení je refaktorovat tento fragment do svou vlastní funkci, která lze volat volně dalších funkcí.

**Postupy:**

1. Zvýrazněte kód extrahovat:

   ![Zvýrazněný kód](images/extractfunction_highlight.png)

1. Dále proveďte jednu z následujících akcí:
   * **Klávesnice**
     * Stiskněte klávesu **Ctrl + R**, pak **Ctrl + M**.  (Všimněte si, že klávesové zkratky se může lišit na základě na profilu, které jste vybrali.)
     * Stiskněte klávesu **Ctrl +.** k aktivační události **rychlé akce a refaktoring** nabídku a vyberte **extrahovat – funkce (experimentální)** v místní nabídce.
   * **Myš**
     * Vyberte **Upravit > Refaktorovat > extrahovat funkce (experimentální)**.
     * Klikněte pravým tlačítkem na kód, vyberte **rychlé akce a refaktoring** nabídku a vyberte **extrahovat – funkce (experimentální)** v místní nabídce.
     * Klikněte ![žárovek](images/bulb.png) ikonu, která se zobrazí v levým okrajem a vyberte **extrahovat – funkce (experimentální)** v místní nabídce.

1. V **extrahovat funkce nebo metodu (experimentální)** okno, zadejte název nové funkce, vyberte místo kód umístit a klikněte **OK** tlačítko.  

   ![Extrahování funkce – funkce](images/extractfunction_dialog.png)

1. Vytvoří se nové funkce tam, kde jste zadali, prototyp funkce v odpovídající soubor hlaviček, a původní kód bude změněno na volání této funkce.

   ![Extrahování výsledku funkce](images/extractfunction_result.png)