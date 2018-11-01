---
title: Extrahování člena knihovny
ms.date: 11/04/2016
f1_keywords:
- Lib
helpviewer_keywords:
- LIB [C++], extracting library members
- EXTRACT library manager option
- libraries, extracting members
- -EXTRACT library manager option
- extracting library members
- /EXTRACT library manager option
ms.assetid: a2c5c2a1-9b7e-489a-a9a4-1dec694e1fc5
ms.openlocfilehash: 2975ef584b0244a16b556232b6939308d2e1bd14
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447031"
---
# <a name="extracting-a-library-member"></a>Extrahování člena knihovny

Lib – slouží k vytvoření souboru objektů (.obj), který obsahuje kopii členem existující knihovnu. Extrahujte kopii členem, použijte následující syntaxi:

```
LIB library /EXTRACT:member /OUT:objectfile
```

Tento příkaz vytvoří soubor .obj nazývá *objectfile* , který obsahuje kopii `member` z *knihovny*. `member` Název je velká a malá písmena. Můžete extrahovat jenom jeden člen stačí jediný příkaz. Parametr/out možnost je vyžadována; neexistuje žádný výchozí název výstupu. Pokud soubor s názvem *objectfile* již existuje v zadaném adresáři (nebo aktuálního adresáře, pokud není zadán žádný adresář s *objectfile*), extrahované *objectfile*nahradí existující soubor.

## <a name="see-also"></a>Viz také

[Referenční dokumentace ke knihovně LIB](../../build/reference/lib-reference.md)