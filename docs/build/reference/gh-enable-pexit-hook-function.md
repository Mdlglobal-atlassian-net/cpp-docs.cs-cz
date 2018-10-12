---
title: -GH (povolení funkce háku _pexit) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _pexit
dev_langs:
- C++
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _pexit function
- -Gh compiler option [C++]
ms.assetid: 93181453-2676-42e5-bf63-3b19e07299b6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9b8ee4c80310c4d94ed432d48ee9702c41f80bf
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49161785"
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

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)