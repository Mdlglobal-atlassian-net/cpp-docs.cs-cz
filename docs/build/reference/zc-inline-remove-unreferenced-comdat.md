---
title: '/ Zc: Inline (odebrat neodkazované sekvence COMDAT) | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc:inline
- VC.Project.VCCLCompilerTool.RemoveUnreferencedCodeData
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Zc compiler options (C++)
- /Zc:inline
ms.assetid: a4c94224-1d73-4bea-a9d5-4fa73dc924df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 067ba5dad4e0751a86835ea56c536a5b7250485d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379585"
---
# <a name="zcinline-remove-unreferenced-comdat"></a>/Zc:inline (Odebrat neodkazované sekvence COMDAT)

Odebere neregistrované funkce nebo data, která jsou COMDATs nebo mít pouze interní propojení. Když **/Zc: Inline** není zadaný, vyžaduje kompilátor, překlad jednotky, které používají data vložené nebo vložené funkce musí také obsahovat definice pro data nebo funkce.

## <a name="syntax"></a>Syntaxe

> **/Zc:inline**[**-**]

## <a name="remarks"></a>Poznámky

Když **/Zc: Inline** není zadaný, kompilátor není emitování informací o symbolu neodkazované sekvence COMDAT funkce nebo data, nebo pro funkce nebo data, která mají jenom vnitřní propojení. Tato optimalizace zjednodušuje část práce prováděné linkeru v sestavení pro vydání nebo když – možnost linkeru [/OPT:REF](../../build/reference/opt-optimizations.md) je zadán. Když kompilátor provede tyto optimalizace, může výrazně snížit velikost souboru .obj a vylepšení rychlostmi linkeru. Pokud jsou zakázány optimalizace není povolené toto – možnost kompilátoru ([/Od](../../build/reference/od-disable-debug.md)) nebo pokud [/GL (optimalizace celého programu)](../../build/reference/gl-whole-program-optimization.md) je zadán.

Ve výchozím nastavení, tato možnost je vypnuta (**/Zc:inline-**). [/ Projektovou-](permissive-standards-conformance.md) možnost neumožňuje **/Zc: Inline**.

Pokud **/Zc: Inline** není zadaný, kompilátor vynucuje C ++ 11 požadavku, že všechny funkce deklarované `inline` musí mít k dispozici ve stejné jednotce překladu definice, pokud se používají. Pokud není zadána možnost, kompilátoru Microsoft umožňuje není vyhovující kód, který volá funkce deklarovaný `inline` i v případě, že je viditelná žádná definice. Další informace najdete v tématu C ++ 11 standard, v části 3.2 a části 7.1.2. Tato možnost kompilátoru byla zavedena v sadě Visual Studio 2013 Update 2.

Použít **/Zc: Inline** možnost nevyhovující kód aktualizace.

Tento příklad ukazuje, jak nevyhovující použití deklarace vložené funkce bez definice stále zkompiluje a odkazy, kdy výchozí **/Zc:inline-** se používá možnost:

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

Když **/Zc: Inline** je povoleno, stejný kód příčiny [LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md) chyby, protože kompilátor není emitování text-vložená kód pro `Example::inline_call` v example.obj. To způsobí, že není vložená volání v `main` Chcete-li nedefinované externí symbol.

Chcete-li tuto chybu vyřešit, můžete odebrat `inline` – klíčové slovo z deklaraci `Example::inline_call`, přesunout definice `Example::inline_call` do záhlaví souboru nebo přesunout implementace `Example` do main.cpp. Další příklad přesune definici do soubor hlaviček, kde je viditelná pro všechny volající, který obsahuje hlavičku.

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

Další informace o problémech shoda v jazyce Visual C++, najdete v části [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **jazyk** stránku vlastností.

1. Změnit **odebrat neodkazované kód a data** vlastnost a potom zvolte **OK**.

## <a name="see-also"></a>Viz také

[/Zc (shoda)](../../build/reference/zc-conformance.md)<br/>
