---
title: Nastavení proměnných cesty a prostředí pro sestavení příkazového řádku
ms.custom: conceptual
ms.date: 07/24/2019
helpviewer_keywords:
- environment variables [C++]
- VCVARS32.bat file
- cl.exe compiler [C++], environment variables
- LINK tool [C++], environment variables
- PATH reserved word
- INCLUDE reserved word
- LINK tool [C++], path
- LIB environment variable
- compiling source code [C++], from command line
- environment variables [C++], CL compiler
ms.assetid: 99389528-deb5-43b9-b99a-03c8773ebaf4
ms.openlocfilehash: aeafe806e5d29b89c243586974814aa7cfc16d1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335589"
---
# <a name="set-the-path-and-environment-variables-for-command-line-builds"></a>Nastavení proměnných cesty a prostředí pro sestavení příkazového řádku

Nástroje sestavení příkazového řádku Microsoft C++ (MSVC) vyžadují několik proměnných prostředí, které jsou přizpůsobeny pro konfiguraci instalace a sestavení. Při instalaci úlohy Jazyka C++ instalačním programem sady Visual Studio vytvoří vlastní soubory příkazů nebo dávkové soubory, které nastavují požadované proměnné prostředí. Instalační program pak pomocí těchto souborů příkazů vytvoří zástupce pro nabídku Start systému Windows k otevření okna příkazového řádku pro vývojáře. Tyto klávesové zkratky nastavit proměnné prostředí pro konkrétní konfiguraci sestavení. Pokud chcete použít nástroje příkazového řádku, můžete spustit jednu z těchto zkratek nebo můžete otevřít okno prostého příkazového řádku a potom spustit jeden z vlastních souborů příkazů a nastavit konfigurační prostředí sestavení sami. Další informace naleznete [v tématu Použití sady nástrojů MSVC z příkazového řádku](building-on-the-command-line.md). Informace o použití souborů příkazů s příkazovým řádekm plain naleznete v části s názvem [Umístění souborů příkazů vývojáře](building-on-the-command-line.md#developer_command_file_locations).

Nástroje příkazového řádku MSVC používají proměnné prostředí PATH, TMP, INCLUDE, LIB a LIB path a také jiné proměnné prostředí specifické pro nainstalované nástroje, platformy a sady SDK. I jednoduchá instalace sady Visual Studio může nastavit dvacet nebo více proměnných prostředí. Vzhledem k tomu, že hodnoty těchto proměnných prostředí jsou specifické pro vaši instalaci a vaši volbu konfigurace sestavení a lze je změnit aktualizacemi nebo upgrady produktů, důrazně doporučujeme použít zástupce příkazového řádku vývojáře nebo jeden z přizpůsobených souborů příkazů, abyste je nastavili sami.

Chcete-li zjistit, které proměnné prostředí jsou nastaveny zástupcem příkazového řádku vývojáře, můžete použít příkaz SET. Otevřete okno jednoduchého příkazového řádku a zachyťte výstup příkazu SET pro účaří. Otevřete okno příkazového řádku vývojáře a zachyťte výstup příkazu SET pro porovnání. Nástroj diff, jako je například ten, který je součástí integrovaného integrovaného prostředí Visual Studio, může být užitečný pro porovnání proměnných prostředí a zobrazení, co je nastaveno příkazovým řádku pro vývojáře. Informace o specifických proměnných prostředí používaných kompilátorem a propojovacím programu naleznete v tématu [CL Environment Variables](reference/cl-environment-variables.md).

> [!NOTE]
> Několik nástrojů příkazového řádku nebo možností nástroje může vyžadovat oprávnění správce. Pokud máte při jejich použití problémy s oprávněními, doporučujeme otevřít okno příkazového řádku vývojáře pomocí možnosti **Spustit jako správce.** Ve Windows 10 kliknutím pravým tlačítkem myši otevřete místní nabídku okna příkazového řádku a pak zvolte **Další**, **Spustit jako správce**.

## <a name="see-also"></a>Viz také

[Použití sady nástrojů MSVC z příkazového řádku](building-on-the-command-line.md)<br/>
[Referenční zdroje k linkeru MSVC](reference/linking.md)<br/>
[Možnosti propojovacího zařízení MSVC](reference/linker-options.md)<br/>
[Odkaz na kompilátor MSVC](reference/compiling-a-c-cpp-program.md)<br/>
[Parametry kompilátoru MSVC](reference/compiler-options.md)
