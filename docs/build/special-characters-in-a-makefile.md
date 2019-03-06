---
title: Speciální znaky v souboru pravidel
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, special characters
- makefiles, special characters
- special characters, in NMAKE macros
- macros, special characters
ms.assetid: 92c34ab5-ca6b-4fc0-bcf4-3172eaeda9f0
ms.openlocfilehash: e2703adbbdba392b1a317e2656c6f3dba30a36b6
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57420751"
---
# <a name="special-characters-in-a-makefile"></a>Speciální znaky v souboru pravidel

Pokud chcete použít speciální znak NMAKE jako literální znak, umístíte stříšky (^) před tímto prvkem. NMAKE ignoruje střížek, které předcházet jiné znaky. Speciální znaky jsou:

`:  ;  #  (  )  $  ^  \  {  }  !  @  —`

Stříšky (^) v rámci řetězec v uvozovkách je považován za znak literálu blikajícího kurzoru. Blikající kurzor na konec řádku vloží literální znak řetězec nebo makro.

V makrech, zpětného lomítka (\\) a potom nový řádek znak je nahrazen mezerou.

V příkazech symbolem procenta (%) se specifikátorem souboru. K reprezentaci % doslova v příkazu, zadejte double znak procenta (%) místo jeden. V jiných situacích NMAKE interpretuje jeden % doslova, ale vždy interpretuje double %% jako jeden %. Proto k reprezentaci literál %%, zadejte buď znaky procenta tři %% %c, nebo znaménka čtyř procent, %% %c.

Pokud chcete použít znak dolaru ($) jako literální znak v příkazu, zadejte dva znaky dolaru ($$). Tuto metodu lze také v jiných situacích, kde ^ $ funguje.

## <a name="see-also"></a>Viz také:

[Obsah souboru pravidel](../build/contents-of-a-makefile.md)
