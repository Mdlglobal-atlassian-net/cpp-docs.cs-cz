---
title: Extrahování člena knihovny | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- Lib
dev_langs:
- C++
helpviewer_keywords:
- LIB [C++], extracting library members
- EXTRACT library manager option
- libraries, extracting members
- -EXTRACT library manager option
- extracting library members
- /EXTRACT library manager option
ms.assetid: a2c5c2a1-9b7e-489a-a9a4-1dec694e1fc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9207a77868b3257d09f0d9efe38e4765cb8f4906
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726515"
---
# <a name="extracting-a-library-member"></a>Extrahování člena knihovny

Lib – slouží k vytvoření souboru objektů (.obj), který obsahuje kopii členem existující knihovnu. Extrahujte kopii členem, použijte následující syntaxi:

```
LIB library /EXTRACT:member /OUT:objectfile
```

Tento příkaz vytvoří soubor .obj nazývá *objectfile* , který obsahuje kopii `member` z *knihovny*. `member` Název je velká a malá písmena. Můžete extrahovat jenom jeden člen stačí jediný příkaz. Parametr/out možnost je vyžadována; neexistuje žádný výchozí název výstupu. Pokud soubor s názvem *objectfile* již existuje v zadaném adresáři (nebo aktuálního adresáře, pokud není zadán žádný adresář s *objectfile*), extrahované *objectfile*nahradí existující soubor.

## <a name="see-also"></a>Viz také

[Referenční dokumentace ke knihovně LIB](../../build/reference/lib-reference.md)