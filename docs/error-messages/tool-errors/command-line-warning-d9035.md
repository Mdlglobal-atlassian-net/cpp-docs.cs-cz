---
title: Upozornění příkazového řádku D9035
ms.date: 12/10/2018
f1_keywords:
- D9035
helpviewer_keywords:
- D9035
ms.assetid: 6254f933-e37a-45ba-b860-1a870d1bc8e8
ms.openlocfilehash: 778830892bca1cbf3520599eb6e918e56bdf17ea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196635"
---
# <a name="command-line-warning-d9035"></a>Upozornění příkazového řádku D9035

> možnost*Option*je zastaralá a v budoucí verzi se odebere.

## <a name="remarks"></a>Poznámky

Zadali jste možnost kompilátoru, která bude odebrána v budoucí verzi kompilátoru. Pokud existuje navrhovaná náhrada pro *možnost*, bude toto upozornění následováno upozorněním [D9036](../../error-messages/tool-errors/command-line-warning-d9036.md).

Zadaná možnost stále funguje, ale nyní byste měli aktualizovat konfiguraci sestavení. V důsledku toho je pravděpodobnější, že projekt bude pokračovat v sestavení při upgradu kompilátoru.

## <a name="see-also"></a>Viz také

[Zastaralé a odebrané možnosti kompilátoru](../../build/reference/compiler-options-listed-by-category.md#deprecated-and-removed-compiler-options)<br/>
[Upozornění příkazového řádku D9036](command-line-warning-d9036.md)
