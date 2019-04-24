---
title: Priority v definicích maker
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, precedence in macro definitions
- macros, precedence
ms.assetid: 0c13182d-83cb-4cbd-af2d-f4c916b62aeb
ms.openlocfilehash: 38a653a9f460beae81f9f88ea457870d30f25339
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320159"
---
# <a name="precedence-in-macro-definitions"></a>Priority v definicích maker

Pokud makro má několik definic, používá NMAKE definici nejvyšší prioritu. Následující seznam uvádí pořadí dle priority od nejvyšší po nejnižší:

1. Makro definované v příkazovém řádku

1. Makro definované v souboru pravidel nebo soubor k zahrnutí

1. Zděděné makra proměnné prostředí

1. Makro definované v souboru Tools.ini

1. Předdefinované makro, jako například [kopie](command-macros-and-options-macros.md) a [AS](command-macros-and-options-macros.md)

/E použijte, aby makra zděděno z proměnné prostředí přepsat makra souboru pravidel se stejným názvem. Použití **! UNDEF** přepsat příkazového řádku.

## <a name="see-also"></a>Viz také:

[Definice makra NMAKE](defining-an-nmake-macro.md)
