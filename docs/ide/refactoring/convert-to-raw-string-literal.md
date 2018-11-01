---
title: Převést na literál nezpracovaného řetězce
ms.date: 11/16/2016
ms.assetid: fffbfee4-66ee-42ba-aeb9-df07fb702c51
ms.openlocfilehash: 508ab52dc1ca41a97dd8c24df5c5d45c379ea265
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509510"
---
# <a name="convert-to-raw-string-literal"></a>Převést na literál nezpracovaného řetězce
**Co:** umožňuje proměnit libovolný řetězec C++ nezpracovaný řetězcový literál.

**Kdy:** řetězec s řídicí znaky, které by neměly být zpracován jako řídicí znaky.

**Důvod, proč:** může dvojitou řídicí znaky, ale to často vede k nepřehledný a nečitelné řetězce.  Pomocí nezpracované řetězcové literály řetězce velmi usnadňuje čtení.

**Jak:**

1. Umístěte kurzor text nebo myši uvozený řetězec k převedení.

   ![Zvýrazněný kód](images/stringliteral_highlight.png)

1. Dále proveďte jednu z následujících akcí:
   * **Klávesnice**
     * Stisknutím klávesy **Ctrl +.** aktivační událost **rychlé akce a Refaktoringy** nabídky a vybereme **převod na nezpracovaný řetězcový literál** v místní nabídce.
   * **Myši**
     * Klikněte pravým tlačítkem na kód, vyberte **rychlé akce a Refaktoringy** nabídky a vybereme **převod na nezpracovaný řetězcový literál** v místní nabídce.
     * Klikněte na tlačítko ![žárovky](images/bulb.png) ikonu, která se zobrazí v levém okraji a vyberte **převod na nezpracovaný řetězcový literál** v místní nabídce.

1. Řetězec se okamžitě převést na nezpracovaný řetězcový literál.

   ![Nezpracovaný řetězcový literál výsledek](images/stringliteral_result.png)