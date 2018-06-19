---
title: Znak pořadí | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 1e6961a9-150e-4c13-b427-9af4b6a1fb7a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 85cf817a4d50346b9d10a9a9d1bc27abb5904433
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32382387"
---
# <a name="character-sequences"></a>Sekvence znaků
**ANSI 3.8.2** mapování sekvence znaků zdrojového souboru  
  
 Příkazy preprocesoru používají stejnou znakovou sadu jako příkazy zdrojového souboru s tím rozdílem, že nejsou podporovány řídicí sekvence.  
  
 Cestu k vloženému souboru tedy zadávejte pouze s jedním zpětným lomítkem:  
  
```  
#include "path1\path2\myfile"  
```  
  
 Ve zdrojovém kódu jsou zapotřebí dvě zpětná lomítka:  
  
```  
fil = fopen( "path1\\path2\\myfile", "rt" );  
```  
  
## <a name="see-also"></a>Viz také  
 [Direktivy předběžného zpracování](../c-language/preprocessing-directives.md)