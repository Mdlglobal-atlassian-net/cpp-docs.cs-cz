---
title: /P (předběžné zpracování souboru)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.GeneratePreprocessedFile
- /p
- VC.Project.VCCLWCECompilerTool.GeneratePreprocessedFile
helpviewer_keywords:
- /P compiler option [C++]
- -P compiler option [C++]
- P compiler option [C++]
- output files, preprocessor
- preprocessing output files
ms.assetid: 123ee54f-8219-4a6f-9876-4227023d83fc
ms.openlocfilehash: 5e6302d90647bce7e37c47a619e814cab300aaee
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813757"
---
# <a name="p-preprocess-to-a-file"></a>/P (předběžné zpracování souboru)

Předzpracuje zdrojové soubory jazyka C a C++ a zapíše Předzpracovaný výstup do souboru.

## <a name="syntax"></a>Syntaxe

```
/P
```

## <a name="remarks"></a>Poznámky

Soubor má stejný základní název jako zdrojový soubor a .i rozšíření. V procesu jsou prováděny všechny direktivy preprocesoru, rozšíření makra se provádí a komentáře se odeberou. Chcete-li zachovat komentáře v Předzpracovaný výstup, použijte [/C (zachovat komentáře při předběžném zpracování)](c-preserve-comments-during-preprocessing.md) možnost spolu s **/P**.

**/P** přidá `#line` direktivy do výstupu, na začátek a konec jednotlivých součástí souborů a kolem řádky odebrat direktivy preprocesoru podmíněné kompilace. Tyto direktivy přečíslování řádky předzpracovaného souboru. Chyby vytvořené během pozdější fáze zpracování v důsledku toho odkazují na čísla řádků původní zdrojový soubor namísto vstupující Předzpracovaný soubor. Chcete-li potlačit generování `#line` použít direktivy, [/EP (předběžné zpracování do direktiv bez příkazů #line)](ep-preprocess-to-stdout-without-hash-line-directives.md) stejně jako **/P**.

**/P** parametr zakazuje kompilaci. Nevytvoří soubor obj., i když používáte [/Fo (název souboru objektů)](fo-object-file-name.md). Musíte znovu spustit Předzpracovaný soubor pro kompilaci. **/P** výstupní soubory z potlačí i **/FA**, **/Fa**, a **/Fm** možnosti. Další informace najdete v tématu [/FA, /Fa (soubor výpisu)](fa-fa-listing-file.md) a [/Fm (pojmenování souboru mapování)](fm-name-mapfile.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **preprocesor** stránku vlastností.

1. Upravit **generovat Předzpracovaný soubor** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>.

## <a name="example"></a>Příklad

Následující příkaz upraví `ADD.C`, zachová komentáře, přidá `#line` direktivy a zapíše výsledek do souboru, `ADD.I`:

```
CL /P /C ADD.C
```

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[/Fi (předzpracování názvu výstupního souboru)](fi-preprocess-output-file-name.md)
