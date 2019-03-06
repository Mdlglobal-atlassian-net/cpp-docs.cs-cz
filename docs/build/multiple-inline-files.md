---
title: Několik vložených souborů
ms.date: 11/04/2016
helpviewer_keywords:
- inline files, multiple NMAKE
- multiple inline files
- NMAKE program, inline files
ms.assetid: 6d381dcf-0ed8-45d1-8df3-b4598d860b99
ms.openlocfilehash: 5b41d448c89ac30d891c41d1ad1e314cbf9724a8
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57425611"
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

## <a name="see-also"></a>Viz také:

[Soubory vložené do souboru pravidel](../build/inline-files-in-a-makefile.md)
