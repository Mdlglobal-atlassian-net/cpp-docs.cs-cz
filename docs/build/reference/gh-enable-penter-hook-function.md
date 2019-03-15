---
title: /Gh (povolení funkce háku _penter)
ms.date: 11/04/2016
f1_keywords:
- _penter
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _penter function
- -Gh compiler option [C++]
ms.assetid: 1510a082-8a0e-486e-a309-6add814b494f
ms.openlocfilehash: bf7734a7b81c9550c060d43c2eabf5cb05332407
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820530"
---
# <a name="gh-enable-penter-hook-function"></a>/Gh (povolení funkce háku _penter)

Způsobí, že volání `_penter` funkce na začátku každé metody nebo funkce.

## <a name="syntax"></a>Syntaxe

```
/Gh
```

## <a name="remarks"></a>Poznámky

`_penter` Funkce není součástí žádné knihovny a je na vás poskytnout definici pro `_penter`.

Pokud máte v úmyslu explicitně volat `_penter`, není potřeba poskytovat prototypu. Funkce musí být uvedena jako by měl následující prototyp, a musí distribuce obsahu všem registrů na záznam a vyvolat přes pop beze změny obsahu při ukončení:

```
void __declspec(naked) __cdecl _penter( void );
```

Tato deklarace není k dispozici pro projekty 64-bit.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **příkazového řádku** stránku vlastností.

1. Zadejte možnost do kompilátoru **další možnosti** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="example"></a>Příklad

Následující kód, když kompilujete s **/Gh**, ukazuje, jak `_penter` je volána dvakrát; jednou při vstupu do funkce `main` a jednou při vstupu do funkce `x`.

```cpp
// Gh_compiler_option.cpp
// compile with: /Gh
// processor: x86
#include <stdio.h>
void x() {}

int main() {
   x();
}

extern "C" void __declspec(naked) __cdecl _penter( void ) {
   _asm {
      push eax
      push ebx
      push ecx
      push edx
      push ebp
      push edi
      push esi
    }

   printf_s("\nIn a function!");

   _asm {
      pop esi
      pop edi
      pop ebp
      pop edx
      pop ecx
      pop ebx
      pop eax
      ret
    }
}
```

```Output
In a function!
In a function!
```

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
