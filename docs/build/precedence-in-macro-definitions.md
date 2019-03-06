---
title: Priority v definicích maker
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, precedence in macro definitions
- macros, precedence
ms.assetid: 0c13182d-83cb-4cbd-af2d-f4c916b62aeb
ms.openlocfilehash: 7f847cd7cea736ff9b4360a050767d00bd6cf539
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421499"
---
# <a name="precedence-in-macro-definitions"></a>Priority v definicích maker

Pokud makro má několik definic, používá NMAKE definici nejvyšší prioritu. Následující seznam uvádí pořadí dle priority od nejvyšší po nejnižší:

1. Makro definované v příkazovém řádku

1. Makro definované v souboru pravidel nebo soubor k zahrnutí

1. Zděděné makra proměnné prostředí

1. Makro definované v souboru Tools.ini

1. Předdefinované makro, jako například [kopie](../build/command-macros-and-options-macros.md) a [AS](../build/command-macros-and-options-macros.md)

/E použijte, aby makra zděděno z proměnné prostředí přepsat makra souboru pravidel se stejným názvem. Použití **! UNDEF** přepsat příkazového řádku.

## <a name="see-also"></a>Viz také:

[Definice makra NMAKE](../build/defining-an-nmake-macro.md)
