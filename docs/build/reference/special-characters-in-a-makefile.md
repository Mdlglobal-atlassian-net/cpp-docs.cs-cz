---
title: Speciální znaky v souboru pravidel
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, special characters
- makefiles, special characters
- special characters, in NMAKE macros
- macros, special characters
ms.assetid: 92c34ab5-ca6b-4fc0-bcf4-3172eaeda9f0
ms.openlocfilehash: d915b182d72b4251f416433642cd8b1832b80e08
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822981"
---
# <a name="special-characters-in-a-makefile"></a>Speciální znaky v souboru pravidel

Pokud chcete použít speciální znak NMAKE jako literální znak, umístíte stříšky (^) před tímto prvkem. NMAKE ignoruje střížek, které předcházet jiné znaky. Speciální znaky jsou:

`:  ;  #  (  )  $  ^  \  {  }  !  @  —`

Stříšky (^) v rámci řetězec v uvozovkách je považován za znak literálu blikajícího kurzoru. Blikající kurzor na konec řádku vloží literální znak řetězec nebo makro.

V makrech, zpětného lomítka (\\) a potom nový řádek znak je nahrazen mezerou.

V příkazech symbolem procenta (%) se specifikátorem souboru. K reprezentaci % doslova v příkazu, zadejte double znak procenta (%) místo jeden. V jiných situacích NMAKE interpretuje jeden % doslova, ale vždy interpretuje double %% jako jeden %. Proto k reprezentaci literál %%, zadejte buď znaky procenta tři %% %c, nebo znaménka čtyř procent, %% %c.

Pokud chcete použít znak dolaru ($) jako literální znak v příkazu, zadejte dva znaky dolaru ($$). Tuto metodu lze také v jiných situacích, kde ^ $ funguje.

## <a name="see-also"></a>Viz také:

[Obsah souboru pravidel](contents-of-a-makefile.md)
