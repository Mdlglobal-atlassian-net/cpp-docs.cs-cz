---
title: '/EP (předběžné zpracování do direktiv bez příkazů #line)'
ms.date: 11/04/2016
f1_keywords:
- /ep
- VC.Project.VCCLCompilerTool.GeneratePreprocessedFileNoLines
helpviewer_keywords:
- copy preprocessor output to stdout
- preprocessor output, copy to stdout
- -EP compiler option [C++]
- EP compiler option [C++]
- /EP compiler option [C++]
ms.assetid: 6ec411ae-e33d-4ef5-956e-0054635eabea
ms.openlocfilehash: 49745b644234c0e5ce92661f14304531aaca5c69
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293248"
---
# <a name="ep-preprocess-to-stdout-without-line-directives"></a>/EP (předběžné zpracování do direktiv bez příkazů #line)

Předzpracuje zdrojové soubory jazyka C a C++ a zkopíruje předzpracovaných souborů do standardního výstupního zařízení.

## <a name="syntax"></a>Syntaxe

```
/EP
```

## <a name="remarks"></a>Poznámky

V procesu jsou prováděny všechny direktivy preprocesoru, rozšíření makra se provádí a komentáře se odeberou. Chcete-li zachovat komentáře v Předzpracovaný výstup, použijte [/C (zachovat komentáře při předběžném zpracování)](c-preserve-comments-during-preprocessing.md) spolu s možností **/EP**.

**/EP** parametr zakazuje kompilaci. Musíte znovu spustit Předzpracovaný soubor pro kompilaci. **/EP** výstupní soubory z potlačí i **/FA**, **/Fa**, a **/Fm** možnosti. Další informace najdete v tématu [/FA, /Fa (soubor výpisu)](fa-fa-listing-file.md) a [/Fm (pojmenování souboru mapování)](fm-name-mapfile.md).

Chyby vytvořené během pozdější fáze zpracování odkazují na čísla řádků z předzpracovaného souboru, nikoli původní zdrojový soubor. Pokud chcete, aby čísla řádků k odkazování na původní zdrojový soubor, použijte [/E (předběžné zpracování výstupu stdout)](e-preprocess-to-stdout.md) místo. **/E** přidává možnost `#line` direktivy do výstupu pro tento účel.

K odeslání Předzpracovaný výstup s `#line` direktivy, chcete-li soubor, použijte [/P (předběžné zpracování souboru)](p-preprocess-to-a-file.md) místo něj parametr.

Odeslat Předzpracovaný výstup do stdout, spolu s `#line` použít direktivy, **/P** a **/EP** společně.

Nelze použít s předkompilovaných hlaviček **/EP** možnost.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **preprocesor** stránku vlastností.

1. Upravit **generovat Předzpracovaný soubor** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>.

## <a name="example"></a>Příklad

Následující příkaz upraví soubor `ADD.C`, zachová komentáře a zobrazí výsledek do standardního výstupního zařízení:

```
CL /EP /C ADD.C
```

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
