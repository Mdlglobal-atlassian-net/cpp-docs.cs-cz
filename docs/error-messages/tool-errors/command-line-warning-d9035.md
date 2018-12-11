---
title: Upozornění příkazového řádku D9035
ms.date: 12/10/2018
f1_keywords:
- D9035
helpviewer_keywords:
- D9035
ms.assetid: 6254f933-e37a-45ba-b860-1a870d1bc8e8
ms.openlocfilehash: 9c0a159dcf193b4ad016069bafd86c557e9e1281
ms.sourcegitcommit: 6990f842fefc27b522b15cf352f3517b319d78da
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248517"
---
# <a name="command-line-warning-d9035"></a>Upozornění příkazového řádku D9035

> možnost "*možnost*' se už nepoužívá a bude v budoucí verzi odebrána

## <a name="remarks"></a>Poznámky

Jste určili možnost kompilátoru, která bude v budoucí verzi kompilátoru odebrána. Pokud navrhovaná náhrada za *možnost*, toto upozornění je následována upozornění [D9036](../../error-messages/tool-errors/command-line-warning-d9036.md).

Zadaná možnost stále funguje, ale měli byste aktualizovat konfiguraci sestavení. V důsledku toho projekt je větší pravděpodobnost pokračovat v sestavení, když upgradujete kompilátor.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru odebrané a zastaralé](../../build/reference/compiler-options-listed-by-category.md#deprecated-and-removed-compiler-options)<br/>
[Upozornění příkazového řádku D9036](command-line-warning-d9036.md)