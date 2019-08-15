---
title: /Source-charset (nastavení zdrojové znakové sady)
ms.date: 02/06/2019
f1_keywords:
- source-charset
- /source-charset
helpviewer_keywords:
- /execution-charset compiler option
ms.assetid: d3c5bf7f-526d-4ee4-acc5-c1a02a4fc481
ms.openlocfilehash: cd3e4eb3fd305ba6bdd298d18b1edb80f2b98343
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498260"
---
# <a name="source-charset-set-source-character-set"></a>/Source-charset (nastavení zdrojové znakové sady)

Umožňuje zadat zdrojovou znakovou sadu pro spustitelný soubor.

## <a name="syntax"></a>Syntaxe

```
/source-charset:[IANA_name|.CPID]
```

## <a name="arguments"></a>Arguments

**IANA_name**<br/>
Název znakové sady definovaný organizací IANA.

**CPID**<br/>
Identifikátor kódové stránky jako desetinné číslo.

## <a name="remarks"></a>Poznámky

Můžete použít možnost **/source-charset** k určení rozšířené zdrojové znakové sady, která se má použít, když zdrojové soubory obsahují znaky, které nejsou reprezentovány v základní zdrojové znakové sadě. Zdrojová znaková sada je kódování použité k interpretaci zdrojového textu programu do interní reprezentace používané jako vstup do fáze předzpracování před kompilací. Vnitřní reprezentace je pak převedena na znakovou sadu spuštění pro uložení hodnot řetězce a znaků ve spustitelném souboru. Můžete použít název sady znaků IANA nebo ISO nebo tečku (.) následovaný znakem 3 až 5 číslice pro desítkový identifikátor znakové stránky a zadat znakovou sadu, která se má použít. Seznam podporovaných identifikátorů znakové stránky a názvů znakové sady naleznete v tématu [identifikátory znakové stránky](/windows/win32/Intl/code-page-identifiers).

Ve výchozím nastavení Visual Studio detekuje značku pro určení, zda je zdrojový soubor v kódovaném formátu Unicode, například UTF-16 nebo UTF-8. Pokud není nalezen žádný znak pořadí bajtů, předpokládá se, že zdrojový soubor je kódován pomocí uživatelské znakové stránky, pokud nezadáte název znakové sady nebo znakovou stránku pomocí možnosti **/source-charset** . Visual Studio umožňuje uložit C++ zdrojový kód pomocí některého z několika kódování znaků. Další informace o zdrojových a spouštěcích znakových sadách naleznete v tématu [znakové sady](../../cpp/character-sets.md) v dokumentaci jazyka.

Zdrojová znaková sada, kterou zadáte, musí namapovat 7 bitů znaků ASCII na stejné body kódu v sadě znaků nebo může docházet k mnoha chybám kompilace. Vaše Zdrojová znaková sada musí být také namapovat na rozšířenou znakovou sadu Unicode encodable pomocí UTF-8. Znaky, které nejsou encodable v kódování UTF-8, jsou reprezentovány náhradou specifickou pro konkrétní implementaci. Kompilátor společnosti Microsoft používá pro tyto znaky otazník.

Pokud chcete nastavit jak zdrojové znakové sady, tak i znaková sada spuštění na UTF-8, můžete použít možnost kompilátoru **/UTF-8.** jako zástupce. Je ekvivalentní zadání **/source-charset: UTF-8/Execution-charset: UTF-8** na příkazovém řádku. Kterákoli z těchto možností také ve výchozím nastavení povolí možnost **/Validate-charset** .

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Další informace najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Rozbalte **Vlastnosti konfigurace**, složka s příkazovým **řádkem** **C/C++** .

1. V části **Další možnosti**přidejte možnost **/source-charset** a zadejte preferované kódování.

1. Kliknutím na **tlačítko OK** uložte změny.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[/Execution-charset (nastavení znakové sady spuštění)](execution-charset-set-execution-character-set.md)<br/>
[/utf-8 (nastavení zdrojové znakové sady a spustitelné znakové sady na UTF-8)](utf-8-set-source-and-executable-character-sets-to-utf-8.md)<br/>
[/validate-charset (ověření kompatibilních znaků)](validate-charset-validate-for-compatible-characters.md)
