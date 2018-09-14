---
title: Chyba kompilátoru C2857 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/13/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2857
dev_langs:
- C++
helpviewer_keywords:
- C2857
ms.assetid: b57302bd-58ec-45ae-992a-1e282d5eeccc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 49e94e12b4cdf07d9f7fe74dd481bbc032a937eb
ms.sourcegitcommit: 87d317ac62620c606464d860aaa9e375a91f4c99
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45601376"
---
# <a name="compiler-error-c2857"></a>Chyba kompilátoru C2857

> "#include" výraz zadaný s možností / Yc*filename* možnost příkazového řádku se nenašel ve zdrojovém souboru

[/Yc](../../build/reference/yc-create-precompiled-header-file.md) parametr určuje název vloženého souboru, který není zahrnutý ve zdrojovém souboru, který je kompilován.

## <a name="remarks"></a>Poznámky

Při použití **/Yc**<em>filename</em> musí zahrnovat možnost na zdrojový soubor vytvoření souboru předkompilované hlavičky (PCH), který zdrojového souboru *filename* hlavičkový soubor. Každý souboru zahrnutém ve zdrojového souboru, až po a včetně zadaného *filename*, jsou uvedeny v souboru PCH. V jiných zdrojových souborech zkompilován s použitím **/Yu**<em>filename</em> možnost použít soubor PCH souboru zahrnutí z *filename* musí být na prvním řádku mimo komentář v souboru. Kompilátor ignoruje nic ve zdrojovém souboru před tuto zahrnout.

Tuto chybu může způsobovat `#include "filename"` příkazu v bloku podmíněné kompilace, který se zkompiluje do zdrojového souboru PCH.

## <a name="example"></a>Příklad

Typické použití jeden zdrojový soubor v projektu je určen jako zdrojový soubor PCH a jeden soubor záhlaví se používá jako soubor hlaviček PCH. Typický soubor hlaviček PCH má některé hlavičky knihovny použitých v projektu, ale není místní hlavičky, které jsou stále ve vývoji. V tomto příkladu je soubor hlaviček PCH s názvem *my_pch.h*.

```cpp
// my_pch.h
#pragma once
#include <stdio.h>
```

Zdrojový soubor PCH je zkompilován s použitím **/Yc**<em>my_pch.h</em> možnost. Pokud kompilátor nenajde zahrnutí tohoto souboru hlaviček PCH, generuje C2857:

```cpp
// my_pch.cpp
// Compile by using: cl /EHsc /W4 /Yumy_pch.h /c my_pch.cpp

#if 0
#include "my_pch.h"  // C2857; remove conditional directives to fix
#endif
```

S použitím tohoto souboru PCH, zdrojové soubory musí být zkompilovány pomocí **/Yu**<em>my_pch.h</em> možnost. Soubor hlaviček PCH musí být nejprve zahrnuté ve zdrojových souborech, které používají soubor PCH:

```cpp
// C2857.cpp
// Compile my_pch.cpp first, then
// compile by using: cl /EHsc /W4 /Yumy_pch.h my_project.cpp my_pch.obj
// Include the pch header before any other non-comment line
#include "my_pch.h"

int main()
{
    puts("Using a precompiled header file.\n");
}
```