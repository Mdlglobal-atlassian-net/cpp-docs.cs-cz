---
title: '-EP (předběžné zpracování do direktiv bez příkazů #line) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ep
- VC.Project.VCCLCompilerTool.GeneratePreprocessedFileNoLines
dev_langs:
- C++
helpviewer_keywords:
- copy preprocessor output to stdout
- preprocessor output, copy to stdout
- -EP compiler option [C++]
- EP compiler option [C++]
- /EP compiler option [C++]
ms.assetid: 6ec411ae-e33d-4ef5-956e-0054635eabea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 598c202cbac0176cb77243c7f0f891ef94c3dcc6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714880"
---
# <a name="ep-preprocess-to-stdout-without-line-directives"></a>/EP (předběžné zpracování do direktiv bez příkazů #line)

Předzpracuje zdrojové soubory jazyka C a C++ a zkopíruje předzpracovaných souborů do standardního výstupního zařízení.

## <a name="syntax"></a>Syntaxe

```
/EP
```

## <a name="remarks"></a>Poznámky

V procesu jsou prováděny všechny direktivy preprocesoru, rozšíření makra se provádí a komentáře se odeberou. Chcete-li zachovat komentáře v Předzpracovaný výstup, použijte [/C (zachovat komentáře při předběžném zpracování)](../../build/reference/c-preserve-comments-during-preprocessing.md) spolu s možností **/EP**.

**/EP** parametr zakazuje kompilaci. Musíte znovu spustit Předzpracovaný soubor pro kompilaci. **/EP** výstupní soubory z potlačí i **/FA**, **/Fa**, a **/Fm** možnosti. Další informace najdete v tématu [/FA, /Fa (soubor výpisu)](../../build/reference/fa-fa-listing-file.md) a [/Fm (pojmenování souboru mapování)](../../build/reference/fm-name-mapfile.md).

Chyby vytvořené během pozdější fáze zpracování odkazují na čísla řádků z předzpracovaného souboru, nikoli původní zdrojový soubor. Pokud chcete, aby čísla řádků k odkazování na původní zdrojový soubor, použijte [/E (předběžné zpracování výstupu stdout)](../../build/reference/e-preprocess-to-stdout.md) místo. **/E** přidává možnost `#line` direktivy do výstupu pro tento účel.

K odeslání Předzpracovaný výstup s `#line` direktivy, chcete-li soubor, použijte [/P (předběžné zpracování souboru)](../../build/reference/p-preprocess-to-a-file.md) místo něj parametr.

Odeslat Předzpracovaný výstup do stdout, spolu s `#line` použít direktivy, **/P** a **/EP** společně.

Nelze použít s předkompilovaných hlaviček **/EP** možnost.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **preprocesor** stránku vlastností.

1. Upravit **generovat Předzpracovaný soubor** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>.

## <a name="example"></a>Příklad

Následující příkaz upraví soubor `ADD.C`, zachová komentáře a zobrazí výsledek do standardního výstupního zařízení:

```
CL /EP /C ADD.C
```

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)