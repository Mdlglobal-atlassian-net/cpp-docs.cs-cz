---
title: Speciální znaky v souboru pravidel | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, special characters
- makefiles, special characters
- special characters, in NMAKE macros
- macros, special characters
ms.assetid: 92c34ab5-ca6b-4fc0-bcf4-3172eaeda9f0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ae77e769672dcc88a9dd41c901424c8c8150e6b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709356"
---
# <a name="special-characters-in-a-makefile"></a>Speciální znaky v souboru pravidel

Pokud chcete použít speciální znak NMAKE jako literální znak, umístíte stříšky (^) před tímto prvkem. NMAKE ignoruje střížek, které předcházet jiné znaky. Speciální znaky jsou:

`:  ;  #  (  )  $  ^  \  {  }  !  @  —`

Stříšky (^) v rámci řetězec v uvozovkách je považován za znak literálu blikajícího kurzoru. Blikající kurzor na konec řádku vloží literální znak řetězec nebo makro.

V makrech, zpětného lomítka (\\) a potom nový řádek znak je nahrazen mezerou.

V příkazech symbolem procenta (%) je specifikátor souboru. K reprezentaci % doslova v příkazu, zadejte místo jeden double znak procenta (%). V jiných situacích NMAKE interpretuje jeden % doslova, ale vždy interpretuje double %% jako jeden %. Proto k reprezentaci literál %%, zadejte buď znaky procenta tři %% %c, nebo znaménka čtyř procent, %% %c.

Pokud chcete použít znak dolaru ($) jako literální znak v příkazu, zadejte dva znaky dolaru ($$). Tuto metodu lze také v jiných situacích, kde ^ $ funguje.

## <a name="see-also"></a>Viz také

[Obsah souboru pravidel](../build/contents-of-a-makefile.md)