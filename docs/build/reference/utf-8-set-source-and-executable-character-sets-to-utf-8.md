---
title: /UTF-8. (nastavení zdrojových a spustitelných znakových UTF-8sad na)
ms.date: 04/26/2020
f1_keywords:
- /utf-8
helpviewer_keywords:
- /utf-8 compiler option
ms.assetid: f0e1f3cb-6cae-46eb-9483-04ed13d9b504
no-loc:
- UTF
- UTF-8
- UTF-16
ms.openlocfilehash: c98a30b0ec4b36b8bd87fb0956d9382751975cfd
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168862"
---
# <a name="utf-8-set-source-and-executable-character-sets-to-opno-locutf-8"></a>`/utf-8`(Nastavení zdrojových a spustitelných znakových UTF-8sad na)

Určuje zdrojovou znakovou sadu a znakovou sadu spuštění jako UTF-8.

## <a name="syntax"></a>Syntaxe

> **`/utf-8`**

## <a name="remarks"></a>Poznámky

Můžete použít **`/utf-8`** možnost k určení zdrojových i spouštěcích znakových sad jako kódovaných pomocí UTF-8. Je ekvivalentní se zadáním **`/source-charset:utf-8 /execution-charset:utf-8`** na příkazovém řádku. Kterákoli z těchto možností taky ve výchozím **`/validate-charset`** nastavení povoluje možnost. Seznam podporovaných identifikátorů znakové stránky a názvů znakové sady naleznete v tématu [identifikátory znakové stránky](/windows/win32/Intl/code-page-identifiers).

Ve výchozím nastavení Visual Studio detekuje značku pro určení, zda je zdrojový soubor v kódovaném formátu Unicode, například UTF-16 nebo. UTF-8 Pokud není nalezen žádný znak pořadí bajtů, předpokládá se, že zdrojový soubor je kódován pomocí uživatelské znakové stránky, pokud jste nezadali znakovou stránku pomocí **`/utf-8`** **`/source-charset`** příkazu nebo. Visual Studio umožňuje uložit zdrojový kód v jazyce C++ pomocí kteréhokoli z několika kódování znaků. Informace o zdrojových a spouštěcích znakových sadách naleznete v tématu [znakové sady](../../cpp/character-sets.md) v dokumentaci jazyka.

## <a name="set-the-option-in-visual-studio-or-programmatically"></a>Nastavte možnost v sadě Visual Studio nebo programově

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Další informace najdete v tématu [nastavení kompilátoru C++ a vlastností sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte stránku vlastností **Konfigurace** > **příkazového řádku** **C/C++** > .

1. V části **Další možnosti**přidejte **`/utf-8`** možnost pro určení upřednostňovaného kódování.

1. Kliknutím na **tlačítko OK** uložte změny.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[/Execution-charset (nastavení znakové sady spuštění)](execution-charset-set-execution-character-set.md)<br/>
[/source-charset (nastavení zdrojové znakové sady)](source-charset-set-source-character-set.md)<br/>
[/validate-charset (ověření kompatibilních znaků)](validate-charset-validate-for-compatible-characters.md)
