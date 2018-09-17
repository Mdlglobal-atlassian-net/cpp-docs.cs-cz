---
title: Soubory příkazů CL | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- cl
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, command files
- command files
- command files, CL compiler
ms.assetid: ec3cea06-2af0-4fe9-a94c-119c9d31b3a9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8458462304a9b739c61997505724d21bb56763f6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45708666"
---
# <a name="cl-command-files"></a>Soubory příkazů CL

Soubor příkazů je textový soubor, který obsahuje možnosti a názvy souborů, které by v opačném případě zadejte na [příkazového řádku](../../build/reference/compiler-command-line-syntax.md) nebo zadat pomocí [proměnné prostředí CL](../../build/reference/cl-environment-variables.md). Příkazový soubor kompilátoru CL přijímá jako argument v proměnné prostředí CL nebo na příkazovém řádku. Na rozdíl od příkazového řádku nebo proměnné prostředí CL umožňuje soubor příkazů použít několik řádků parametrů a názvů souborů.

Možnosti a názvy souborů v souboru příkazů se zpracovávají podle umístění v rámci proměnné prostředí CL nebo na příkazovém řádku příkaz název souboru. Ale pokud možnost/Link se zobrazí v souboru příkazů, jsou předány všech možností na rest řádku linkeru. Možnosti v dalších řádcích v souboru příkazů a možnosti příkazového řádku po vyvolání příkazu souboru jsou stále přijímány jako možnosti kompilátoru. Další informace o vlivu pořadí možnosti jejich interpretaci najdete v tématu [pořadí možností CL](../../build/reference/order-of-cl-options.md).

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

## <a name="see-also"></a>Viz také

[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)<br/>
[Možnosti kompilátoru](../../build/reference/compiler-options.md)