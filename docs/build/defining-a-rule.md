---
title: Definice pravidla
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, inference rules
- defining inference rules
ms.assetid: 071cd092-3f2e-4065-b0fb-36a9d393cfa8
ms.openlocfilehash: 7031f56d82fcaf557388c7600d493ebda48add1a
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416927"
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

## <a name="see-also"></a>Viz také:

[Odvozená pravidla](../build/inference-rules.md)
