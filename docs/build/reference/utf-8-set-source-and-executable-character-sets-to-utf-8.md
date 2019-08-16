---
title: /UTF-8. (nastavení zdrojových a spustitelných znakových sad na UTF-8)
ms.date: 11/04/2016
f1_keywords:
- /utf-8
helpviewer_keywords:
- /utf-8 compiler option
ms.assetid: f0e1f3cb-6cae-46eb-9483-04ed13d9b504
ms.openlocfilehash: 1ff0f23ad0758642c73b1b35d6d4dd1be20899cb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498183"
---
# <a name="utf-8-set-source-and-executable-character-sets-to-utf-8"></a>/UTF-8. (nastavení zdrojových a spustitelných znakových sad na UTF-8)

Určuje zdrojovou znakovou sadu a znakovou sadu spuštění jako UTF-8.

## <a name="syntax"></a>Syntaxe

```
/utf-8
```

## <a name="remarks"></a>Poznámky

Pomocí možnosti **/UTF-8.** můžete určit zdrojové i spouštěcí znakové sady jako kódované pomocí kódování UTF-8. Je ekvivalentní zadání **/source-charset: UTF-8/Execution-charset: UTF-8** na příkazovém řádku. Kterákoli z těchto možností také ve výchozím nastavení povolí možnost **/Validate-charset** . Seznam podporovaných identifikátorů znakové stránky a názvů znakové sady naleznete v tématu [identifikátory znakové stránky](/windows/win32/Intl/code-page-identifiers).

Ve výchozím nastavení Visual Studio detekuje značku pro určení, zda je zdrojový soubor v kódovaném formátu Unicode, například UTF-16 nebo UTF-8. Pokud není nalezen žádný znak pořadí bajtů, předpokládá se, že zdrojový soubor je kódován pomocí uživatelské znakové stránky, pokud jste nezadali znakovou stránku pomocí **/UTF-8.** nebo možnosti **/source-charset** . Visual Studio umožňuje uložit C++ zdrojový kód pomocí některého z několika kódování znaků. Informace o zdrojových a spouštěcích znakových sadách naleznete v tématu [znakové sady](../../cpp/character-sets.md) v dokumentaci jazyka.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Další informace najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Rozbalte **Vlastnosti konfigurace**, složka s příkazovým **řádkem** **C/C++** .

1. V části **Další možnosti**přidejte možnost **/UTF-8.** pro určení upřednostňovaného kódování.

1. Kliknutím na **tlačítko OK** uložte změny.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[/Execution-charset (nastavení znakové sady spuštění)](execution-charset-set-execution-character-set.md)<br/>
[/source-charset (nastavení zdrojové znakové sady)](source-charset-set-source-character-set.md)<br/>
[/validate-charset (ověření kompatibilních znaků)](validate-charset-validate-for-compatible-characters.md)
