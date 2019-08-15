---
title: /Execution-charset (nastavení znakové sady spuštění)
ms.date: 02/06/2019
f1_keywords:
- execution-charset
- /execution-charset
helpviewer_keywords:
- /execution-charset compiler option
- -execution-charset compiler option
ms.assetid: 0e02f487-2236-45bc-95f3-5760933a8f96
ms.openlocfilehash: 44e83524867bc8a914706e1f5b45b61bc4a48087
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492919"
---
# <a name="execution-charset-set-execution-character-set"></a>/Execution-charset (nastavení znakové sady spuštění)

Umožňuje zadat znakovou sadu spouštění pro spustitelný soubor.

## <a name="syntax"></a>Syntaxe

```
/execution-charset:[IANA_name|.CPID]
```

## <a name="arguments"></a>Arguments

*IANA_name*<br/>
Název znakové sady definovaný organizací IANA.

*CPID*<br/>
Identifikátor kódové stránky

## <a name="remarks"></a>Poznámky

K určení znakové sady pro spuštění můžete použít možnost **/Execution-charset** . Znaková sada spuštění je kódování použité pro text programu, který je vstupem do fáze kompilace po všech krocích předběžného zpracování. Tato znaková sada se používá pro interní reprezentace libovolných řetězcových nebo znakových literálů v kompilovaném kódu. Tuto možnost nastavte, pokud chcete zadat znakovou sadu rozšířeného spuštění, která se má použít, když zdrojové soubory obsahují znaky, které nejsou reprezentovány v základní znakové sadě spuštění. Můžete použít název sady znaků IANA nebo ISO nebo tečku (.) následovaný znakem 3 až 5 číslice pro desítkový identifikátor znakové stránky a zadat znakovou sadu, která se má použít. Seznam podporovaných identifikátorů znakové stránky a názvů znakové sady naleznete v tématu [identifikátory znakové stránky](/windows/win32/Intl/code-page-identifiers).

Ve výchozím nastavení Visual Studio detekuje značku pro určení, zda je zdrojový soubor v kódovaném formátu Unicode, například UTF-16 nebo UTF-8. Pokud není nalezen žádný znak pořadí bajtů, předpokládá se, že zdrojový soubor je kódován pomocí uživatelské znakové stránky, pokud jste nezadali název znakové sady nebo znakovou stránku pomocí možnosti **/source-charset** nebo možnosti **/UTF-8.** . Visual Studio umožňuje uložit C++ zdrojový kód pomocí některého z několika kódování znaků. Informace o zdrojových a spouštěcích znakových sadách naleznete v tématu [znakové sady](../../cpp/character-sets.md) v dokumentaci jazyka.

Pokud chcete nastavit jak zdrojové znakové sady, tak i znaková sada spuštění na UTF-8, můžete použít možnost kompilátoru **/UTF-8.** jako zástupce. Je ekvivalentní zadání **/source-charset: UTF-8/Execution-charset: UTF-8** na příkazovém řádku. Kterákoli z těchto možností také ve výchozím nastavení povolí možnost **/Validate-charset** .

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Další informace najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Rozbalte **Vlastnosti konfigurace**, složka s příkazovým **řádkem** **C/C++** .

1. V části **Další možnosti**přidejte možnost **/Execution-charset** a zadejte preferované kódování.

1. Kliknutím na **tlačítko OK** uložte změny.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[/source-charset (nastavení zdrojové znakové sady)](source-charset-set-source-character-set.md)<br/>
[/utf-8 (nastavení zdrojové znakové sady a spustitelné znakové sady na UTF-8)](utf-8-set-source-and-executable-character-sets-to-utf-8.md)<br/>
[/validate-charset (ověření kompatibilních znaků)](validate-charset-validate-for-compatible-characters.md)
