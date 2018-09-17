---
title: – spouštění-charset (nastavení znakové sady spuštění) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- execution-charset
- /execution-charset
dev_langs:
- C++
helpviewer_keywords:
- /execution-charset compiler option
- -execution-charset compiler option
ms.assetid: 0e02f487-2236-45bc-95f3-5760933a8f96
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3cd7acf018930c013f477cf4c3a8b3260a8d53ec
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714616"
---
# <a name="execution-charset-set-execution-character-set"></a>/ Execution-Charset (nastavení znakové sady spuštění)

Umožňuje určit spuštění znakové sady pro spustitelný soubor.

## <a name="syntax"></a>Syntaxe

```
/execution-charset:[IANA_name|.CPID]
```

## <a name="arguments"></a>Arguments

**IANA_name**<br/>
Název sady znaků definice IANA.

**CPID**<br/>
Identifikátor kódu stránky.

## <a name="remarks"></a>Poznámky

Můžete použít **/Execution-Charset** můžete zadat znaková sada spuštění. Znaková sada spuštění je kódování použité pro text ovládacího prvku programu, který je vstup do fáze kompilace koneckonců předběžného zpracování kroky. Znaková sada se používá pro interní reprezentace libovolný řetězec nebo znak literály do kompilovaného kódu. Nastavte tuto možnost k určení znakové sady rozšířeného spuštění při vaší zdrojové soubory obsahují znaky, které nejsou reprezentovat základní znakové sadě spuštění. Můžete použít buď IANA nebo ISO znaková sada název nebo tečku (.), za nímž následuje identifikátor číslice 3 až 5 desítkový kód stránky zadat znakovou sadu. Seznam podporovaných identifikátory znakových stránek a znakové sady názvy, naleznete v tématu [identifikátory znakových stránek](/windows/desktop/Intl/code-page-identifiers).

Ve výchozím nastavení sada Visual Studio zjistí značka pořadí bajtů k určení, zda zdrojový soubor je v zakódovaném formátu Unicode, například UTF-16 nebo UTF-8. Pokud se nenajde žádné značky pořadí bajtů, předpokládá zdrojový soubor je zakódován pomocí aktuální znakové stránce uživatele uvedeno znaková sada s použitím názvu nebo kódu stránky **/Source-Charset** možnost nebo **/UTF-8** možnost. Visual Studio umožňuje uložit zdrojovém kódu jazyka C++ pomocí některého z několika kódování znaků. Informace o spuštění a zdrojová znakových sadách najdete v tématu [znakové sady](../../cpp/character-sets.md) v dokumentaci jazyka.

Pokud chcete nastavit zdrojové znakové sady a znakové sady spuštění na UTF-8, můžete použít **/UTF-8** – možnost kompilátoru jako zástupce. Je ekvivalentní se zadáním **/source-charset:utf – 8 /execution-charset:utf – 8** na příkazovém řádku. Některé z těchto možností také umožňuje **/Validate-Charset** možnost ve výchozím nastavení.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Rozbalte **vlastnosti konfigurace**, **C/C++**, **příkazového řádku** složky.

1. V **rozšířené možnosti**, přidejte **/Execution-Charset** možnosti a určete upřednostňované kódování.

1. Zvolte **OK** uložte provedené změny.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)<br/>
[/ Source-Charset (nastavení zdrojové znakové sady)](../../build/reference/source-charset-set-source-character-set.md)
[/UTF-8 (nastavení zdrojové a spustitelné znakové sady UTF-8)](../../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)
 [ /Validate-Charset (ověření kompatibilních znaků)](../../build/reference/validate-charset-validate-for-compatible-characters.md)