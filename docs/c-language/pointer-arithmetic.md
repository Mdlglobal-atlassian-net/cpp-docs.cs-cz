---
title: Aritmetika ukazatele | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- pointer arithmetic
- arithmetic pointer
ms.assetid: eb924a29-59d3-48a5-9d62-9424790730eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c0cbaa5d71b0867ff355e194ad6c82c120148d76
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="pointer-arithmetic"></a>Aritmetika ukazatele
Aditivní operace, které zahrnují ukazatel na celé číslo, dávají smysluplné výsledky, pouze pokud operand ukazatele adresuje člena pole a pokud celočíselná hodnota vytvoří posunutí v rámci rozmezí stejného pole. Při převodu celočíselné hodnoty na posun adresy kompilátor předpokládá, že mezi původní adresou a adresou s posunem leží pouze pozice v paměti stejné velikosti.  
  
 Tento předpoklad platí pro členy pole. Podle definice je pole řada hodnot stejného typu. Jeho prvky jsou umístěny v místech spojité paměti. Úložiště pro libovolné typy, s výjimkou prvků pole, však nemusí být naplněno stejným typem identifikátorů. To znamená, že se mezi paměťovými pozicemi mohou vyskytovat mezery, a to dokonce i mezi pozicemi stejného typu. Proto nejsou definovány výsledky přičítání nebo odčítání adres z libovolných hodnot, s výjimkou prvků.  
  
 Podobně jsou-li odečteny dvě hodnoty ukazatele, převod předpokládá, že mezi dvěma adresami zadanými operandy leží pouze hodnoty stejného typu bez mezer.  
  
## <a name="see-also"></a>Viz také  
 [Sčítací operátory jazyka C](../c-language/c-additive-operators.md)