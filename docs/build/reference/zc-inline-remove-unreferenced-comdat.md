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
ms.openlocfilehash: f0c0d9a4e5e5f52d239f1a8591006b3d9e369778
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740113"
---
# <a name="zcinline-remove-unreferenced-comdat"></a>/Zc:inline (Odebrat neodkazované sekvence COMDAT)

Odebere neodkazované funkce nebo data, která jsou sekvence COMDAT nebo mají pouze interní propojení. Když je zadán parametr **/Zc: inline** , kompilátor vyžaduje, aby jednotky překladu, které používají vložená data nebo vložené funkce, měly také zahrnovat definice pro data nebo funkce.

## <a name="syntax"></a>Syntaxe

> **/Zc:inline**[ **-** ]

## <a name="remarks"></a>Poznámky

Když je zadán parametr **/Zc: inline** , kompilátor negeneruje informace o symbolech pro neodkazované funkce nebo data COMDAT nebo pro funkce nebo data, které mají pouze interní propojení. Tato optimalizace zjednodušuje některé práce provedené linkerem v sestavách vydaných verzí nebo v případě, že je zadána možnost linkeru [/OPT: ref](opt-optimizations.md) . Když kompilátor tuto optimalizaci provede, může významně snížit velikost souboru. obj a zvýšit rychlost linkeru. Tato možnost kompilátoru není povolená, když jsou zakázané optimalizace ([/od](od-disable-debug.md)), nebo když se zadá [/GL (celá optimalizace programu)](gl-whole-program-optimization.md) .

Ve výchozím nastavení je tato možnost vypnuta ( **/Zc: inline-** ) v sestaveních příkazového řádku. Možnost [/Permissive-](permissive-standards-conformance.md) nepovoluje **/Zc: inline**. V projektech MSBuild je možnost nastavena pomocí **vlastností** > konfigurace**jazyk** >  > **C/C++** jazyk**Odebrat neodkazovaný kód a vlastnost dat** , která je nastavena na **hodnotu Ano** podle výchozí.

Je-li zadán parametr **/Zc: inline** , vynutil kompilátor požadavek c++ 11, že všechny `inline` deklarované funkce musí mít definici dostupnou ve stejné jednotce překladu, pokud jsou použity. Pokud možnost není zadána, kompilátor společnosti Microsoft povolí nevyhovující kód, který vyvolá funkce deklarované `inline` i v případě, že není zobrazena žádná definice. Další informace najdete v části Standard C++ 11 v oddílu 3,2 a bodě 7.1.2. Tato možnost kompilátoru byla představena ve Visual Studio 2013 Update 2.

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

void main() {
   Example example;
   example.inline_call(); // normal call when definition unavailable
}
```

Když je povolena možnost **/Zc: inline** , stejný kód způsobí chybu [linkerů LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md) , protože kompilátor negeneruje tělo nevloženého `Example::inline_call` kódu v příkladu. obj. To způsobí, že volání `main` bez vloženého objektu odkazuje na nedefinovaný externí symbol.

Chcete-li tuto chybu vyřešit, můžete odebrat `inline` klíčové slovo z `Example::inline_call`deklarace `Example::inline_call` , přesunout definici do `Example` hlavičkového souboru nebo přesunout implementaci do Main. cpp. V dalším příkladu je přesunuta definice do hlavičkového souboru, kde je viditelná pro libovolného volajícího, který obsahuje hlavičku.

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

void main() {
   Example2 example2;
   example2.inline_call(); // normal call when definition unavailable
}
```

Další informace o problémech s kompatibilitou ve vizuálu C++najdete v tématu [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte stránku vlastností **Konfigurace** > **C/C++**  > **jazyk** .

1. Upravte vlastnost **Odebrat neodkazovaný kód a data** a pak klikněte na **tlačítko OK**.

## <a name="see-also"></a>Viz také:

[/Zc (shoda)](zc-conformance.md)<br/>
