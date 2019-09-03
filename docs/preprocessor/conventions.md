---
title: Konvence dokumentů
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor
- preprocessor, conventions
ms.assetid: 469ce448-dc6c-4d0e-ba2b-e2e7a10155e1
ms.openlocfilehash: bb826b879b71edd3631c11a717320cee51c87175
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220370"
---
# <a name="document-conventions"></a>Konvence dokumentů

Úmluvy používají odlišné atributy písma pro různé součásti syntaxe. Symboly a písma jsou následující:

| Atribut | Popis |
|---------------|-----------------|
| *neterminálu* | Kurzíva označuje neterminály. |
| **#include** | Terminály tučného typu jsou slova a symboly vyhrazená literály, které je nutné zadat tak, jak je znázorněno. Znaky v tomto kontextu vždy rozlišují velká a malá písmena. |
| <sub>přihlásit</sub> | Neterminály následované <sub>výslovným souhlasem</sub> jsou vždycky volitelné.|
| výchozí písmo | Znaky ze sady, které jsou popsány nebo uvedeny v tomto písmu, lze použít jako terminály v příkazech. |

Dvojtečka ( **:** ) po neterminálu zavádí svou definici. Alternativní definice jsou uvedeny na samostatných řádcích.

V blocích syntaxe kódu mají tyto symboly ve výchozím řezu písma zvláštní význam:

| Písmeno | Popis |
|---|---|
| \[] | Hranaté závorky obklopí volitelný prvek. |
| { \| } | Složené závorky ohraničují alternativní prvky oddělené svislými pruhy. |
| ... | Určuje, že se může opakovat vzor předchozího prvku. |

V blocích syntaxe kódu, čárky (`,`),`.`tečky (), středník (`;`), dvojtečky (`:`), závorky (`( )`), dvojité uvozovky (`"`) a jednoduché uvozovky (`'`) jsou literály.

## <a name="see-also"></a>Viz také:

[Souhrn gramatiky (CC++/)](../preprocessor/grammar-summary-c-cpp.md)
