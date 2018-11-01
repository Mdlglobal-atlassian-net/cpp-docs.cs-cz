---
title: Upozornění linkerů LNK4022
ms.date: 11/04/2016
f1_keywords:
- LNK4022
helpviewer_keywords:
- LNK4022
ms.assetid: 890f487e-db98-45dd-a226-c7ccead82b1e
ms.openlocfilehash: 1c9ccfe6ca201ae4deed69c7d01429c67cce4bda
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552474"
---
# <a name="linker-tools-warning-lnk4022"></a>Upozornění linkerů LNK4022

nejde najít unikátní shoda pro symbol 'symbol'

ODKAZ nebo LIB nalezeno více odpovídá dané nedekorovaných symbolů a nepovedlo se vyřešit nejednoznačnost. Není vytvořen žádný výstupní soubor (.exe, .dll, .exp nebo .lib). Toto upozornění je následována jedno upozornění [LNK4002](../../error-messages/tool-errors/linker-tools-warning-lnk4002.md) pro každou duplicitní symbol a nakonec následuje závažná chyba [LNK1152](../../error-messages/tool-errors/linker-tools-error-lnk1152.md).

Pokud chcete zabránit toto upozornění, zadejte symbolu v upravené podobě. Spustit [DUMPBIN](../../build/reference/dumpbin-options.md) na objekt, který chcete zobrazit dekorované názvy.