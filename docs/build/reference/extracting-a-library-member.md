---
title: Extrahování člena knihovny
ms.date: 11/04/2016
helpviewer_keywords:
- LIB [C++], extracting library members
- EXTRACT library manager option
- libraries, extracting members
- -EXTRACT library manager option
- extracting library members
- /EXTRACT library manager option
ms.assetid: a2c5c2a1-9b7e-489a-a9a4-1dec694e1fc5
ms.openlocfilehash: 874866627099eb5aeb318273db26a976e99bac7f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439877"
---
# <a name="extracting-a-library-member"></a>Extrahování člena knihovny

LIB můžete použít k vytvoření souboru objektu (. obj), který obsahuje kopii člena existující knihovny. Chcete-li extrahovat kopii člena, použijte následující syntaxi:

```
LIB library /EXTRACT:member /OUT:objectfile
```

Tento příkaz vytvoří soubor. obj s názvem *objectfile* , který obsahuje kopii `member` *knihovny*. Název `member` rozlišuje velká a malá písmena. V jednom příkazu můžete extrahovat pouze jednoho člena. Možnost/OUT je povinná; není k dispozici žádný výchozí název výstupu. Pokud soubor s názvem *objectfile* již v určeném adresáři (nebo v aktuálním adresáři není zadán, pokud není k dispozici žádný adresář s *objectfile*), nahradí extrahovaný *objectfile* existující soubor.

## <a name="see-also"></a>Viz také

[Referenční dokumentace ke knihovně LIB](lib-reference.md)
