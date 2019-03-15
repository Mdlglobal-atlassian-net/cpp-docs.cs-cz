---
title: /Oi (Generovat vnitřní funkce)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableIntrinsicFunctions
- /oi
- VC.Project.VCCLWCECompilerTool.EnableIntrinsicFunctions
helpviewer_keywords:
- Oi compiler option [C++]
- intrinsic functions, generate
- /Oi compiler option [C++]
- -Oi compiler option [C++]
- generate intrinsic functions compiler option [C++]
ms.assetid: fa4a3bf6-0ed8-481b-91c0-add7636132b4
ms.openlocfilehash: f3afedade6f99129c21069e5117daa4ceb616cc2
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57811885"
---
# <a name="oi-generate-intrinsic-functions"></a>/Oi (Generovat vnitřní funkce)

Některé funkce se volá s formuláři vnitřní nebo jinak speciální funkce, které vaší aplikaci pomůžou se nahradí rychleji.

## <a name="syntax"></a>Syntaxe

```
/Oi[-]
```

## <a name="remarks"></a>Poznámky

Programy používající vnitřní funkce jsou rychlejší, protože nemají režii volání funkcí, ale může být větší kvůli další kód vytvořený.

Zobrazit [vnitřní](../../preprocessor/intrinsic.md) Další informace, na kterém funkce mají vnitřní formy.

**/OI** je pouze požadavek na kompilátor vnitřních objektů, nahraďte volání některých funkcí kompilátoru může volat funkci (a není nahraďte volání funkce se vnitřní hodnota) Pokud tím bude zvýšen výkon.

**x86 konkrétní**

Vnitřní funkce s plovoucí desetinnou čárkou nejsou provádět žádné zvláštní kontroly vstupních hodnot tak pracovat s omezeným přístupem rozsahy vstupu a mít jinou výjimku zpracování a podmínky hranice než rutiny knihovny se stejným názvem. Použití skutečné vnitřní formy znamená ztráty IEEE zpracování výjimek a ke ztrátě `_matherr` a `errno` funkce; ten znamená ztráty ANSI – shoda. Ale vnitřní formy může výrazně urychlit plovoucí desetinnou náročné programy a pro mnoho aplikací, problémech přizpůsobení jsou malé praktickým přínosem.

Můžete použít [Za](za-ze-disable-language-extensions.md) přepsat generování možností skutečně vnitřních plovoucích – možnost kompilátoru. V tomto případě jsou funkce generovány jako rutiny knihoven, které předávají argumenty přímo do čipu plovoucí desetinné čárky namísto jejich ukládání do zásobníku programu.

**END x86 konkrétní**

Můžete také použít [vnitřní](../../preprocessor/intrinsic.md) vytvořit vnitřní funkce nebo [– funkce (C/C++)](../../preprocessor/function-c-cpp.md) k vynucení explicitního volání funkce.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **optimalizace** stránku vlastností.

1. Upravit **povolit vnitřní funkce** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableIntrinsicFunctions%2A>.

## <a name="see-also"></a>Viz také:

[/O – možnosti (optimalizace kódu)](o-options-optimize-code.md)<br/>
[Možnosti kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[Vnitřní funkce kompilátoru](../../intrinsics/compiler-intrinsics.md)
