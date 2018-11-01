---
title: Volající / volaný – uložené registry
ms.date: 11/04/2016
ms.assetid: 0533bd4b-d6bb-4ce1-8201-495e16870cbb
ms.openlocfilehash: f34fbfff8e6c61b5d568c073f6b7da2a12e34535
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50654698"
---
# <a name="callercallee-saved-registers"></a>Volající/volaný – uložené registry

Poškození registrů RAX RCX, RDX, R8, R9, R10, R11 jsou považovány za volatile a musíte vzít v úvahu při volání funkce (není-li jinak bezpečnost dokázat analýzou například celková optimalizace programu).

Registry RBX RBP, RDI, RSI, RSP, r 12, R13, R14 a R15 jsou považovány za stálé a musí být uloženy a obnovit pomocí funkce, která je používá.

## <a name="see-also"></a>Viz také

[Konvence volání](../build/calling-convention.md)