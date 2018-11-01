---
title: Několik vložených souborů
ms.date: 11/04/2016
helpviewer_keywords:
- inline files, multiple NMAKE
- multiple inline files
- NMAKE program, inline files
ms.assetid: 6d381dcf-0ed8-45d1-8df3-b4598d860b99
ms.openlocfilehash: ec531e5716098725782010927201ef57e2a8aa24
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558155"
---
# <a name="multiple-inline-files"></a>Několik vložených souborů

Příkaz můžete vytvořit více než jeden vložený soubor.

## <a name="syntax"></a>Syntaxe

```
command << <<
inlinetext
<<[KEEP | NOKEEP]
inlinetext
<<[KEEP | NOKEEP]
```

## <a name="remarks"></a>Poznámky

Pro každý soubor zadejte jeden nebo více řádků textu vložené, za nímž následuje pravou řádek obsahující oddělovač. Zahájit text druhý soubor na řádek následující oddělovací čáry použité k první soubor.

## <a name="see-also"></a>Viz také

[Soubory vložené do souboru pravidel](../build/inline-files-in-a-makefile.md)