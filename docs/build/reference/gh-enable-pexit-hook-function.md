---
title: /GH (Povolit funkce háku _pexit)
ms.date: 11/04/2016
f1_keywords:
- _pexit
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _pexit function
- -Gh compiler option [C++]
ms.assetid: 93181453-2676-42e5-bf63-3b19e07299b6
ms.openlocfilehash: 5382ba90f490aaa12e9e55767fdf15170a69ced5
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749237"
---
# <a name="gh-enable-_pexit-hook-function"></a>/GH (Povolit funkce háku _pexit)

Volá `_pexit` funkci na konci každé metody nebo funkce.

## <a name="syntax"></a>Syntaxe

```
/GH
```

## <a name="remarks"></a>Poznámky

Funkce `_pexit` není součástí žádné knihovny a je na vás, `_pexit`abyste pro něj zadali definici .

Pokud nemáte v `_pexit`úmyslu explicitně volat , není nutné zadat prototyp. Funkce musí vypadat, jako by měla následující prototyp, a musí při vstupu tlačit obsah všech registrů a při výstupu vysuňovat nezměněný obsah:

```cpp
void __declspec(naked) __cdecl _pexit( void );
```

`_pexit`je podobná `_penter`; viz [/Gh (Povolit _penter funkce hook)](gh-enable-penter-hook-function.md) pro `_pexit` příklad, jak napsat funkci.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **Stránky vlastností** projektu. Podrobnosti naleznete v [tématu Nastavení kompilátoru jazyka C++ a vlastnosti sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na složku **C/C++.**

1. Klepněte na stránku vlastností **příkazového řádku.**

1. Do pole **Další možnosti** zadejte možnost kompilátoru.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
