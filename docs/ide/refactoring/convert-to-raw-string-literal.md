---
title: Převést na literál nezpracovaného řetězce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: fffbfee4-66ee-42ba-aeb9-df07fb702c51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75037ea542a5bd2160d9a89138b12f82867002a5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46388443"
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