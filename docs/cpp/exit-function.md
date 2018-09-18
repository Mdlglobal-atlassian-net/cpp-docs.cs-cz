---
title: Funkce Exit | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- Exit
dev_langs:
- C++
helpviewer_keywords:
- exit function
ms.assetid: 26ce439f-81e2-431c-9ff8-a09a96f32127
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71bff42495c4b6b7bf4016f0f08e7127c2b278ac
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46075173"
---
# <a name="exit-function"></a>exit – funkce

**Ukončit** funkce deklarovaná ve standardním vloženém souboru \<stdlib.h >, ukončuje program jazyka C++.

Hodnota zadaná jako argument **ukončit** je vrácena operačnímu systému jako návratový nebo ukončovací kód programu. Dle konvence návratový kód nula znamená, že byl program dokončen úspěšně.

> [!NOTE]
>  Můžete použít konstanty EXIT_FAILURE a EXIT_SUCCESS definované v \<stdlib.h >, indikující úspěch nebo neúspěch programu.

Vydání **vrátit** příkaz z `main` je ekvivalentní volání funkce **ukončit** funkce s návratovou hodnotou jako svůj argument.

Další informace najdete v tématu [ukončit](../c-runtime-library/reference/exit-exit-exit.md) v *Run-Time Library Reference*.

## <a name="see-also"></a>Viz také:

[Ukončení programu](../cpp/program-termination.md)