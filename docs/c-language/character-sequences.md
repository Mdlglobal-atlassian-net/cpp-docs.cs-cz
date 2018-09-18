---
title: Znak sekvence | Dokumentace Microsoftu
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
ms.openlocfilehash: 5cf3b52b8a4e76062d06b0b9ca3d4535b79595c5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061510"
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