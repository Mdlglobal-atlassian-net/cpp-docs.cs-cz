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
ms.openlocfilehash: 9b3d84d94ed75acd68011b895afbc4f190019673
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622228"
---
# <a name="p-preprocess-to-a-file"></a>/P (předběžné zpracování souboru)

Předzpracuje zdrojové soubory jazyka C a C++ a zapíše Předzpracovaný výstup do souboru.

## <a name="syntax"></a>Syntaxe

```
/P
```

## <a name="remarks"></a>Poznámky

Soubor má stejný základní název jako zdrojový soubor a .i rozšíření. V procesu jsou prováděny všechny direktivy preprocesoru, rozšíření makra se provádí a komentáře se odeberou. Chcete-li zachovat komentáře v Předzpracovaný výstup, použijte [/C (zachovat komentáře při předběžném zpracování)](../../build/reference/c-preserve-comments-during-preprocessing.md) možnost spolu s **/P**.

**/P** přidá `#line` direktivy do výstupu, na začátek a konec jednotlivých součástí souborů a kolem řádky odebrat direktivy preprocesoru podmíněné kompilace. Tyto direktivy přečíslování řádky předzpracovaného souboru. Chyby vytvořené během pozdější fáze zpracování v důsledku toho odkazují na čísla řádků původní zdrojový soubor namísto vstupující Předzpracovaný soubor. Chcete-li potlačit generování `#line` použít direktivy, [/EP (předběžné zpracování do direktiv bez příkazů #line)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) stejně jako **/P**.

**/P** parametr zakazuje kompilaci. Nevytvoří soubor obj., i když používáte [/Fo (název souboru objektů)](../../build/reference/fo-object-file-name.md). Musíte znovu spustit Předzpracovaný soubor pro kompilaci. **/P** výstupní soubory z potlačí i **/FA**, **/Fa**, a **/Fm** možnosti. Další informace najdete v tématu [/FA, /Fa (soubor výpisu)](../../build/reference/fa-fa-listing-file.md) a [/Fm (pojmenování souboru mapování)](../../build/reference/fm-name-mapfile.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

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

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)<br/>
[/Fi (předzpracování názvu výstupního souboru)](../../build/reference/fi-preprocess-output-file-name.md)