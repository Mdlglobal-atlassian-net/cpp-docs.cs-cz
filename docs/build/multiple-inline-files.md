---
title: Několik vložených souborů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inline files, multiple NMAKE
- multiple inline files
- NMAKE program, inline files
ms.assetid: 6d381dcf-0ed8-45d1-8df3-b4598d860b99
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 87d68034c4f0018d65020915d24d0b5c2ec5d61a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725592"
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