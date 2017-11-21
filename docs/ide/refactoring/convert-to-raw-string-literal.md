---
title: "Převést literál Nezpracovaný řetězec | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fffbfee4-66ee-42ba-aeb9-df07fb702c51
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c237f9042707654c913a24db916a82971603bb0a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="convert-to-raw-string-literal"></a>Převést na nezpracovaná řetězcový literál
**Co:** umožňuje zapnout libovolný řetězec do C++ Nezpracovaný řetězec literálu.

**Kdy:** řetězec s uvozovacími znaky znaky, které by neměly být zpracovány jako řídící znaky.

**Důvod:** může dvojitou řídicí znaky, ale tento často vede k matoucí a nečitelné řetězce.  Pomocí nezpracovaná textové literály jednodušší řetězce ke čtení.

**Postupy:**

1. Umístěte kurzor text nebo myš uvozený řetězec k převedení.

   ![Zvýrazněný kód](images/stringliteral_highlight.png)

1. Dále proveďte jednu z následujících akcí:
   * **Klávesnice**
     * Stiskněte klávesu **Ctrl +.** k aktivační události **rychlé akce a refaktoring** nabídku a vyberte **převést na nezpracovaná literálu řetězce** v místní nabídce.
   * **Myš**
     * Klikněte pravým tlačítkem na kód, vyberte **rychlé akce a refaktoring** nabídku a vyberte **převést na nezpracovaná literálu řetězce** v místní nabídce.
     * Klikněte na tlačítko ![žárovek](images/bulb.png) ikonu, která se zobrazí v levým okrajem a vyberte **převést na nezpracovaná literálu řetězce** v místní nabídce.

1. Řetězec se okamžitě převede na nezpracovaná řetězcový literál.  

   ![Nezpracovaná řetězec literálu výsledek](images/stringliteral_result.png)