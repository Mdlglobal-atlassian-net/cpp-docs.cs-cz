---
title: strict_gs_check – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- strict_gs_check
- strict_gs_check_CPP
helpviewer_keywords:
- strict_gs_check pragma
ms.assetid: decfec81-c916-42e0-a07f-8cc26df6a7ce
ms.openlocfilehash: 0b66e87f2280c923d05103fccfcbbc8d32daf3fd
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216593"
---
# <a name="strict_gs_check-pragma"></a>strict_gs_check – direktiva pragma

Tato direktiva pragma poskytuje rozšířenou kontrolu zabezpečení.

## <a name="syntax"></a>Syntaxe

> **#pragma strict_gs_check (**  | [ **push,** ] {**off** } **)** \
> **#pragma strict_gs_check (pop)**

## <a name="remarks"></a>Poznámky

Dává pokyn kompilátoru k vložení náhodných souborů cookie do zásobníku funkce pro zjištění některých kategorií přetečení vyrovnávací paměti založené na zásobníku. Ve výchozím nastavení `/GS` možnost kompilátoru (kontrolní zabezpečení vyrovnávací paměti) nevloží soubor cookie pro všechny funkce. Další informace najdete v tématu [/GS (kontrolní zabezpečení vyrovnávací paměti)](../build/reference/gs-buffer-security-check.md).

Zkompilujte pomocí `/GS` pro povolení **strict_gs_check**.

Tuto direktivu pragma je třeba použít u modulů kódu, které jsou vystaveny potenciálně škodlivým datům. **strict_gs_check** je agresivní direktiva pragma a je použita na funkce, které nemusí tuto obranu potřebovat, ale je optimalizována pro minimalizaci jejího vlivu na výkon výsledné aplikace.

I když bude tato direktiva pragma použita, je nutné snažit se psát bezpečný kód. To znamená, že se ujistěte, že váš kód nemá žádné přetečení vyrovnávací paměti. **strict_gs_check** může chránit vaši aplikaci před přetečením vyrovnávací paměti, která zůstává ve vašem kódu.

## <a name="example"></a>Příklad

V této ukázce dojde k přetečení vyrovnávací paměti při kopírování pole do místního pole. Když kompilujete tento kód s `/GS`, do zásobníku není vložen žádný soubor cookie, protože datový typ pole je ukazatel. Přidání direktivy pragma **strict_gs_check** vynutí soubor cookie zásobníku do zásobníku funkce.

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

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[/GS (kontrolu zabezpečení vyrovnávací paměti)](../build/reference/gs-buffer-security-check.md)
