---
title: Definice pravidla
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, inference rules
- defining inference rules
ms.assetid: 071cd092-3f2e-4065-b0fb-36a9d393cfa8
ms.openlocfilehash: cd82dc5b0693e563fd3d75a0215265089ff57913
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342882"
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

[Cesty hledání v pravidlech](search-paths-in-rules.md)

## <a name="see-also"></a>Viz také:

[Odvozená pravidla](inference-rules.md)
