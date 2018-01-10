---
title: "Místo definice maker | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- defining macros
- macros, NMAKE
- NMAKE program, defining macros
ms.assetid: 0fc59ec5-5f58-4644-b7da-7b021f7001af
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c2e646de4cf67fc249d69fb07789f4c8a3e14bf0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="where-to-define-macros"></a>Místo definice maker
Definice maker v příkazového řádku, příkazového řádku, souboru pravidel nebo Tools.ini souboru.  
  
 V souboru pravidel nebo soubor Tools.ini každý definici makra musí být na samostatném řádku a nemůže začínat mezera nebo kartě. Mezery nebo karty znaménku rovná se ignorují. Všechny [řetězec znaků](../build/defining-an-nmake-macro.md) jsou literálu, včetně okolních uvozovek a mezery.  
  
 V příkazovém řádku nebo příkazového řádku mezery a karty vymezení argumenty a nemůže obklopit znaménkem rovnosti. Pokud `string` má vložené mezery nebo karty, uzavřete vlastní řetězec nebo celé makro do dvojitých uvozovek nahoře ("").  
  
## <a name="see-also"></a>Viz také  
 [Definice makra NMAKE](../build/defining-an-nmake-macro.md)