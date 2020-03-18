---
title: Soubory příkazů CL
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, command files
- command files
- command files, CL compiler
ms.assetid: ec3cea06-2af0-4fe9-a94c-119c9d31b3a9
ms.openlocfilehash: 1dc2d6bffe4d0681a04b875383215a0bbfc1a720
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440262"
---
# <a name="cl-command-files"></a>Soubory příkazů CL

Soubor příkazů je textový soubor, který obsahuje možnosti a názvy souborů, které byste jinak zadali do [příkazového řádku](compiler-command-line-syntax.md) nebo určili pomocí [proměnné prostředí CL](cl-environment-variables.md). CL přijme soubor příkazů kompilátoru jako argument v proměnné prostředí CL nebo na příkazovém řádku. Na rozdíl od příkazového řádku nebo proměnné prostředí CL umožňuje soubor příkazů použít několik řádků parametrů a názvů souborů.

Možnosti a názvy souborů v souboru příkazů jsou zpracovány podle umístění příkazu filename v proměnné prostředí CL nebo na příkazovém řádku. Nicméně pokud se v souboru příkazů objeví možnost/Link, všechny možnosti na zbytek řádku jsou předány do linkeru. Možnosti na dalších řádcích v souboru příkazů a možnosti příkazového řádku po vyvolání souboru příkazů jsou stále přijaty jako možnosti kompilátoru. Další informace o tom, jak pořadí možností ovlivňuje jejich výklad, naleznete v části [pořadí možností CL](order-of-cl-options.md).

Soubor příkazů nesmí obsahovat příkaz CL. Každá možnost musí na stejném řádku začínat a končit; pomocí zpětného lomítka ( **\\** ) nelze kombinovat možnost mezi dvěma řádky.

Soubor příkazů je určen znakem po znaku ( **\@** ) následovaným názvem souboru; název souboru může určovat absolutní nebo relativní cestu.

Například pokud je následující příkaz v souboru s názvem ODP:

```
/Og /link LIBC.LIB
```

a zadáte následující příkaz CL:

```
CL /Ob2 @RESP MYAPP.C
```

příkaz pro CL je následující:

```
CL /Ob2 /Og MYAPP.C /link LIBC.LIB
```

Všimněte si, že příkazový řádek a příkazy příkazového souboru jsou efektivně kombinovány.

## <a name="see-also"></a>Viz také

[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[Parametry kompilátoru MSVC](compiler-options.md)
