---
title: MBCS – tipy pro programování | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- _mbcs
dev_langs:
- C++
helpviewer_keywords:
- programming [C++], MBCS
- character sets [C++], multibyte
- MBCS [C++], programming
- multibyte characters [C++]
ms.assetid: d8ad36b8-917f-474e-8adb-69462adecd17
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7eb6e298961580c959235a97f37793df41d1124f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="mbcs-programming-tips"></a>MBCS – tipy pro programování
Při vývoji nových aplikací byste měli používat kódování znaků Unicode pro všechny řetězce, které pravděpodobně koncoví uživatelé setkat. Znakové sady MBCS je starší verze technologie, která byla nahrazena kódování Unicode. Tento oddíl poskytuje tipy pro vývojáře, kteří musí zachovat existující programy, které používají rozhraní MBCS a pokud to není praktické převést na kódování Unicode. Doporučení platí pro aplikace MFC a aplikace napsané bez MFC. Témata zahrnují:  
  
-   [Obecné rady k programování se znakovou sadou MBCS](../text/general-mbcs-programming-advice.md)  
  
-   [Inkrementace a dekrementace ukazatelů](../text/incrementing-and-decrementing-pointers.md)  
  
-   [Bajtové indexy](../text/byte-indices.md)  
  
-   [Poslední znak v řetězci](../text/last-character-in-a-string.md)  
  
-   [Přiřazení znaků](../text/character-assignment.md)  
  
-   [Porovnávání znaků](../text/character-comparison.md)  
  
-   [Přetečení vyrovnávací paměti](../text/buffer-overflow.md)  
  
## <a name="see-also"></a>Viz také  
 [Podpora vícebajtových znakových sad (MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)