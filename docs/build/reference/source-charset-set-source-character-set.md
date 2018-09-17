---
title: -Zdroj-charset (nastavení zdrojové znakové sady) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- source-charset
- /source-charset
dev_langs:
- C++
helpviewer_keywords:
- /execution-charset compiler option
ms.assetid: d3c5bf7f-526d-4ee4-acc5-c1a02a4fc481
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c36f898c005a989a7be78e436b560fe9a0536b57
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715062"
---
# <a name="source-charset-set-source-character-set"></a>/ Source-Charset (nastavení zdrojové znakové sady)

Umožňuje určit zdrojové znakové sady pro spustitelný soubor.

## <a name="syntax"></a>Syntaxe

```
/source-charset:[IANA_name|.CPID]
```

## <a name="arguments"></a>Arguments

**IANA_name**<br/>
Název sady znaků definice IANA.

**CPID**<br/>
Identifikátor kódu stránky jako desítkové číslo.

## <a name="remarks"></a>Poznámky

Můžete použít **/Source-Charset** můžete zadat rozšířené zdrojové znakové nastaveno pro použití při zdrojové soubory obsahují znaky, které nejsou reprezentovány v základní zdrojové znakové sady. Zdrojová znaková sada je kódování použité k interpretaci text zdrojového programu do vnitřní reprezentaci používá jako vstup do fáze předběžného zpracování před kompilací. Vnitřní reprezentaci je pak převedeno do znakové sady spuštění pro ukládání hodnot řetězců a znaků ve spustitelném souboru. Můžete použít buď IANA nebo ISO znaková sada název nebo tečku (.), za nímž následuje identifikátor číslice 3 až 5 desítkový kód stránky zadat znakovou sadu. Seznam podporovaných identifikátory znakových stránek a znakové sady názvy, naleznete v tématu [identifikátory znakových stránek](/windows/desktop/Intl/code-page-identifiers).

Ve výchozím nastavení sada Visual Studio zjistí značka pořadí bajtů k určení, zda zdrojový soubor je v zakódovaném formátu Unicode, například UTF-16 nebo UTF-8. Pokud se nenajde žádné značky pořadí bajtů, předpokládá zdrojový soubor je kódovaný pomocí aktuální znakové stránce uživatele, pokud znaková sada s použitím názvu nebo kódu stránky **/Source-Charset** možnost. Visual Studio umožňuje uložit zdrojovém kódu jazyka C++ pomocí některého z několika kódování znaků. Další informace o znakové sady spuštění a zdrojová najdete v tématu [znakové sady](../../cpp/character-sets.md) v dokumentaci jazyka.

Zdrojová znaková sada, kterou zadáte musí být namapovaný 7bitových znaků ASCII na stejné body kódu ve znakové sadě nebo mnoho chyb kompilace jsou za ní nejpravděpodobněji následují. Vaše zdrojové znakové sady musí být také lze mapovat na rozšířené znak Unicode UTF-8 nastavuje kódovat. Znaky, které nejsou kódovat v kódování UTF-8 jsou reprezentovány náhradou specifický pro implementaci. Kompilátor společnosti Microsoft používá otazník pro tyto znaky.

Pokud chcete nastavit zdrojové znakové sady a znakové sady spuštění na UTF-8, můžete použít **/UTF-8** – možnost kompilátoru jako zástupce. Je ekvivalentní se zadáním **/source-charset:utf – 8 /execution-charset:utf – 8** na příkazovém řádku. Některé z těchto možností také umožňuje **/Validate-Charset** možnost ve výchozím nastavení.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Rozbalte **vlastnosti konfigurace**, **C/C++**, **příkazového řádku** složky.

1. V **rozšířené možnosti**, přidejte **/Source-Charset** možnosti a určete upřednostňované kódování.

1. Zvolte **OK** uložte provedené změny.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)<br/>
[/ Execution-Charset (nastavení znakové sady spuštění)](../../build/reference/execution-charset-set-execution-character-set.md)
[/UTF-8 (nastavení zdrojové a spustitelné znakové sady UTF-8)](../../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)
 [ /Validate-Charset (ověření kompatibilních znaků)](../../build/reference/validate-charset-validate-for-compatible-characters.md)