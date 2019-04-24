---
title: Soubory příkazů CL
ms.date: 11/04/2016
f1_keywords:
- cl
helpviewer_keywords:
- cl.exe compiler, command files
- command files
- command files, CL compiler
ms.assetid: ec3cea06-2af0-4fe9-a94c-119c9d31b3a9
ms.openlocfilehash: 9810f7b4308eab2b47a068072039335e59e19f5f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272582"
---
# <a name="cl-command-files"></a>Soubory příkazů CL

Soubor příkazů je textový soubor, který obsahuje možnosti a názvy souborů, které by v opačném případě zadejte na [příkazového řádku](compiler-command-line-syntax.md) nebo zadat pomocí [proměnné prostředí CL](cl-environment-variables.md). Příkazový soubor kompilátoru CL přijímá jako argument v proměnné prostředí CL nebo na příkazovém řádku. Na rozdíl od příkazového řádku nebo proměnné prostředí CL umožňuje soubor příkazů použít několik řádků parametrů a názvů souborů.

Možnosti a názvy souborů v souboru příkazů se zpracovávají podle umístění v rámci proměnné prostředí CL nebo na příkazovém řádku příkaz název souboru. Ale pokud možnost/Link se zobrazí v souboru příkazů, jsou předány všech možností na rest řádku linkeru. Možnosti v dalších řádcích v souboru příkazů a možnosti příkazového řádku po vyvolání příkazu souboru jsou stále přijímány jako možnosti kompilátoru. Další informace o vlivu pořadí možnosti jejich interpretaci najdete v tématu [pořadí možností CL](order-of-cl-options.md).

Soubor příkazů nesmí obsahovat příkaz CL. Jednotlivé možnosti musí začínat a končit na stejném řádku; nelze použít zpětné lomítko (**\\**) ke sloučení volbu mezi dvěma řádky.

Soubor příkazů je určená zavináč (**\@**) za nímž následuje název souboru; název souboru můžete zadat absolutní nebo relativní cestu.

Například následující příkaz je do souboru s názvem odezvy:

```
/Og /link LIBC.LIB
```

a zadejte následující příkaz CL:

```
CL /Ob2 @RESP MYAPP.C
```

příkaz do CL vypadá takto:

```
CL /Ob2 /Og MYAPP.C /link LIBC.LIB
```

Mějte na paměti, efektivně kombinovat příkazového řádku a příkazy souboru příkazů.

## <a name="see-also"></a>Viz také:

[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[Parametry kompilátoru MSVC](compiler-options.md)
