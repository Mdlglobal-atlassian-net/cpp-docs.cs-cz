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
ms.openlocfilehash: 87815b5f0e0450b84acbe3c35b7ef4f31216ec72
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749289"
---
# <a name="gh-enable-_penter-hook-function"></a>/Gh (povolení funkce háku _penter)

Způsobí volání funkce `_penter` na začátku každé metody nebo funkce.

## <a name="syntax"></a>Syntaxe

```
/Gh
```

## <a name="remarks"></a>Poznámky

Funkce `_penter` není součástí žádné knihovny a je na vás, `_penter`abyste pro něj zadali definici .

Pokud nemáte v `_penter`úmyslu explicitně volat , není nutné zadat prototyp. Funkce musí vypadat, jako by měla následující prototyp, a musí při vstupu tlačit obsah všech registrů a při výstupu vysuňovat nezměněný obsah:

```cpp
void __declspec(naked) __cdecl _penter( void );
```

Tato deklarace není k dispozici pro 64bitové projekty.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **Stránky vlastností** projektu. Podrobnosti naleznete v [tématu Nastavení kompilátoru jazyka C++ a vlastnosti sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na složku **C/C++.**

1. Klepněte na stránku vlastností **příkazového řádku.**

1. Do pole **Další možnosti** zadejte možnost kompilátoru.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="example"></a>Příklad

Následující kód, při kompilaci s **/Gh**, ukazuje, jak `_penter` se nazývá dvakrát; jednou při `main` zadávání funkce a `x`jednou při zadávání funkce .

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

## <a name="see-also"></a>Viz také

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
