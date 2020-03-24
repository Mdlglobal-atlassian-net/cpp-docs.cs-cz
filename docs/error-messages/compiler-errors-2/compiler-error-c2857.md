---
title: Chyba kompilátoru C2857
ms.date: 09/13/2018
f1_keywords:
- C2857
helpviewer_keywords:
- C2857
ms.assetid: b57302bd-58ec-45ae-992a-1e282d5eeccc
ms.openlocfilehash: 11b620f9748ac85e731d79b0652c0392375b2ea4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201848"
---
# <a name="compiler-error-c2857"></a>Chyba kompilátoru C2857

> příkaz #include zadaný s parametrem příkazového řádku/YC*filename* nebyl ve zdrojovém souboru nalezen.

Možnost [/YC](../../build/reference/yc-create-precompiled-header-file.md) Určuje název zahrnutého souboru, který není součástí zkompilovaného zdrojového souboru.

## <a name="remarks"></a>Poznámky

Použijete-li ve zdrojovém souboru možnost **/YC**<em>filename</em> pro vytvoření souboru předkompilované hlavičky (PCH), tento zdrojový soubor musí zahrnovat hlavičkový soubor *filename* . Do souboru PCH je zahrnut každý soubor, který je součástí zdrojového souboru, a to včetně zadaného *názvu souboru*. V jiných zdrojových souborech kompilovaných pomocí možnosti **/Yu**<em>filename</em> pro použití souboru PCH musí být zahrnutí *filename* první řádek bez komentáře v souboru. Kompilátor ve zdrojovém souboru před tímto zahrnutím ignoruje cokoli.

Tato chyba může být způsobena výrazem `#include "filename"` v bloku podmíněné kompilace, který není zkompilován ve vašem zdrojovém souboru PCH.

## <a name="example"></a>Příklad

V typickém použití je jeden zdrojový soubor v projektu označený jako zdrojový soubor PCH a jeden hlavičkový soubor se používá jako hlavičkový soubor PCH. Typický hlavičkový soubor PCH obsahuje všechna záhlaví knihoven použitá ve vašem projektu, ale ne místní hlavičky, které jsou stále ve vývoji. V této ukázce má hlavičkový soubor PCH název *my_pch. h*.

```cpp
// my_pch.h
#pragma once
#include <stdio.h>
```

Zdrojový soubor PCH je zkompilován pomocí možnosti **/Yc**<em>my_pch. h</em> . Pokud kompilátor nenajde zahrnutí tohoto hlavičkového souboru PCH, generuje C2857:

```cpp
// my_pch.cpp
// Compile by using: cl /EHsc /W4 /Yumy_pch.h /c my_pch.cpp

#if 0
#include "my_pch.h"  // C2857; remove conditional directives to fix
#endif
```

Chcete-li použít tento soubor PCH, zdrojové soubory musí být zkompilovány pomocí možnosti **/Yu**<em>my_pch. h</em> . Hlavičkový soubor PCH musí být zahrnut jako první ve zdrojových souborech, které používají PCH:

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
