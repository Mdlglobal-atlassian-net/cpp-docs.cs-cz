---
title: Priority v definicích maker | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, precedence in macro definitions
- macros, precedence
ms.assetid: 0c13182d-83cb-4cbd-af2d-f4c916b62aeb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 21a3d8873fd1fee61afec865181bab27305bebfd
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722212"
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