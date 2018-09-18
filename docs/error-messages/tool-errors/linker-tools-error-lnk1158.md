---
title: Chyba Linkerů LNK1158 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1158
dev_langs:
- C++
helpviewer_keywords:
- LNK1158
ms.assetid: 45febf16-d9e1-42db-af91-532e2717fd6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ce319aa4529c74cad00342b09aa0ed98bb49ce7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094166"
---
# <a name="linker-tools-error-lnk1158"></a>Chyba linkerů LNK1158

nelze spustit 'název souboru.

Daný spustitelný soubor volá [odkaz](../../build/reference/linker-command-line-syntax.md) není v adresáři, který obsahuje odkaz, ani v adresáři uvedeném na proměnné prostředí PATH.

Například obdržíte tuto chybu, pokud se pokusíte použít parametr PGOPTIMIZE [parametru/LTCG](../../build/reference/ltcg-link-time-code-generation.md) – možnost linkeru na počítači s operačním systémem 32-bit.