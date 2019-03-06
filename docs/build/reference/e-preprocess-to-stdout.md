---
title: /E (předběžné zpracování výstupu stdout)
ms.date: 11/04/2016
f1_keywords:
- /e
helpviewer_keywords:
- -E compiler option [C++]
- /E compiler option [C++]
- preprocessor output, copy to stdout
- preprocessor output
ms.assetid: ddbb1725-d950-4978-ab2f-30a5cd7b778c
ms.openlocfilehash: f0a0d692cd7eaf59aa0c53ecf4436b4c507439a3
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57425481"
---
# <a name="e-preprocess-to-stdout"></a>/E (předběžné zpracování výstupu stdout)

Předzpracuje zdrojové soubory jazyka C a C++ a zkopíruje předzpracovaných souborů do standardního výstupního zařízení.

## <a name="syntax"></a>Syntaxe

```
/E
```

## <a name="remarks"></a>Poznámky

V tomto procesu jsou prováděny všechny direktivy preprocesoru, rozšíření makra se provádí a komentáře se odeberou. Chcete-li zachovat komentáře v Předzpracovaný výstup, použijte [/C (zachovat komentáře při předběžném zpracování)](../../build/reference/c-preserve-comments-during-preprocessing.md) i – možnost kompilátoru.

**/E** přidá `#line` direktivy k výstupu na začátek a konec jednotlivých součástí souborů a kolem řádky odebrat direktivy preprocesoru podmíněné kompilace. Tyto direktivy přečíslování řádky předzpracovaného souboru. Chyby vytvořené během pozdější fáze zpracování v důsledku toho odkazují na čísla řádků původní zdrojový soubor namísto vstupující Předzpracovaný soubor.

**/E** parametr zakazuje kompilaci. Musíte znovu spustit Předzpracovaný soubor pro kompilaci. **/E** výstupní soubory z potlačí i **/FA**, **/Fa**, a **/Fm** možnosti. Další informace najdete v tématu [/FA, /Fa (soubor výpisu)](../../build/reference/fa-fa-listing-file.md) a [/Fm (pojmenování souboru mapování)](../../build/reference/fm-name-mapfile.md).

Chcete-li potlačit `#line` direktivy, použijte [/EP (předběžné zpracování do direktiv bez příkazů #line)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) místo něj parametr.

K odeslání Předzpracovaný výstup do souboru místo položky `stdout`, použijte [/P (předběžné zpracování souboru)](../../build/reference/p-preprocess-to-a-file.md) místo něj parametr.

Chcete-li potlačit `#line` direktivy a odeslat Předzpracovaný výstup do souboru, použijte **/P** a **/EP** společně.

Nelze použít s předkompilovaných hlaviček **/E** možnost.

Všimněte si, že při předzpracování do samostatného souboru, mezery nejsou zaznamenávány po tokeny. K tomu může mít za následek neplatný program nebo mít nežádoucí vedlejší účinky. Následující program zkompiluje úspěšně:

```
#define m(x) x
m(int)main( )
{
   return 0;
}
```

Nicméně pokud kompilujete s:

```
cl -E test.cpp > test2.cpp
```

`int main` test2.cpp nesprávně budou `intmain`.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **příkazového řádku** stránku vlastností.

1. Zadejte možnost do kompilátoru **další možnosti**pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>.

## <a name="example"></a>Příklad

Následující příkaz upraví `ADD.C`, zachová komentáře, přidá `#line` direktivy a zobrazí výsledek do standardního výstupního zařízení:

```
CL /E /C ADD.C
```

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)
