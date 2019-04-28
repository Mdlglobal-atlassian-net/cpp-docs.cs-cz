---
title: Převést na literál nezpracovaného řetězce
ms.date: 11/16/2016
ms.assetid: fffbfee4-66ee-42ba-aeb9-df07fb702c51
ms.openlocfilehash: bf492e6796b9d2342b5952abb093bddd5ede114b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349414"
---
# <a name="convert-to-raw-string-literal"></a>Převést na literál nezpracovaného řetězce

**Co:** Umožňuje vypnout libovolný řetězec do C++ nezpracovaný řetězcový literál.

**Kdy:** Máte řetězec s řídicí znaky, které by neměly být zpracován jako řídicí znaky.

**Proč:** Můžete dvojitou řídicí znaky, ale to často vede k nepřehledný a nečitelné řetězce.  Pomocí nezpracované řetězcové literály řetězce velmi usnadňuje čtení.

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