---
title: "Ukládání textových literálů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: string literals, storage
ms.assetid: ba5e4d2c-d456-44b3-a8ca-354af547ac50
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2a1a001899e46fbd8894b72f2c8cd806f1834b7e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="storage-of-string-literals"></a>Ukládání textových literálů
Znaky textového literálu jsou uloženy v pořadí v oblastech souvislé paměti. Řídicí sekvence (například  **\\ \\**  nebo  **\\"**) v rámci řetězcový literál počítá jako jeden znak. Znak hodnoty null (reprezentována **\0** řídicí sekvenci) se automaticky připojí k a označí konce, každý řetězce literálu. (K tomu dojde během [fáze překladu](../preprocessor/phases-of-translation.md) 7.) Všimněte si, že kompilátor nemusí ukládat dva identické řetězce na dva různé adresy. [/GF](../build/reference/gf-eliminate-duplicate-strings.md) vynutí kompilátoru umístit jenom jedna kopie identické řetězců do spustitelného souboru.  
  
## <a name="remarks"></a>Poznámky  
 **Konkrétní Microsoft**  
  
 Řetězce mají statickou dobu ukládání. V tématu [třídy úložiště](../c-language/c-storage-classes.md) informace o trvání uložení.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Textové literály jazyka C](../c-language/c-string-literals.md)