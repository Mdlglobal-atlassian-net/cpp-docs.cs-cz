---
title: Upozornění Linkerů LNK4022 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4022
dev_langs:
- C++
helpviewer_keywords:
- LNK4022
ms.assetid: 890f487e-db98-45dd-a226-c7ccead82b1e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 644e7a9ba26dab15e2bfa2a269f62c04f0510180
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040996"
---
# <a name="linker-tools-warning-lnk4022"></a>Upozornění linkerů LNK4022

nejde najít unikátní shoda pro symbol 'symbol'

ODKAZ nebo LIB nalezeno více odpovídá dané nedekorovaných symbolů a nepovedlo se vyřešit nejednoznačnost. Není vytvořen žádný výstupní soubor (.exe, .dll, .exp nebo .lib). Toto upozornění je následována jedno upozornění [LNK4002](../../error-messages/tool-errors/linker-tools-warning-lnk4002.md) pro každou duplicitní symbol a nakonec následuje závažná chyba [LNK1152](../../error-messages/tool-errors/linker-tools-error-lnk1152.md).

Pokud chcete zabránit toto upozornění, zadejte symbolu v upravené podobě. Spustit [DUMPBIN](../../build/reference/dumpbin-options.md) na objekt, který chcete zobrazit dekorované názvy.