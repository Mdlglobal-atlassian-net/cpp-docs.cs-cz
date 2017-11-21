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
ms.openlocfilehash: cfb17f531df5c232f1f376cd003acb7bf5a62206
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="where-to-define-macros"></a>Místo definice maker
Definice maker v příkazového řádku, příkazového řádku, souboru pravidel nebo Tools.ini souboru.  
  
 V souboru pravidel nebo soubor Tools.ini každý definici makra musí být na samostatném řádku a nemůže začínat mezera nebo kartě. Mezery nebo karty znaménku rovná se ignorují. Všechny [řetězec znaků](../build/defining-an-nmake-macro.md) jsou literálu, včetně okolních uvozovek a mezery.  
  
 V příkazovém řádku nebo příkazového řádku mezery a karty vymezení argumenty a nemůže obklopit znaménkem rovnosti. Pokud `string` má vložené mezery nebo karty, uzavřete vlastní řetězec nebo celé makro do dvojitých uvozovek nahoře ("").  
  
## <a name="see-also"></a>Viz také  
 [Definice makra NMAKE](../build/defining-an-nmake-macro.md)