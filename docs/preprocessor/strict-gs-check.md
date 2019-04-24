---
title: strict_gs_check
ms.date: 11/04/2016
f1_keywords:
- strict_gs_check
- strict_gs_check_CPP
helpviewer_keywords:
- strict_gs_check pragma
ms.assetid: decfec81-c916-42e0-a07f-8cc26df6a7ce
ms.openlocfilehash: b62e1be466e65c0de6fb4eaa33ac6e99915529e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62179942"
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

Dává pokyn kompilátoru k vložení náhodných souborů cookie do zásobníku funkce pro zjištění některých kategorií přetečení vyrovnávací paměti založené na zásobníku. Ve výchozím nastavení `/GS` (Kontrola zabezpečení vyrovnávací paměti) – možnost kompilátoru k vložení do souboru cookie pro všechny funkce. Další informace najdete v tématu [/GS (Kontrola zabezpečení vyrovnávací paměti)](../build/reference/gs-buffer-security-check.md).

Je nutné kompilovat s `/GS` (Kontrola zabezpečení vyrovnávací paměti) umožňující **strict_gs_check**.

Tuto direktivu pragma je třeba použít u modulů kódu, které jsou vystaveny potenciálně škodlivým datům. Direktiva pragma je velmi agresivní a je použita na funkce, které tuto obranu pravděpodobně potřebovat nebudou, ale je optimalizována pro minimalizaci vlivu na výkon výsledné aplikace.

I když bude tato direktiva pragma použita, je nutné snažit se psát bezpečný kód. To znamená Ujistěte se, že váš kód nemá žádné přetečení vyrovnávací paměti. **strict_gs_check** může chránit aplikace od přetečení vyrovnávací paměti, které zůstávají ve vašem kódu.

## <a name="example"></a>Příklad

V následujícím kódu dochází k přetečení vyrovnávací paměti při kopírování pole do místního pole. Při kompilaci tohoto kódu s `/GS`, žádný soubor cookie je vložen do zásobníku, protože datový typ pole je ukazatel. Přidávání **strict_gs_check** – Direktiva pragma vynutí soubor cookie zásobníku do zásobníku funkce.

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

## <a name="see-also"></a>Viz také:

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)<br/>
[/GS (kontrola zabezpečení vyrovnávací paměti)](../build/reference/gs-buffer-security-check.md)