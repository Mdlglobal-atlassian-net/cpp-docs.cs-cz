---
title: Chyba Linkerů LNK1181 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/22/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1181
dev_langs:
- C++
helpviewer_keywords:
- LNK1181
ms.assetid: 984b0db6-e331-4284-b2a7-a212fe96c486
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 787c6c35b698b5dce57c4aaf3acb4eca496ead95
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50072158"
---
# <a name="linker-tools-error-lnk1181"></a>Chyba linkerů LNK1181

vstupní soubor 'filename' nelze otevřít.

Nelze najít linker `filename` protože neexistuje nebo cesta nebyla nalezena.

Některé běžné příčiny chyby LNK1181 patří:

- `filename` je odkazováno jako další závislost na řádku linkeru, ale soubor neexistuje.

- A **/Libpath** příkaz, který určuje adresáře, který obsahuje `filename` chybí.

Chcete-li vyřešit uvedené problémy, zajistěte, aby všechny soubory, které odkazuje na řádku linkeru jsou k dispozici v systému.  Také zajistěte **/Libpath** příkaz pro každý adresář obsahující soubor závislé na linkeru.

Další informace najdete v tématu [soubory .lib jako vstup Linkeru](../../build/reference/dot-lib-files-as-linker-input.md).

LNK1181 další možnou příčinou je, že dlouhý název souboru s vloženými mezerami nebyla uzavřena v uvozovkách.  V takovém případě bude linker pouze rozpoznat název souboru až po první místo a potom předpokládají příponu souboru. Knihovna  Řešení tuto situaci lze vyřešit, je uzavřete dlouhý název souboru (název cesty a soubor) do uvozovek.

Kompilace s [/P (předběžné zpracování souboru)](../../build/reference/p-preprocess-to-a-file.md) možnost může vést LNK1181, protože tato možnost potlačí vytváření soubory .obj.

## <a name="see-also"></a>Viz také

[/LIBPATH (další proměnná Libpath)](../../build/reference/libpath-additional-libpath.md)