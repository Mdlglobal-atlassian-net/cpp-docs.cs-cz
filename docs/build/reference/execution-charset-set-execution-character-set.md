---
title: / Execution-Charset (nastavení znakové sady spuštění)
ms.date: 02/06/2019
f1_keywords:
- execution-charset
- /execution-charset
helpviewer_keywords:
- /execution-charset compiler option
- -execution-charset compiler option
ms.assetid: 0e02f487-2236-45bc-95f3-5760933a8f96
ms.openlocfilehash: 0a140bf438a44df152b1578f4569a087a604061c
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807712"
---
# <a name="execution-charset-set-execution-character-set"></a>/ Execution-Charset (nastavení znakové sady spuštění)

Umožňuje určit spuštění znakové sady pro spustitelný soubor.

## <a name="syntax"></a>Syntaxe

```
/execution-charset:[IANA_name|.CPID]
```

## <a name="arguments"></a>Arguments

*IANA_name*<br/>
Název sady znaků definice IANA.

*CPID*<br/>
Identifikátor kódu stránky.

## <a name="remarks"></a>Poznámky

Můžete použít **/Execution-Charset** můžete zadat znaková sada spuštění. Znaková sada spuštění je kódování použité pro text ovládacího prvku programu, který je vstup do fáze kompilace koneckonců předběžného zpracování kroky. Znaková sada se používá pro interní reprezentace libovolný řetězec nebo znak literály do kompilovaného kódu. Nastavte tuto možnost k určení znakové sady rozšířeného spuštění při vaší zdrojové soubory obsahují znaky, které nejsou reprezentovat základní znakové sadě spuštění. Můžete použít buď IANA nebo ISO znaková sada název nebo tečku (.), za nímž následuje identifikátor číslice 3 až 5 desítkový kód stránky zadat znakovou sadu. Seznam podporovaných identifikátory znakových stránek a znakové sady názvy, naleznete v tématu [identifikátory znakových stránek](/windows/desktop/Intl/code-page-identifiers).

Ve výchozím nastavení sada Visual Studio zjistí značka pořadí bajtů k určení, zda zdrojový soubor je v zakódovaném formátu Unicode, například UTF-16 nebo UTF-8. Pokud se nenajde žádné značky pořadí bajtů, předpokládá zdrojový soubor je zakódován pomocí aktuální znakové stránce uživatele uvedeno znaková sada s použitím názvu nebo kódu stránky **/Source-Charset** možnost nebo **/UTF-8** možnost. Visual Studio umožňuje uložit zdrojovém kódu jazyka C++ pomocí některého z několika kódování znaků. Informace o spuštění a zdrojová znakových sadách najdete v tématu [znakové sady](../../cpp/character-sets.md) v dokumentaci jazyka.

Pokud chcete nastavit zdrojové znakové sady a znakové sady spuštění na UTF-8, můžete použít **/UTF-8** – možnost kompilátoru jako zástupce. Je ekvivalentní se zadáním **/source-charset:utf – 8 /execution-charset:utf – 8** na příkazovém řádku. Některé z těchto možností také umožňuje **/Validate-Charset** možnost ve výchozím nastavení.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Rozbalte **vlastnosti konfigurace**, **C/C++**, **příkazového řádku** složky.

1. V **další možnosti**, přidejte **/Execution-Charset** možnosti a určete upřednostňované kódování.

1. Zvolte **OK** uložte provedené změny.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[/source-charset (nastavení zdrojové znakové sady)](source-charset-set-source-character-set.md)<br/>
[/utf-8 (nastavení zdrojové znakové sady a spustitelné znakové sady na UTF-8)](utf-8-set-source-and-executable-character-sets-to-utf-8.md)<br/>
[/validate-charset (ověření kompatibilních znaků)](validate-charset-validate-for-compatible-characters.md)
