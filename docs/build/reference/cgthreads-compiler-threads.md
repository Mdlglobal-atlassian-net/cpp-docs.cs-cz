---
title: -CGTHREADS (vlákna kompilátoru) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- /CGTHREADS linker option
- -CGTHREADS linker option
- CGTHREADS linker option
ms.assetid: 4b52cfdb-3702-470b-9580-fabeb1417488
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d717ffb3ed135ffe9e6f4ed2c55f925e3f10d86f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720524"
---
# <a name="cgthreads-compiler-threads"></a>/CGTHREADS (Vlákna kompilátoru)

Nastaví počet vláken cl.exe pro optimalizace a generování kódu při generování kódu při propojování určena.

## <a name="syntax"></a>Syntaxe

```
/CGTHREADS:[1-8]
```

## <a name="arguments"></a>Arguments

*Číslo*<br/>
Maximální počet vláken pro cl.exe pro použití v rozsahu 1 až 8.

## <a name="remarks"></a>Poznámky

**/Cgthreads** možnost určuje maximální počet vláken cl.exe využívá paralelní fázích optimalizace a generování kódu při propojování kompilace generování kódu ([parametru/LTCG](../../build/reference/ltcg-link-time-code-generation.md)) je zadat. Ve výchozím nastavení používá cl.exe čtyři vlákna, jako kdyby **/CGTHREADS:4** byly zadány. Pokud jsou k dispozici více jader procesoru větší `number` hodnotu můžete zkrátit dobu sestavování.

Sestavení lze zadat více úrovní paralelismu. Přepínač msbuild.exe **/maxcpucount** určuje počet procesů MSBuild, které můžou běžet paralelně. [/MP (sestavení pomocí několika procesů)](../../build/reference/mp-build-with-multiple-processes.md) kompilátoru příznak určuje, kolik cl.exe procesy, které současně kompilaci zdrojové soubory. [/Cgthreads](../../build/reference/cgthreads-code-generation-threads.md) – možnost kompilátoru určuje počet vláken používaných každý proces cl.exe. Protože procesor může spustit pouze počet vláken ve stejnou dobu jako jader procesoru, není užitečné k určení vyšší hodnoty pro všechny tyto možnosti ve stejnou dobu a může být kontraproduktivní. Další informace o tom, jak vytvořit paralelně, naleznete v tématu [sestavování více projektů současně](/visualstudio/msbuild/building-multiple-projects-in-parallel-with-msbuild).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace**, **Linkeru** složky.

1. Vyberte **příkazového řádku** stránku vlastností.

1. Upravit **další možnosti** vlastnost, aby zahrnovala **/cgthreads:**`number`, kde `number` je hodnotu od 1 do 8 a potom zvolte **OK**.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Možnosti linkeru](../../build/reference/linker-options.md)<br/>
[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)