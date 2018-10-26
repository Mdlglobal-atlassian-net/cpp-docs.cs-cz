---
title: Extrahovat funkci | Dokumentace Microsoftu
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
ms.openlocfilehash: e032c2f1579294431b01d5a7695bf2c8a35aa421
ms.sourcegitcommit: 072e12d6b7a242765bdcc9afe4a14a284ade01fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/26/2018
ms.locfileid: "50136117"
---
# <a name="extract-function"></a>Extrahovat funkci
**Co:** umožňuje zapnout fragment kódu do samostatné funkce.

**Kdy:** máte fragment existující kód v některé funkce, které je potřeba volat z jiné funkci.

**Důvod, proč:** vám může kopírovat/vložit tento kód, ale které by mohlo dojít k duplikaci.  Lepším řešením je refaktorovat tohoto fragmentu do své vlastní funkce, které je možné vyvolat bez omezení dalších funkcí.

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
