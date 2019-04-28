---
title: Extrahovat funkci
ms.date: 11/16/2016
ms.assetid: e31d1249-9705-4511-acbd-9f6fe73bdf2d
ms.openlocfilehash: ec3b9a0aeaef9e418b457bafdfb9bb1bbd2edffc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349336"
---
# <a name="extract-function"></a>Extrahovat funkci

**Co:** Umožňuje vypnout fragment kódu do samostatné funkce.

**Kdy:** Máte fragment existující kód v některé funkce, které je potřeba volat z jiné funkci.

**Proč:** Vám může kopírovat/vložit tento kód, ale které by mohlo dojít k duplikaci.  Lepším řešením je refaktorovat tohoto fragmentu do své vlastní funkce, které je možné vyvolat bez omezení dalších funkcí.

**Jak:**

1. Zvýraznění kódu extrahovaným:

   ![Zvýrazněný kód](images/extractfunction_highlight.png)

1. Dále proveďte jednu z následujících akcí:
   * **Klávesnice**
     * Stisknutím klávesy **Ctrl + R**, pak **Ctrl + M**.  (Všimněte si, že klávesová zkratka může být jiný platformě, na který profil vyberete.)
     * Stisknutím klávesy **Ctrl +.** aktivační událost **rychlé akce a Refaktoringy** nabídky a vybereme **extrahovat funkci (experimentální)** v místní nabídce.
   * **Myši**
     * Vyberte **Upravit > Refaktorovat > extrahovat (experimentální) funkce**.
     * Klikněte pravým tlačítkem na kód, vyberte **rychlé akce a Refaktoringy** nabídky a vybereme **extrahovat funkci (experimentální)** v místní nabídce.
     * Klikněte na tlačítko ![žárovky](images/bulb.png) ikonu, která se zobrazí v levém okraji a vyberte **extrahovat funkci (experimentální)** v místní nabídce.

1. V **extrahovat funkci/metodu (experimentální)** zadejte nový název funkce, vyberte, kde chcete kód umístit a klikněte na tlačítko **OK** tlačítko.

   ![Extrahovat funkci dialogového okna](images/extractfunction_dialog.png)

1. Vytvoří se nová funkce tam, kde jste zadali, prototypu funkce v odpovídající soubor záhlaví a původního kódu se změní, aby volání této funkce.

   ![Extrahovat výsledku funkce](images/extractfunction_result.png)
