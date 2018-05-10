---
title: strict_gs_check – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- strict_gs_check
- strict_gs_check_CPP
dev_langs:
- C++
helpviewer_keywords:
- strict_gs_check pragma
ms.assetid: decfec81-c916-42e0-a07f-8cc26df6a7ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6b58b02781f266b24fa321b3849f42b2e090b860
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="strictgscheck"></a>strict_gs_check
Tato direktiva pragma poskytuje rozšířenou kontrolu zabezpečení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma strict_gs_check([push,] on )   
#pragma strict_gs_check([push,] off )   
#pragma strict_gs_check(pop)  
```  
  
## <a name="remarks"></a>Poznámky  
 Dává pokyn kompilátoru k vložení náhodných souborů cookie do zásobníku funkce pro zjištění některých kategorií přetečení vyrovnávací paměti založené na zásobníku. Ve výchozím nastavení nevkládá možnost kompilátoru /GS (kontrola zabezpečení vyrovnávací paměti) soubor cookie pro všechny funkce. Další informace najdete v tématu [/GS (Kontrola zabezpečení vyrovnávací paměti)](../build/reference/gs-buffer-security-check.md).  
  
 Pro povolení strict_gs_check je nutné kompilovat s /GS (kontrola zabezpečení vyrovnávací paměti).  
  
 Tuto direktivu pragma je třeba použít u modulů kódu, které jsou vystaveny potenciálně škodlivým datům. Direktiva pragma je velmi agresivní a je použita na funkce, které tuto obranu pravděpodobně potřebovat nebudou, ale je optimalizována pro minimalizaci vlivu na výkon výsledné aplikace.  
  
 I když bude tato direktiva pragma použita, je nutné snažit se psát bezpečný kód. To znamená Ujistěte se, že má váš kód žádné přetečení vyrovnávací paměti. strict_gs_check – může chránit aplikace od přetečení vyrovnávací paměti, které zůstávají ve vašem kódu.  
  
## <a name="example"></a>Příklad  
 V následujícím kódu dochází k přetečení vyrovnávací paměti při kopírování pole do místního pole. Při kompilaci tohoto kódu s /GS nebude do zásobníku vložen žádný soubor cookie, protože datový typ pole je ukazatel. Přidání direktivy pragma strict_gs_check vynutí soubor cookie zásobníku do zásobníku funkce.  
  
```cpp  
// pragma_strict_gs_check.cpp  
// compile with: /c  
  
#pragma strict_gs_check(on)  
  
void ** ReverseArray(void **pData,  
                     size_t cData)  
{  
    // *** This buffer is subject to being overrun!! ***  
    void *pReversed[20];  
  
    // Reverse the array into a temporary buffer  
    for (size_t j = 0, i = cData; i ; --i, ++j)  
        // *** Possible buffer overrun!! ***  
            pReversed[j] = pData[i];   
  
    // Copy temporary buffer back into input/output buffer  
    for (size_t i = 0; i < cData ; ++i)   
        pData[i] = pReversed[i];  
  
    return pData;  
}  
  
```  
  
## <a name="see-also"></a>Viz také  
 [Direktivy pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
 [/GS (kontrola zabezpečení vyrovnávací paměti)](../build/reference/gs-buffer-security-check.md)