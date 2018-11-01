---
title: /Fe (název souboru EXE)
ms.date: 11/04/2016
f1_keywords:
- /fe
helpviewer_keywords:
- -Fe compiler option [C++]
- executable files, renaming
- rename file compiler option [C++]
- /Fe compiler option [C++]
- Fe compiler option [C++]
ms.assetid: 49f594fd-5e94-45fe-a1bf-7c9f2abb6437
ms.openlocfilehash: cac4dc0908c86574ef5b57c4436f734f94c0bb49
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473408"
---
# <a name="fe-name-exe-file"></a>/Fe (název souboru EXE)

Určuje název a adresář pro soubor .exe nebo knihovnu DLL vytvořený kompilátorem.

## <a name="syntax"></a>Syntaxe

> **/FE**[_cesta_] **/Fe:** _cesta_

### <a name="arguments"></a>Arguments

*pathname*<br/>
Relativní nebo absolutní cesta a název základního souboru nebo relativní nebo absolutní cesta k adresáři, nebo název základního souboru pro generované spustitelné soubory.

## <a name="remarks"></a>Poznámky

**/Fe** možnost umožňuje zadat výstupní adresář, název výstupního spustitelného souboru nebo obojí pro vygenerovaný spustitelný soubor. Pokud *cesta* končí oddělovačem cesty (**&#92;**), se předpokládá, že zadejte výstupní adresář. V opačném případě poslední součástí *cesta* slouží jako základní název výstupního souboru a zbytek *cesta* Určuje výstupní adresář. Pokud *cesta* nemá žádné oddělovače cesty, předpokládá se, zadejte název výstupního souboru v aktuálním adresáři. *Cesta* musí být umístěn do dvojitých uvozovek (**"**) pokud obsahují znaky, které nelze v krátkou cestu, jako jsou mezery, rozšířené znaky nebo součástí cesty více než osm znaků dlouhé.

Když **/Fe** možnost nezadáte, nebo pokud nějaký soubor základní název není zadán v *cesta*, kompilátor dává výstupnímu souboru výchozí název, pomocí základní název zadaný první soubor pro zdrojové i Objektové na příkazovém řádku a příponou .exe nebo .dll.

Pokud zadáte [/c (Kompilovat bez propojení)](c-compile-without-linking.md) možnost **/Fe** nemá žádný vliv.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Otevřít **vlastnosti konfigurace** > **Linkeru** > **Obecné** stránku vlastností.

1. Upravit **výstupní soubor** vlastnost. Zvolte **OK** uložte provedené změny.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>.

## <a name="example"></a>Příklad

Následující příkaz zkompiluje a propojí všechny zdrojové soubory jazyka C v aktuálním adresáři. Výsledný spustitelný soubor má název PROCESS.exe a vytvoří se v adresáři "C:\Users\User Name\repos\My Project\bin".

```
CL /Fe"C:\Users\User Name\repos\My Project\bin\PROCESS" *.C
```

## <a name="example"></a>Příklad

Následující příkaz vytvoří spustitelný soubor v `C:\BIN` se stejným základním názvem jako první zdrojový soubor v aktuálním adresáři:

```
CL /FeC:\BIN\ *.C
```

## <a name="see-also"></a>Viz také:

[Možnosti výstupního souboru (/F)](../../build/reference/output-file-f-options.md)<br/>
[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)<br/>
[Určení názvu cesty](../../build/reference/specifying-the-pathname.md)<br/>
