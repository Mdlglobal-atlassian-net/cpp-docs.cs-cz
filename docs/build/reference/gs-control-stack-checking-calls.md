---
title: /Gs (kontrola volání ověření zásobníku)
ms.date: 10/25/2018
f1_keywords:
- /GS
helpviewer_keywords:
- disabling stack probes
- GS compiler option [C++]
- /GS compiler option [C++]
- stack, stack probes
- stack probes
- -GS compiler option [C++]
- stack checking calls
ms.assetid: 40daed7c-f942-4085-b872-01e12b37729e
ms.openlocfilehash: e31b42c1d9422d44c5f106f40c4a60a38f23425b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818562"
---
# <a name="gs-control-stack-checking-calls"></a>/Gs (kontrola volání ověření zásobníku)

Určuje mezní hodnotu pro sondy zásobníku.

## <a name="syntax"></a>Syntaxe

> **/Gs**[*size*]

## <a name="arguments"></a>Arguments

*Velikost*<br/>
(Volitelné) Počet bajtů, které může zabírat místní proměnné před sondu zásobníku je zahájeno. Je povolena mezera mezi **/Gs** a *velikost*.

## <a name="remarks"></a>Poznámky

A *sondy zásobníku* je posloupnost kód, který kompilátor vloží na začátek volání funkce. Při spuštění, dosáhne sondu zásobníku benignly do paměti na množství místa, které je nutné pro ukládání místních proměnných funkce. To způsobí, že transparentně stránky v paměti další zásobníku v případě potřeby předtím, než spustí zbývající část funkce operačního systému.

Ve výchozím nastavení kompilátor generuje kód, který iniciuje sondu zásobníku, pokud funkci vyžaduje více než jednu stránku místo v zásobníku. To je ekvivalentní možnosti kompilátoru **/Gs4096** pro x86, x 64, ARM, ARM64 platformy a. Tato hodnota umožňuje aplikaci a Windows správce paměti pro zvýšení množství paměti potvrzené do zásobníku programu dynamicky za běhu.

> [!NOTE]
> Výchozí hodnota **/Gs4096** umožňuje zásobníku aplikací pro Windows správně růst v době běhu programu. Doporučujeme vám, pokud si nejste jisti, že přesně Proč je třeba změnit ho nelze změnit výchozí hodnotu.

Některé programy – například ovladačů virtuálních zařízení – nevyžadují, aby tento mechanismus výchozí zásobníku růstu. V takovém případě nejsou nutné sondy zásobníku a zastavíte kompilátoru generování nastavením *velikost* na hodnotu, která je větší, než všechny funkce bude vyžadovat místní proměnné úložiště.

**/ Gs0** iniciuje zásobníku sondy pro každé volání funkce, která vyžaduje úložiště pro místní proměnné. To může mít negativní dopad na výkon.

Pro x64 cílí, pokud **/Gs** je zadána možnost bez *velikost* argument, je stejný jako **/Gs0**. Pokud *velikost* argument je 1 až 9, upozornění D9014 je vygenerován a efekt je stejné jako zadání **/Gs0**.

Pro x86, ARM, ARM64 cíle a **/Gs** možnost bez *velikost* argument je stejný jako **/Gs4096**. Pokud *velikost* argument je 1 až 9, upozornění D9014 je vygenerován a efekt je stejné jako zadání **/Gs4096**.

Pro všechny cíle *velikost* argument mezi 10 a 2147485647 nastaví prahovou hodnotu na zadanou hodnotu. A *velikost* 2147485648 nebo větší způsobí závažné chyby C1049.

Sondy zásobníku zapnutí nebo vypnutí můžete vypnout pomocí [check_stack –](../../preprocessor/check-stack.md) směrnice. **/GS** a `check_stack` – Direktiva pragma nemají žádný vliv na standardní rutiny knihoven C; ovlivní pouze funkce, které při kompilaci.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Zadejte **/Gs** – možnost kompilátoru a volitelné velikost v **další možnosti**. Zvolte **OK** nebo **použít** uložte provedené změny.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
