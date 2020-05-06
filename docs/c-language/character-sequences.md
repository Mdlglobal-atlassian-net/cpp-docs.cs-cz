---
title: Sekvence znaků
ms.date: 11/04/2016
ms.assetid: 1e6961a9-150e-4c13-b427-9af4b6a1fb7a
ms.openlocfilehash: 42fb6b61771feb3eaedfb4ce1e674003df91b263
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62312684"
---
# <a name="character-sequences"></a>Sekvence znaků

**3.8.2 ANSI** Mapování znakových sekvencí zdrojového souboru

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
