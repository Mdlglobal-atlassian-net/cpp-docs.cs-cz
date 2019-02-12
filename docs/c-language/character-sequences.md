---
title: Sekvence znaků
ms.date: 11/04/2016
ms.assetid: 1e6961a9-150e-4c13-b427-9af4b6a1fb7a
ms.openlocfilehash: 42fb6b61771feb3eaedfb4ce1e674003df91b263
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149925"
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

## <a name="see-also"></a>Viz také:

[Direktivy předběžného zpracování](../c-language/preprocessing-directives.md)
