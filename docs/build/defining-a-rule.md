---
title: Definice pravidla | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, inference rules
- defining inference rules
ms.assetid: 071cd092-3f2e-4065-b0fb-36a9d393cfa8
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7e720613dd4d918b2b697a6ff21a8950f0c5adc2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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