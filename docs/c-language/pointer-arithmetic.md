---
title: Aritmetika ukazatele | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- pointer arithmetic
- arithmetic pointer
ms.assetid: eb924a29-59d3-48a5-9d62-9424790730eb
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6d74dfdf716065384a1c0a65a6a2bf0e5437dc1e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="pointer-arithmetic"></a>Aritmetika ukazatele
Aditivní operace, které zahrnují ukazatel na celé číslo, dávají smysluplné výsledky, pouze pokud operand ukazatele adresuje člena pole a pokud celočíselná hodnota vytvoří posunutí v rámci rozmezí stejného pole. Při převodu celočíselné hodnoty na posun adresy kompilátor předpokládá, že mezi původní adresou a adresou s posunem leží pouze pozice v paměti stejné velikosti.  
  
 Tento předpoklad platí pro členy pole. Podle definice je pole řada hodnot stejného typu. Jeho prvky jsou umístěny v místech spojité paměti. Úložiště pro libovolné typy, s výjimkou prvků pole, však nemusí být naplněno stejným typem identifikátorů. To znamená, že se mezi paměťovými pozicemi mohou vyskytovat mezery, a to dokonce i mezi pozicemi stejného typu. Proto nejsou definovány výsledky přičítání nebo odčítání adres z libovolných hodnot, s výjimkou prvků.  
  
 Podobně jsou-li odečteny dvě hodnoty ukazatele, převod předpokládá, že mezi dvěma adresami zadanými operandy leží pouze hodnoty stejného typu bez mezer.  
  
## <a name="see-also"></a>Viz také  
 [Operátory sčítání jazyka C](../c-language/c-additive-operators.md)