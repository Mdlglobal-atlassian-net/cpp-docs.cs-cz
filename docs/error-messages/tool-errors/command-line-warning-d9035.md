---
title: Upozornění příkazového řádku D9035
ms.date: 12/10/2018
f1_keywords:
- D9035
helpviewer_keywords:
- D9035
ms.assetid: 6254f933-e37a-45ba-b860-1a870d1bc8e8
ms.openlocfilehash: 9c0a159dcf193b4ad016069bafd86c557e9e1281
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62213767"
---
# <a name="command-line-warning-d9035"></a>Upozornění příkazového řádku D9035

> možnost "*možnost*' se už nepoužívá a bude v budoucí verzi odebrána

## <a name="remarks"></a>Poznámky

Jste určili možnost kompilátoru, která bude v budoucí verzi kompilátoru odebrána. Pokud navrhovaná náhrada za *možnost*, toto upozornění je následována upozornění [D9036](../../error-messages/tool-errors/command-line-warning-d9036.md).

Zadaná možnost stále funguje, ale měli byste aktualizovat konfiguraci sestavení. V důsledku toho projekt je větší pravděpodobnost pokračovat v sestavení, když upgradujete kompilátor.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru odebrané a zastaralé](../../build/reference/compiler-options-listed-by-category.md#deprecated-and-removed-compiler-options)<br/>
[Upozornění příkazového řádku D9036](command-line-warning-d9036.md)