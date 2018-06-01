---
title: Převést literál Nezpracovaný řetězec | Microsoft Docs
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
ms.openlocfilehash: b98825719e7b3c0d8eb760a2ec50644b5eddd54e
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "33328406"
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