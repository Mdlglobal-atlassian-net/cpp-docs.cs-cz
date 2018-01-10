---
title: "Extrahování funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e31d1249-9705-4511-acbd-9f6fe73bdf2d
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dbcd323292e301857c65d908047ab14948b86573
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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