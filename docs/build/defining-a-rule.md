---
title: Definice pravidla | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, inference rules
- defining inference rules
ms.assetid: 071cd092-3f2e-4065-b0fb-36a9d393cfa8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a8ff7c58033ac5f7e42764d185c45c206bf406f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="defining-a-rule"></a>Definice pravidla
*Fromext* představuje příponu závislý soubor, a *toext* představuje příponu cílového souboru.  
  
```  
.fromext.toext:  
   commands  
```  
  
## <a name="remarks"></a>Poznámky  
 Rozšíření se nerozlišují malá a velká písmena. Makra může vyvolat představují *fromext* a *toext*; makra rozbaleny při předběžném zpracování. Tečka (.) předchozí *fromext* musí být uvedena na začátku řádku. Nula nebo více mezerami nebo karty je před dvojtečkou (:). Ho může následovat pouze mezery nebo karty, středníkem (;) k určení příkazu, křížku (#) k určení komentář nebo znak nového řádku. Žádné jiné mezery. Příkazy jsou zadány jako popis bloky.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
 [Cesty hledání v pravidlech](../build/search-paths-in-rules.md)  
  
## <a name="see-also"></a>Viz také  
 [Odvozená pravidla](../build/inference-rules.md)