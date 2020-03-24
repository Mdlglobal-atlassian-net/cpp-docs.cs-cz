---
title: Převést na literál nezpracovaného řetězce
ms.date: 11/16/2016
ms.assetid: fffbfee4-66ee-42ba-aeb9-df07fb702c51
ms.openlocfilehash: 5636e00bfe8655d84fb2e4b64e0391324ab35d7d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171811"
---
# <a name="convert-to-raw-string-literal"></a>Převést na literál nezpracovaného řetězce

**Co:** Umožňuje převést libovolný řetězec na C++ nezpracovaný řetězcový literál.

**Když:** Máte řetězec se znakem escape, který by neměl být zpracován jako řídicí znaky.

**Proč:** Mohli byste zadat dvojité řídicí znaky, ale to často vede k matoucím a nečitelným řetězcům.  Použití nezpracovaných řetězcových literálů usnadňuje čtení řetězců.

**Použití**

1. Umístěte text nebo ukazatel myši nad řetězec s řídicím řetězcem k převedení.

   ![Zvýrazněný kód](images/stringliteral_highlight.png)

1. Dále proveďte jednu z následujících akcí:
   * **Kombinace**
     * Stiskněte **kombinaci kláves CTRL +.** Chcete-li aktivovat nabídku **rychlé akce a refaktoring** a v místní nabídce vyberte **převést na nezpracovaný řetězcový literál** .
   * **Stisknut**
     * Klikněte pravým tlačítkem na kód, vyberte nabídku **rychlé akce a refaktoring** a v místní nabídce vyberte **převést na nezpracovaný řetězcový literál** .
     * Klikněte na ikonu ![žárovky](images/bulb.png), která se zobrazí na levém okraji, a v místní nabídce vyberte **převést na literál nezpracovaného řetězce** .

1. Řetězec se okamžitě převede na nezpracovaný řetězcový literál.

   ![Výsledek nezpracovaného řetězcového literálu](images/stringliteral_result.png)
