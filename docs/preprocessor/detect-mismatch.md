---
title: detect_mismatch
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.detect_mismatch
- detect_mismatch_CPP
helpviewer_keywords:
- pragmas, detect_mismatch
- detect_mismatch pragma
ms.assetid: ddb13ac9-0e2f-40ce-be69-7e44c04f5a12
ms.openlocfilehash: 42a3ba61cefe3b2db01aef24b802e3a51fed55d9
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59026703"
---
# <a name="detectmismatch"></a>detect_mismatch
Umístí do objektu záznam. Linker zkontroluje tyto záznamy a vyhledá potenciální problémy.

## <a name="syntax"></a>Syntaxe

```
#pragma detect_mismatch("name", "value")
```

## <a name="remarks"></a>Poznámky

Při propojení projektu vyvolá linker chybu `LNK2038`, pokud projekt obsahuje dva objekty, které mají stejný název `name`, ale každý má jinou hodnotu `value`. Pomocí této direktivy pragma lze zabránit v propojení nekonzistentních objektových souborů.

Název a hodnota jsou řetězcové literály a dodržují pravidla pro řetězcové literály, pokud jde o řídicí znaky a zřetězení. Jsou malá a velká písmena a nemůže obsahovat čárku, znaménko rovnosti, uvozovky, nebo **null** znak.

## <a name="example"></a>Příklad

Tento příklad vytvoří dva soubory, které mají různá čísla verze pro stejný popisek verze.

```cpp
// pragma_directive_detect_mismatch_a.cpp
#pragma detect_mismatch("myLib_version", "9")
int main ()
{
   return 0;
}

// pragma_directive_detect_mismatch_b.cpp
#pragma detect_mismatch("myLib_version", "1")
```

Jsou-li oba soubory zkompilovány pomocí příkazového řádku `cl pragma_directive_detect_mismatch_a.cpp pragma_directive_detect_mismatch_b.cpp`, dojde k chybě `LNK2038`.

## <a name="see-also"></a>Viz také:

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
