---
title: "Znak pořadí | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 1e6961a9-150e-4c13-b427-9af4b6a1fb7a
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 09134a17ad8711169a3afc30490c188af47a3f42
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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