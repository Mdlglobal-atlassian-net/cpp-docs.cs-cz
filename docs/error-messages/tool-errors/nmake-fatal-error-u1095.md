---
title: Závažná chyba nástroje NMAKE U1095 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1095
dev_langs:
- C++
helpviewer_keywords:
- U1095
ms.assetid: a392582b-06db-4568-9c13-450293a4fbda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 964ec1d029e56a5d9d78659ad919c71a4e44506d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039878"
---
# <a name="nmake-fatal-error-u1095"></a>Závažná chyba nástroje NMAKE U1095

Rozbalený příkazový řádek "příkazového řádku" příliš dlouhý

Po rozšíření makra na daném řádku příkaz překročil limit délky příkazových řádků pro operační systém.

Zástupného kódu MS-DOS umožňuje až 128 znaků v příkazovém řádku.

Pokud je příkaz pro program, který může přijmout příkazového řádku vstup ze souboru, změňte příkaz a zadejte vstup ze souboru na disku nebo vložený soubor. Například odkaz a LIB přijímat vstup ze souboru odpovědí.