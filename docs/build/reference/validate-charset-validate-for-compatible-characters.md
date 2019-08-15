---
title: /validate-charset (ověření kompatibilních znaků)
ms.date: 02/06/2019
f1_keywords:
- /validate-charset
- validate-charset
helpviewer_keywords:
- /validate-charset compiler option
ms.assetid: 50360fd0-4d32-4a4f-95d0-53d38c12ad4c
ms.openlocfilehash: 2390aa98b9416eb538f529c8c370c888cccf4734
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498161"
---
# <a name="validate-charset-validate-for-compatible-characters"></a>/validate-charset (ověření kompatibilních znaků)

Ověří, zda text zdrojového souboru obsahuje pouze znaky, které lze reprezentovat jako UTF-8.

## <a name="syntax"></a>Syntaxe

```
/validate-charset[-]
```

## <a name="remarks"></a>Poznámky

Pomocí možnosti **/Validate-charset** můžete ověřit, zda zdrojový kód obsahuje pouze znaky, které lze reprezentovat v zdrojové znakové sadě i ve znakové sadě spuštění. Tato kontrolu je povolena automaticky při zadání možností kompilátoru **/source-charset**, **/Execution-charset**nebo **/UTF-8.** . Tuto kontrolu můžete explicitně zakázat zadáním možnosti **/Validate-charset-** .

Ve výchozím nastavení Visual Studio detekuje značku pro určení, zda je zdrojový soubor v kódovaném formátu Unicode, například UTF-16 nebo UTF-8. Pokud není nalezen žádný znak pořadí bajtů, předpokládá se, že zdrojový soubor je kódován pomocí uživatelské znakové stránky, pokud jste nezadali znakovou stránku pomocí **/UTF-8.** nebo možnosti **/source-charset** . Visual Studio umožňuje uložit C++ zdrojový kód pomocí některého z několika kódování znaků. Informace o zdrojových a spouštěcích znakových sadách naleznete v tématu [znakové sady](../../cpp/character-sets.md) v dokumentaci jazyka. Seznam podporovaných identifikátorů znakové stránky a názvů znakové sady naleznete v tématu [identifikátory znakové stránky](/windows/win32/Intl/code-page-identifiers).

Sada Visual Studio používá UTF-8 jako kódování interního znaku během konverze mezi zdrojovou znakovou sadou a znakovou sadou spuštění. Pokud znak ve zdrojovém souboru nemůže být reprezentován ve znakové sadě spuštění, konverze UTF-8 nahradí otazník znakem?. Možnost **/Validate-charset** způsobí, že kompilace ohlásí upozornění, pokud k tomu dojde.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Další informace najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Rozbalte **Vlastnosti konfigurace**, složka s příkazovým **řádkem** **C/C++** .

1. V části **Další možnosti**přidejte možnost **/Validate-charset** a zadejte preferované kódování.

1. Kliknutím na **tlačítko OK** uložte změny.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[/Execution-charset (nastavení znakové sady spuštění)](execution-charset-set-execution-character-set.md)<br/>
[/source-charset (nastavení zdrojové znakové sady)](source-charset-set-source-character-set.md)<br/>
[/utf-8 (nastavení zdrojové znakové sady a spustitelné znakové sady na UTF-8)](utf-8-set-source-and-executable-character-sets-to-utf-8.md)
