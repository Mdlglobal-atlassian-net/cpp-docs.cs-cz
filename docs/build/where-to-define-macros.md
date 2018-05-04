---
title: Místo definice maker | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- defining macros
- macros, NMAKE
- NMAKE program, defining macros
ms.assetid: 0fc59ec5-5f58-4644-b7da-7b021f7001af
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9cf3e87a50362c770d45f00c4dc17ac3d264f611
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="where-to-define-macros"></a>Místo definice maker
Definice maker v příkazového řádku, příkazového řádku, souboru pravidel nebo Tools.ini souboru.  
  
 V souboru pravidel nebo soubor Tools.ini každý definici makra musí být na samostatném řádku a nemůže začínat mezera nebo kartě. Mezery nebo karty znaménku rovná se ignorují. Všechny [řetězec znaků](../build/defining-an-nmake-macro.md) jsou literálu, včetně okolních uvozovek a mezery.  
  
 V příkazovém řádku nebo příkazového řádku mezery a karty vymezení argumenty a nemůže obklopit znaménkem rovnosti. Pokud `string` má vložené mezery nebo karty, uzavřete vlastní řetězec nebo celé makro do dvojitých uvozovek nahoře ("").  
  
## <a name="see-also"></a>Viz také  
 [Definice makra NMAKE](../build/defining-an-nmake-macro.md)