---
title: Sekvence znaků
ms.date: 11/04/2016
ms.assetid: 1e6961a9-150e-4c13-b427-9af4b6a1fb7a
ms.openlocfilehash: dea24a2ae5887ea8c0111d8251ba4d9d03ccba0f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50489658"
---
# <a name="character-sequences"></a>Sekvence znaků

**ANSI 3.8.2** mapování znakové sekvence zdrojového souboru

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