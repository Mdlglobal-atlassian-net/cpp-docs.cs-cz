---
title: Soubor příkazů BSCMAKE (soubor odezvy)
ms.date: 11/04/2016
helpviewer_keywords:
- BSCMAKE, response file
- BSCMAKE, command file
- response files, BSCMAKE
- command files, BSCMAKE
- response files
- command files
ms.assetid: abdffeea-35c7-4f2d-8c17-7d0d80bac314
ms.openlocfilehash: 43f5a886dd41941a0675e31bc8c9d3f23c607023
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57426235"
---
# <a name="bscmake-command-file-response-file"></a>Soubor příkazů BSCMAKE (soubor odezvy)

Můžete zadat část nebo všechny z příkazového řádku vstup v souboru příkazů. Zadejte soubor příkazů, použijte tuto syntaxi:

```
BSCMAKE @filename
```

Soubor jenom jeden příkaz je povolen. Můžete zadat cestu s *filename*. Předcházet *filename* s zavináč (**\@**). BscMake – nepředpokládá rozšíření. Můžete zadat další *sbrfiles* na příkazovém řádku po *filename*. Soubor příkazů je textový soubor, který obsahuje vstup do nástroje BSCMAKE ve stejném pořadí, jako by ji zadejte na příkazovém řádku. Argumenty příkazového řádku oddělte jeden nebo více mezery, tabulátory nebo znaky nového řádku.

Následující příkaz volá pomocí soubor příkazů BSCMAKE:

```
BSCMAKE @prog1.txt
```

Následuje ukázkový soubor příkaz:

```
/n /v /o main.bsc /El
/S (
toolbox.h
verdate.h c:\src\inc\screen.h
)
file1.sbr file2.sbr file3.sbr file4.sbr
```

## <a name="see-also"></a>Viz také:

[BSCMAKE – referenční dokumentace](../../build/reference/bscmake-reference.md)
