---
title: Závažná chyba nástroje NMAKE U1056 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1056
dev_langs:
- C++
helpviewer_keywords:
- U1056
ms.assetid: da855728-b69e-413c-83ed-df912126215e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e0a83c62bedf995708d5e99fee19f05696d05c2d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065689"
---
# <a name="nmake-fatal-error-u1056"></a>Závažná chyba nástroje NMAKE U1056

Nelze najít procesor příkazů.

Příkaz procesoru nebyla v cestě zadané v **COMSPEC** nebo **cesta** proměnné prostředí.

NMAKE používá COMMAND.COM nebo CMD. Soubor EXE jako příkazový procesor při provádění příkazů. Vyhledá procesor příkazu nejprve v cestě, nastavte **COMSPEC**. Pokud **COMSPEC** buď neexistuje, NMAKE prohledávání adresáře podle **cesta**.