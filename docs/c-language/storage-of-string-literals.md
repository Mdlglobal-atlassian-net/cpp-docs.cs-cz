---
title: Ukládání textových literálů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- string literals, storage
ms.assetid: ba5e4d2c-d456-44b3-a8ca-354af547ac50
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9d87998f7e9d579c012f5db2f38f20886c1e74c6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32387031"
---
# <a name="storage-of-string-literals"></a>Ukládání textových literálů
Znaky textového literálu jsou uloženy v pořadí v oblastech souvislé paměti. Řídicí sekvence (například **\\ \\** nebo  **\\"**) v rámci řetězcový literál počítá jako jeden znak. Znak hodnoty null (reprezentována **\0** řídicí sekvenci) se automaticky připojí k a označí konce, každý řetězce literálu. (K tomu dojde během [fáze překladu](../preprocessor/phases-of-translation.md) 7.) Všimněte si, že kompilátor nemusí ukládat dva identické řetězce na dva různé adresy. [/GF](../build/reference/gf-eliminate-duplicate-strings.md) vynutí kompilátoru umístit jenom jedna kopie identické řetězců do spustitelného souboru.  
  
## <a name="remarks"></a>Poznámky  
 **Konkrétní Microsoft**  
  
 Řetězce mají statickou dobu ukládání. V tématu [třídy úložiště](../c-language/c-storage-classes.md) informace o trvání uložení.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Textové literály jazyka C](../c-language/c-string-literals.md)