---
title: Priority v definicích maker
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, precedence in macro definitions
- macros, precedence
ms.assetid: 0c13182d-83cb-4cbd-af2d-f4c916b62aeb
ms.openlocfilehash: 8829b3cdbc7b2324ef3d118f8ca45dd2a1621e7e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50619076"
---
# <a name="precedence-in-macro-definitions"></a>Priority v definicích maker

Pokud makro má několik definic, používá NMAKE definici nejvyšší prioritu. Následující seznam uvádí pořadí dle priority od nejvyšší po nejnižší:

1. Makro definované v příkazovém řádku

1. Makro definované v souboru pravidel nebo soubor k zahrnutí

1. Zděděné makra proměnné prostředí

1. Makro definované v souboru Tools.ini

1. Předdefinované makro, jako například [kopie](../build/command-macros-and-options-macros.md) a [AS](../build/command-macros-and-options-macros.md)

/E použijte, aby makra zděděno z proměnné prostředí přepsat makra souboru pravidel se stejným názvem. Použití **! UNDEF** přepsat příkazového řádku.

## <a name="see-also"></a>Viz také

[Definice makra NMAKE](../build/defining-an-nmake-macro.md)