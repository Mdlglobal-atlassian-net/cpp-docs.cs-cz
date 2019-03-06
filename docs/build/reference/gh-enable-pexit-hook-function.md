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
ms.openlocfilehash: 21649838ba81f3affdda3f3833de23e4d9e33746
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422526"
---
# <a name="gh-enable-pexit-hook-function"></a>/GH (Povolit funkce háku _pexit)

Volání `_pexit` funkce na konci každé metody nebo funkce.

## <a name="syntax"></a>Syntaxe

```
/GH
```

## <a name="remarks"></a>Poznámky

`_pexit` Funkce není součástí žádné knihovny a je na vás poskytnout definici pro `_pexit`.

Pokud máte v úmyslu explicitně volat `_pexit`, není potřeba poskytovat prototypu. Funkce musí být uvedena jako by měl následující prototyp, a musí distribuce obsahu všem registrů na záznam a vyvolat přes pop beze změny obsahu při ukončení:

```
void __declspec(naked) __cdecl _pexit( void );
```

`_pexit` je podobný `_penter`; naleznete v tématu [/Gh (povolení _penter funkce háku)](../../build/reference/gh-enable-penter-hook-function.md) příklad toho, jak zapisovat `_pexit` funkce.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **příkazového řádku** stránku vlastností.

1. Zadejte možnost do kompilátoru **další možnosti** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)
