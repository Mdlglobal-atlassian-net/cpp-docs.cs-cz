---
title: -Fe (název souboru EXE) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /fe
dev_langs:
- C++
helpviewer_keywords:
- -Fe compiler option [C++]
- executable files, renaming
- rename file compiler option [C++]
- /Fe compiler option [C++]
- Fe compiler option [C++]
ms.assetid: 49f594fd-5e94-45fe-a1bf-7c9f2abb6437
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0afd8a863c9b8482e2b7f3868047845818bd2923
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377054"
---
# <a name="fe-name-exe-file"></a>/Fe (název souboru EXE)

Určuje název a adresář pro soubor .exe nebo knihovny DLL vytvořené kompilátoru.

## <a name="syntax"></a>Syntaxe

> **/FE**[_pathname_]  
> **/ Fe:** _pathname_  

### <a name="arguments"></a>Arguments

*pathname*<br/>
Relativní nebo absolutní cesta a název základního souboru nebo relativní nebo absolutní cesta k adresáři, nebo název základního souboru pro generovaný spustitelný soubor.

## <a name="remarks"></a>Poznámky

**/Fe** možnost umožňuje zadat výstupnímu adresáři, výstupní název spustitelného souboru nebo obojí, pro vygenerovaný spustitelný soubor. Pokud *pathname* končí v oddělovač cesty (**&#92;**), se předpokládá, že zadejte výstupního adresáře. V opačném poslední součástí *pathname* slouží jako základní název výstupního souboru a zbytek z *pathname* určuje výstupnímu adresáři. Pokud *pathname* nemá oddělovačů cesta se předpokládá, že zadejte název výstupního souboru v aktuálním adresáři. *Pathname* musí být uzavřena do uvozovek (**"**) Pokud obsahuje znaky, které nelze v krátké cestu, například mezery, rozšířené znaky nebo cesta součástí více než osm znaků dlouhé.

Když **/Fe** není určena možnost, nebo když soubor základní název není zadán v *pathname*, kompilátor poskytuje výstupní soubor pomocí základní název první zdrojového objektu souboru nebo zadaný výchozí název na příkazovém řádku a příponou .exe nebo .dll.

Pokud zadáte [/c (Kompilovat bez propojení)](c-compile-without-linking.md) možnost **/Fe** nemá žádný vliv.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Otevřete **vlastnosti konfigurace** > **Linkeru** > **Obecné** stránku vlastností.

1. Změnit **výstupní soubor** vlastnost. Zvolte **OK** uložte provedené změny.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>.

## <a name="example"></a>Příklad

Následující příkazový řádek zkompiluje a propojuje všechny zdrojové soubory C v aktuálním adresáři. Výsledný spustitelný soubor je s názvem PROCESS.exe a je vytvořen v adresáři "C:\Users\User Name\repos\My Project\bin".

```
CL /Fe"C:\Users\User Name\repos\My Project\bin\PROCESS" *.C
```

## <a name="example"></a>Příklad

Následující příkaz vytvoří spustitelný soubor v `C:\BIN` se stejným názvem základní jako první zdrojový soubor v aktuálním adresáři:

```
CL /FeC:\BIN\ *.C
```

## <a name="see-also"></a>Viz také

[Možnosti výstupního souboru (/F)](../../build/reference/output-file-f-options.md)<br/>
[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)<br/>
[Určení názvu cesty](../../build/reference/specifying-the-pathname.md)<br/>
