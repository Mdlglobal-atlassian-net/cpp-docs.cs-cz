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
ms.openlocfilehash: 6a55fd616a00aeb3ade229bf7cff8220f86085b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295042"
---
# <a name="bscmake-command-file-response-file"></a>Soubor příkazů BSCMAKE (soubor odezvy)

> [!WARNING]
> Přestože BSCMAKE je stále instalace sady Visual Studio, se už používá integrovaným vývojovým prostředím. Od verze Visual Studio 2008 je automaticky uloženy informace o procházení a symbol v soubor SDF SQL serveru ve složce řešení.

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

[BSCMAKE – referenční dokumentace](bscmake-reference.md)
