---
title: Volající / volaný – uložené registry | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0533bd4b-d6bb-4ce1-8201-495e16870cbb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e8e877387dbb5b0be865e11017a3ac71a0c38faa
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707652"
---
# <a name="callercallee-saved-registers"></a>Volající/volaný – uložené registry

Poškození registrů RAX RCX, RDX, R8, R9, R10, R11 jsou považovány za volatile a musíte vzít v úvahu při volání funkce (není-li jinak bezpečnost dokázat analýzou například celková optimalizace programu).

Registry RBX RBP, RDI, RSI, RSP, r 12, R13, R14 a R15 jsou považovány za stálé a musí být uloženy a obnovit pomocí funkce, která je používá.

## <a name="see-also"></a>Viz také

[Konvence volání](../build/calling-convention.md)