---
title: /QIfist (Potlačit _ftol)
ms.date: 11/04/2016
f1_keywords:
- /qifist
helpviewer_keywords:
- QIfist compiler option [C++]
- -QIfist compiler option [C++]
- /QIfist compiler option [C++]
ms.assetid: 1afd32a5-f658-4b66-85f4-e0ce4cb955bd
ms.openlocfilehash: 7af88c91793688d23cf35177ae7a5250b04832a8
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816591"
---
# <a name="qifist-suppress-ftol"></a>/QIfist (Potlačit _ftol)

Zastaralé Potlačí volání funkce nápovědy `_ftol` při převodu z typu s plovoucí desetinnou čárkou na celočíselný typ vyžádáním.

## <a name="syntax"></a>Syntaxe

```
/QIfist
```

## <a name="remarks"></a>Poznámky

> [!NOTE]
>  **/ QIfist** je dostupná pouze v kompilátoru cílení x86; tato možnost kompilátoru není k dispozici v kompilátorech, které cílí na x64 orARM.

Kromě převod z typu s plovoucí desetinnou čárkou na celočíselný typ `_ftol` funkce zajišťuje režimu zaokrouhlování jednotku s plovoucí desetinnou čárkou (FPU) směrem k nule (zkrácení), nastavením bitů 10 a 11 řídicího slova. Zaručí se tak, že převod z typu s plovoucí desetinnou čárkou na celočíselný typ dochází podle popisu ve standardu ANSI jazyka C (desetinná část čísla se zahodí). Při použití **/QIfist**, tuto záruku už neplatí. Režim bude jednu ze čtyř, jak je uvedeno v Intel referenční příručky:

- Zaokrouhlit na nejbližší (sudé číslo Pokud zařízením)

- Zaokrouhlí směrem k zápornému nekonečnu

- Zaokrouhlení směrem ke kladnému nekonečnu

- Zaokrouhlí směrem k nule.

Můžete použít [_control87 _controlfp, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) funkce C Run-Time pro úpravu zaokrouhlení chování FPU. Režim FPU zaokrouhlení výchozí hodnota je "Zaokrouhlit na nejbližší." Pomocí **/QIfist** může zlepšit výkon vaší aplikace, ale ne bez rizika. Měli byste důkladně otestovat části kódu, které jsou citlivé na režimech zaokrouhlení předtím, než spoléhání se na kód sestaven s **/QIfist** v produkčním prostředí.

[/ arch (x86)](arch-x86.md) a **/QIfist** nelze použít na stejném kompilace.

> [!NOTE]
>  **/ QIfist** je výsledkem bude ve výchozím nastavení protože zaokrouhlování bity také vliv plovoucí desetinná čárka s plovoucí desetinnou čárkou neukazuje zaokrouhlení (které dojde po každé výpočtu), tak když nastavíte příznaky pro zaokrouhlení C-style (směrem k nule), vaše plovoucí desetinnou čárkou výpočty se může lišit. **/ QIfist** neměl by se používat, pokud váš kód závisí na očekávané chování zkracování necelá část hodnoty číslo s plovoucí desetinnou čárkou. Pokud si nejste jistí, nepoužívejte **/QIfist**.

**/QIfist** možnost je zastaralé od verze Visual Studio 2005. Kompilátor provedl významná vylepšení float k urychlení int převodu. Seznam zastaralých kompilátoru možnosti najdete v tématu **zastaralé a odebrat možnosti kompilátoru** v [možnosti kompilátoru seřazené podle kategorie](compiler-options-listed-by-category.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **příkazového řádku** stránku vlastností.

1. Zadejte možnost do kompilátoru **další možnosti** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[/Q – možnosti (operace nízké úrovně)](q-options-low-level-operations.md)<br/>
[Možnosti kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
