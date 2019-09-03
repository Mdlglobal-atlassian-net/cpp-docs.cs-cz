---
title: detect_mismatch – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.detect_mismatch
- detect_mismatch_CPP
helpviewer_keywords:
- pragmas, detect_mismatch
- detect_mismatch pragma
ms.assetid: ddb13ac9-0e2f-40ce-be69-7e44c04f5a12
ms.openlocfilehash: 6e247b3f251bce47710a3380fb295597314a3bd8
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222390"
---
# <a name="detect_mismatch-pragma"></a>detect_mismatch – direktiva pragma

Umístí do objektu záznam. Linker zkontroluje tyto záznamy a vyhledá potenciální problémy.

## <a name="syntax"></a>Syntaxe

> **#pragma detect_mismatch (** "*název*" **;** "*hodnota*" **)**

## <a name="remarks"></a>Poznámky

Když propojíte projekt, linker vyvolá chybu [linkerů LNK2038](../error-messages/tool-errors/linker-tools-error-lnk2038.md) , pokud projekt obsahuje dva objekty, které mají stejný *název* , ale každá má jinou *hodnotu*. Pomocí této direktivy pragma lze zabránit v propojení nekonzistentních objektových souborů.

*Název* i *hodnota* jsou řetězcové literály a podléhají pravidlům pro řetězcové literály s ohledem na řídicí znaky a zřetězení. Rozlišují velká a malá písmena a nesmí obsahovat čárku, rovnítko, uvozovky nebo znak **null** .

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

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
