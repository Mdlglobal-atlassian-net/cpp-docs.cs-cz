---
title: Chyba linkerů LNK1181
ms.date: 08/22/2018
f1_keywords:
- LNK1181
helpviewer_keywords:
- LNK1181
ms.assetid: 984b0db6-e331-4284-b2a7-a212fe96c486
ms.openlocfilehash: d2b28af52a2ca2263a7bad77c8c69242396ff2b4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195250"
---
# <a name="linker-tools-error-lnk1181"></a>Chyba linkerů LNK1181

vstupní soubor filename nelze otevřít.

Linker nemohl najít `filename`, protože neexistuje nebo cesta nebyla nalezena.

Mezi běžné příčiny chyby LINKERŮ LNK1181 patří:

- na `filename` se odkazuje jako na další závislost na čáře linkeru, ale soubor neexistuje.

- Příkaz **/LIBPATH** , který určuje adresář obsahující `filename` chybí.

Chcete-li vyřešit výše uvedené problémy, zajistěte, aby byly v systému přítomny všechny soubory, na které se odkazuje v propojovacím programu  Také zajistěte, aby byl k dispozici příkaz **/LIBPATH** pro každý adresář obsahující soubor závislý na linkeru.

Další informace naleznete v tématu [soubory. lib jako vstup linkeru](../../build/reference/dot-lib-files-as-linker-input.md).

Další možnou příčinou pro LINKERŮ LNK1181 je, že dlouhý název souboru s vloženými mezerami nebyl uzavřen do uvozovek.  V takovém případě linker rozpozná pouze název souboru až do prvního místa a pak předpokládá příponu souboru. obj.  Řešením v této situaci je uzavřít dlouhý název souboru (cesta plus název souboru) v uvozovkách.

Kompilace s možností [/p (předzpracování souboru)](../../build/reference/p-preprocess-to-a-file.md) může mít za následek linkerů LNK1181, protože tato možnost potlačuje vytváření souborů. obj.

## <a name="see-also"></a>Viz také

[/LIBPATH (další proměnná Libpath)](../../build/reference/libpath-additional-libpath.md)
