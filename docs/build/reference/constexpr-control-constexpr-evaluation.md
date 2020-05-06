---
title: /constexpr (kontrolní vyhodnocení constexpr)
ms.date: 08/15/2017
f1_keywords:
- /constexpr
- -constexpr
helpviewer_keywords:
- /constexpr control constexpr evaluation [C++]
- -constexpr control constexpr evaluation [C++]
- constexpr control constexpr evaluation [C++]
ms.assetid: 76d56784-f5ad-401d-841d-09d1059e8b8c
ms.openlocfilehash: 4d3f33a64dcebfc40778f81354cb5067a5239ace
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825588"
---
# <a name="constexpr-control-constexpr-evaluation"></a>/constexpr (kontrolní vyhodnocení constexpr)

Použijte možnosti kompilátoru **/constexpr** k řízení parametrů pro vyhodnocení **constexpr** v době kompilace.

## <a name="syntax"></a>Syntaxe

> **/constexpr: Hloubka**<em>N</em>\
> **/constexpr: zpětné trasování**<em>N</em>\
> **/constexpr: kroky**<em>N</em>

## <a name="arguments"></a>Argumenty

**Hloubka**<em>N</em> omezí hloubku rekurzivního volání funkce **constexpr** na *N* úrovní. Výchozí hodnota je 512.

**zpětné trasování**<em>N</em> zobrazuje až *n* vyhodnocení **constexpr** v diagnostice. Výchozí hodnota je 10.

**kroky**<em>n</em> ukončí vyhodnocení **constexpr** po *N* krocích. Výchozí hodnota je 100 000.

## <a name="remarks"></a>Poznámky

Možnosti kompilátoru **/constexpr** řídí vyhodnocení výrazů **constexpr** při kompilaci. Postup vyhodnocení, úrovně rekurze a hloubka zpětného trasování jsou řízeny, aby nedocházelo k tomu, že kompilátor nebude příliš velký čas při vyhodnocování **constexpr** . Další informace o elementu jazyka **constexpr** naleznete v tématu [constexpr (C++)](../../cpp/constexpr-cpp.md).

Možnosti **/constexpr** jsou k dispozici od začátku v aplikaci Visual Studio 2015.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu.

2. V části **Vlastnosti konfigurace**rozbalte složku **C/C++** a vyberte stránku vlastností **příkazový řádek** .

3. V poli **Další možnosti** zadejte všechny možnosti kompilátoru **/constexpr** . Změny uložte kliknutím na **OK** nebo **použít** .

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
