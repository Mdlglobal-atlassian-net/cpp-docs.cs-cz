---
title: /Zc:inline (Odebrat neodkazované sekvence COMDAT)
ms.date: 09/05/2019
f1_keywords:
- /Zc:inline
- VC.Project.VCCLCompilerTool.RemoveUnreferencedCodeData
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Zc compiler options (C++)
- /Zc:inline
ms.assetid: a4c94224-1d73-4bea-a9d5-4fa73dc924df
ms.openlocfilehash: 42791b2e337fb9a9724a165145e757152b8d679d
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518241"
---
# <a name="zcinline-remove-unreferenced-comdat"></a>/Zc:inline (Odebrat neodkazované sekvence COMDAT)

Odebere neodkazovaná data nebo funkce, které jsou sekvence COMDAT nebo které mají pouze interní propojení. V rámci **/Zc: inline**kompilátor určuje, že jednotky překladu s vloženými daty nebo funkcemi musí také zahrnovat jejich definice.

## <a name="syntax"></a>Syntaxe

> **/Zc:inline**[ **-** ]

## <a name="remarks"></a>Poznámky

Při zadání parametru **/Zc: inline** Kompilátor negeneruje informace o symbolech pro neodkazované funkce COMDAT nebo data. Nebo pro data nebo funkce, které mají pouze interní propojení. Tato optimalizace zjednodušuje některé práce, které linker provádí v sestaveních vydaných verzí, nebo když zadáte možnost linkeru [/OPT: ref](opt-optimizations.md) . Tato optimalizace kompilátoru může významně snížit velikost souboru. obj a zlepšit rychlost linkeru. Možnost kompilátoru není povolená, pokud zakážete optimalizace ([/od](od-disable-debug.md)). Nebo, pokud zadáte [/GL (celá optimalizace programu)](gl-whole-program-optimization.md).

Ve výchozím nastavení je tato možnost vypnuta ( **/Zc: inline-** ) v sestaveních příkazového řádku. Možnost [/Permissive-](permissive-standards-conformance.md) nepovoluje **/Zc: inline**. V projektech MSBuild je tato možnost nastavena pomocí **vlastností konfigurace** > **jazyka** **C++ C/**  >  > **Odebrat neodkazovaný kód a vlastnost dat** , která je ve výchozím nastavení nastavena na **hodnotu Ano** .

Je-li zadán parametr **/Zc: inline** , vynutil kompilátor požadavek c++ 11, že všechny funkce deklarované `inline` musí mít definici dostupnou ve stejné jednotce překladu, pokud jsou použity. Pokud možnost není zadána, kompilátor společnosti Microsoft povolí nevyhovující kód, který vyvolá funkce deklarované `inline` i v případě, že není zobrazena žádná definice. Další informace najdete v části Standard C++ 11 v oddílu 3,2 a bodě 7.1.2. Tato možnost kompilátoru byla představena ve Visual Studio 2013 Update 2.

Chcete-li použít možnost **/Zc: inline** , aktualizujte kód, který nedodržuje předpisy.

Tento příklad ukazuje, jak je nevyhovující použití vložené deklarace funkce bez definice stále kompilována a odkazy, pokud je použita výchozí hodnota **/Zc: inline-** Option:

```cpp
// example.h
// Compile by using: cl /W4 /EHsc /O2 zcinline.cpp example.cpp
#pragma once

class Example {
public:
   inline void inline_call(); // declared but not defined inline
   void normal_call();
   Example() {};
};
```

```cpp
// example.cpp
// Compile by using: cl /W4 /EHsc /O2 zcinline.cpp example.cpp
#include <stdio.h>
#include "example.h"

void Example::inline_call() {
   printf("inline_call was called.\n");
}

void Example::normal_call() {
   printf("normal_call was called.\n");
   inline_call(); // with /Zc:inline-, inline_call forced into .obj file
}
```

```cpp
// zcinline.cpp
// Compile by using: cl /W4 /EHsc /O2 zcinline.cpp example.cpp
#include "example.h"

int main() {
   Example example;
   example.inline_call(); // normal call when definition unavailable
}
```

Když je povoleno **/Zc: inline** , stejný kód způsobí chybu [linkerů LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md) , protože kompilátor negeneruje tělo nevloženého kódu pro `Example::inline_call` v příkladu. obj. To způsobí, že nevložené volání v `main` odkazuje na nedefinovaný externí symbol.

Chcete-li tuto chybu vyřešit, můžete odebrat klíčové slovo `inline` z deklarace `Example::inline_call`, přesunout definici `Example::inline_call` do souboru hlaviček nebo přesunout implementaci `Example` do Main. cpp. V dalším příkladu je přesunuta definice do hlavičkového souboru, kde je viditelná pro libovolného volajícího, který obsahuje hlavičku.

```cpp
// example2.h
// Compile by using: cl /W4 /EHsc /O2 zcinline2.cpp example2.cpp
#pragma once
#include <stdio.h>

class Example2 {
public:
   inline void inline_call() {
      printf("inline_call was called.\n");
   }
   void normal_call();
   Example2() {};
};
```

```cpp
// example2.cpp
// Compile by using: cl /W4 /EHsc /O2 zcinline2.cpp example2.cpp
#include "example2.h"

void Example2::normal_call() {
   printf("normal_call was called.\n");
   inline_call();
}
```

```cpp
// zcinline2.cpp
// Compile by using: cl /W4 /EHsc /O2 zcinline2.cpp example2.cpp
#include "example2.h"

int main() {
   Example2 example2;
   example2.inline_call(); // normal call when definition unavailable
}
```

Další informace o problémech s kompatibilitou ve vizuálu C++najdete v tématu [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **Vlastnosti konfigurace** > stránce vlastností **jazyka** **CC++ /**  > .

1. Upravte vlastnost **Odebrat neodkazovaný kód a data** a pak klikněte na **tlačítko OK**.

## <a name="see-also"></a>Viz také:

[/Zc (shoda)](zc-conformance.md)<br/>
