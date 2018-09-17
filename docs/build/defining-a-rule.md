---
title: Definice pravidla | Dokumentace Microsoftu
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
ms.openlocfilehash: a8a5cb7a0285f7abf8bcf476141451eae1b10f85
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705572"
---
# <a name="defining-a-rule"></a>Definice pravidla

*Fromext* představuje rozšíření závislého souboru a *toext* představuje příponu cílového souboru.

```
.fromext.toext:
   commands
```

## <a name="remarks"></a>Poznámky

Rozšíření se nerozlišují malá a velká písmena. Makra lze vyvolat a představují *fromext* a *toext*; makra jsou rozvinuta během předběžného zpracování. Tečka (.) předchozí *fromext* musí být uvedena na začátku řádku. Dvojtečka (:) předchází nula nebo více mezerami či tabulátory. To může následovat pouze mezery nebo tabulátory, středník (;) k určení příkazu, křížku (#) k zadání komentáře nebo znak nového řádku. Nejsou povoleny žádné mezery. Příkazy jsou určeny jako popis bloky.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

[Cesty hledání v pravidlech](../build/search-paths-in-rules.md)

## <a name="see-also"></a>Viz také

[Odvozená pravidla](../build/inference-rules.md)