---
title: / Validate-Charset (ověření kompatibilních znaků)
ms.date: 11/04/2016
f1_keywords:
- /validate-charset
- validate-charset
helpviewer_keywords:
- /validate-charset compiler option
ms.assetid: 50360fd0-4d32-4a4f-95d0-53d38c12ad4c
ms.openlocfilehash: 243d225f5acde0c6099050539687726ea082c898
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590486"
---
# <a name="validate-charset-validate-for-compatible-characters"></a>/ Validate-Charset (ověření kompatibilních znaků)

Ověřuje, zda text souboru zdroje obsahuje pouze znaky reprezentovat jako UTF-8.

## <a name="syntax"></a>Syntaxe

```
/validate-charset[-]
```

## <a name="remarks"></a>Poznámky

Můžete použít **/Validate-Charset** možnost ověřit, že zdrojový kód obsahuje jen znaky, které je možné znázornit na zdrojové znakové sady a provedení znakové sady. Tato kontrola se povolí automaticky při zadávání **/Source-Charset**, **/Execution-Charset**, nebo **/UTF-8** – možnosti kompilátoru. Můžete explicitně zakázat tuto kontrolu tak, že zadáte **/ validate-charset –** možnost.

Ve výchozím nastavení sada Visual Studio zjistí značka pořadí bajtů k určení, zda zdrojový soubor je v zakódovaném formátu Unicode, například UTF-16 nebo UTF-8. Pokud se nenajde žádné značky pořadí bajtů, předpokládá zdrojový soubor je zakódován pomocí aktuální znakové stránce uživatele, pokud zadáte znakovou stránku pomocí **/UTF-8** nebo **/Source-Charset** možnost. Visual Studio umožňuje uložit zdrojovém kódu jazyka C++ pomocí některého z několika kódování znaků. Informace o spuštění a zdrojová znakových sadách najdete v tématu [znakové sady](../../cpp/character-sets.md) v dokumentaci jazyka. Seznam podporovaných identifikátory znakových stránek a znakové sady názvy, naleznete v tématu [identifikátory znakových stránek](/windows/desktop/Intl/code-page-identifiers).

Visual Studio používá jako interní kódování znaků, které během převodu mezi zdrojovou znakovou sadou a spouštěcí znaková sada UTF-8. Pokud ve znakové sadě spuštění nelze reprezentovat znaku ve zdrojovém souboru, nahradí převodu znakové sady UTF-8 otazník '?' znaků. **/Validate-Charset** možnost způsobí, že kompilace hlásit upozornění, pokud k tomu dojde.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Rozbalte **vlastnosti konfigurace**, **C/C++**, **příkazového řádku** složky.

1. V **rozšířené možnosti**, přidejte **/Validate-Charset** možnosti a určete upřednostňované kódování.

1. Zvolte **OK** uložte provedené změny.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)<br/>
[/ Execution-Charset (nastavení znakové sady spuštění)](../../build/reference/execution-charset-set-execution-character-set.md)<br/>
[/source-charset (nastavení zdrojové znakové sady)](../../build/reference/source-charset-set-source-character-set.md)<br/>
[/utf-8 (nastavení zdrojové znakové sady a spustitelné znakové sady na UTF-8)](../../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)