---
title: /Zc:inline (Odebrat neodkazované sekvence COMDAT)
ms.date: 03/01/2018
f1_keywords:
- /Zc:inline
- VC.Project.VCCLCompilerTool.RemoveUnreferencedCodeData
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Zc compiler options (C++)
- /Zc:inline
ms.assetid: a4c94224-1d73-4bea-a9d5-4fa73dc924df
ms.openlocfilehash: 06bdb3300aae88c6c4c8f7e66af658f47548ac5a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316051"
---
# <a name="zcinline-remove-unreferenced-comdat"></a>/Zc:inline (Odebrat neodkazované sekvence COMDAT)

Odebere neodkazovaná funkce nebo data, která jsou sekvence Comdat nebo pouze mít interní vazbu. Když **/Zc: Inline** není zadán, kompilátor, vyžaduje jednotkách překladu, které používají vložená data nebo vložené funkce musí obsahovat také definice pro data nebo funkce.

## <a name="syntax"></a>Syntaxe

> **/Zc:inline**[**-**]

## <a name="remarks"></a>Poznámky

Když **/Zc: Inline** není zadán, kompilátor negeneruje informace o symbolech pro neodkazované sekvence COMDAT funkce nebo data, nebo pro funkce nebo data, která mají jenom vnitřní vazby. Tato optimalizace zjednodušuje některé akce prováděné v linkeru v sestaveních pro vydání a kdy možností propojovacího programu [OPT](opt-optimizations.md) je zadán. Když kompilátor provádí tyto optimalizace, může výrazně zmenšit velikost souboru .obj a zvýšení rychlosti linkeru. Tato možnost kompilátoru není povolena, pokud jsou zakázané optimalizace ([/Od](od-disable-debug.md)) nebo když [/GL (optimalizace celého programu)](gl-whole-program-optimization.md) určena.

Ve výchozím nastavení, tato možnost je vypnuta (**/Zc:inline-**). [/ Permissive-](permissive-standards-conformance.md) možnost nepovolíte **/Zc: Inline**.

Pokud **/Zc: Inline** není zadána, vynucuje kompilátor C ++ 11 požadavku, že všechny funkce deklarované `inline` musejí obsahovat definici k dispozici ve stejné jednotce překladu, pokud jsou použity. Pokud není zadán parametr, kompilátor společnosti Microsoft umožňuje kódu nesplňuje podmínky shody, který vyvolá funkce deklarované `inline` i v případě, že je viditelná žádná definice. Další informace najdete v tématu standard C ++ 11, v části 3.2 a části 7.1.2. Tato možnost kompilátoru byla zavedena v aplikaci Visual Studio 2013 Update 2.

Použít **/Zc: Inline** možnost aktualizace kódu nedodržující předpisy.

Tento příklad ukazuje, jak nedodržující předpisy vloženou deklaraci funkce bez definice stále zkompiluje a propojí kdy výchozí **/Zc:inline-** možnost se používá:

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

Když **/Zc: Inline** je povoleno, stejný kód způsobí, že [LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md) chybu, protože kompilátor negeneruje tělo-vložený kód pro `Example::inline_call` v example.obj. To způsobí, že není vložená volání v `main` k odkazování nedefinovaného symbolu externí.

Chcete-li vyřešit tuto chybu, můžete odebrat `inline` – klíčové slovo z deklarace `Example::inline_call`, definice typu přesuňte `Example::inline_call` do záhlaví souboru, nebo přesunout provádění `Example` do main.cpp. Následující příklad definice přesune do souboru hlaviček, ve kterém je viditelná pro všechny volající, který obsahuje hlavičku.

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

Další informace o problémech přizpůsobení v aplikaci Visual C++, naleznete v tématu [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **jazyk** stránku vlastností.

1. Upravit **odebrat neodkazovaný kód a data** vlastnost a klikněte na tlačítko **OK**.

## <a name="see-also"></a>Viz také:

[/Zc (shoda)](zc-conformance.md)<br/>
