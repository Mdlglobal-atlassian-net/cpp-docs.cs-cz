---
title: / constexpr (kontrolní vyhodnocení constexpr)
ms.date: 08/15/2017
f1_keywords:
- /constexpr
- -constexpr
helpviewer_keywords:
- /constexpr control constexpr evaluation [C++]
- -constexpr control constexpr evaluation [C++]
- constexpr control constexpr evaluation [C++]
ms.assetid: 76d56784-f5ad-401d-841d-09d1059e8b8c
ms.openlocfilehash: 178acc548fb9c89dcfde104d2a12d85637440e28
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810182"
---
# <a name="constexpr-control-constexpr-evaluation"></a>/ constexpr (kontrolní vyhodnocení constexpr)

Použití **/constexpr** – možnosti kompilátoru pro ovládací prvek parametry pro **constexpr** vyhodnocení za kompilace.

## <a name="syntax"></a>Syntaxe

> **/constexpr:depth**<em>N</em>
>  **/constexpr:backtrace**<em>N</em>
>  **/constexpr:steps**<em>N</em>

## <a name="arguments"></a>Arguments

**Hloubka**<em>N</em> omezení hloubky rekurzivní **constexpr** volání do funkce *N* úrovně. Výchozí hodnota je 512.

**backtrace**<em>N</em> zobrazit až *N* **constexpr** hodnocení v diagnostice. Výchozí hodnota je 10.

**kroky**<em>N</em> Terminate **constexpr** zkušební verzi po *N* kroky. Výchozí hodnota je 100 000.

## <a name="remarks"></a>Poznámky

**/Constexpr** – možnosti kompilátoru řídí vyhodnocení za kompilace **constexpr** výrazy. Vyhodnocení kroků, rekurze úrovně a hloubka backtrace jsou řízeny pro zabránění kompilátoru útraty uběhla spousta času na **constexpr** hodnocení. Další informace o **constexpr** prvek jazyka naleznete v tématu [constexpr (C++)](../../cpp/constexpr-cpp.md).

**/Constexpr** možnosti jsou k dispozici od verze Visual Studio 2015.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete svůj projekt **stránky vlastností** dialogové okno.

2. V části **vlastnosti konfigurace**, rozbalte **C/C++** složky a vyberte **příkazového řádku** stránku vlastností.

3. Zadejte libovolné **/constexpr** možnosti kompilátoru **další možnosti** pole. Zvolte **OK** nebo **použít** uložte provedené změny.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
