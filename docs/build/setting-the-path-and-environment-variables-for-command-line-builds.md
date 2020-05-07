---
title: Nastavení cesty a proměnných prostředí pro sestavení příkazového řádku
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
# <a name="set-the-path-and-environment-variables-for-command-line-builds"></a>Nastavení cesty a proměnných prostředí pro sestavení příkazového řádku

Nástroje pro sestavení příkazového řádku Microsoft C++ (MSVC) vyžadují několik proměnných prostředí, které jsou přizpůsobené pro instalaci a konfiguraci sestavení. Když instalační program sady Visual Studio nainstaluje úlohu C++, vytvoří přizpůsobené soubory příkazů nebo dávkové soubory, které nastaví požadované proměnné prostředí. Instalační program pak pomocí těchto souborů příkazů vytvoří klávesové zkratky pro nabídku Start systému Windows a otevře okno příkazového řádku pro vývojáře. Tyto klávesové zkratky nastaví proměnné prostředí pro konkrétní konfiguraci sestavení. Pokud chcete použít nástroje příkazového řádku, můžete spustit jednu z těchto klávesových zkratek, nebo můžete otevřít okno příkazového řádku a potom spustit jeden z vlastních příkazových souborů pro nastavení prostředí konfigurace sestavení sami. Další informace najdete v tématu [použití sady nástrojů MSVC z příkazového řádku](building-on-the-command-line.md). Chcete-li použít soubory příkazů s jednoduchým příkazovým řádkem, přečtěte si část s názvem " [umístění souborů příkazů pro vývojáře](building-on-the-command-line.md#developer_command_file_locations)".

Nástroje příkazového řádku MSVC používají proměnné prostředí PATH, TMP, INCLUDE, LIB a LIBPATH a používají také další proměnné prostředí specifické pro nainstalované nástroje, platformy a sady SDK. Dokonce i jednoduchá instalace sady Visual Studio může nastavit dvacet nebo více proměnných prostředí. Vzhledem k tomu, že hodnoty těchto proměnných prostředí jsou specifické pro vaši instalaci a výběr konfigurace sestavení a lze je změnit pomocí aktualizací a upgradů produktu, důrazně doporučujeme použít zástupce příkazového řádku pro vývojáře nebo některý z přizpůsobených souborů příkazů k jejich nastavení, místo abyste je nastavili v prostředí systému Windows sami.

Chcete-li zjistit, které proměnné prostředí jsou nastaveny pomocí zástupce příkazového řádku vývojáře, můžete použít příkaz SET. Otevřete okno příkazového řádku s prostým textem a zaznamenejte výstup příkazu SET pro směrný plán. Otevřete okno příkazového řádku vývojáře a zaznamenejte výstup příkazu SET pro porovnání. Rozdílový nástroj, jako je například ten integrovaný do integrovaného vývojového prostředí (IDE) sady Visual Studio, může být užitečný pro porovnání proměnných prostředí a zjištění, co je nastaveno pomocí příkazového řádku pro vývojáře. Informace o specifických proměnných prostředí používaných kompilátorem a linkerem naleznete v tématu [proměnné prostředí CL](reference/cl-environment-variables.md).

> [!NOTE]
> Některé nástroje příkazového řádku nebo možnosti nástroje mohou vyžadovat oprávnění správce. Pokud máte při použití problémy s oprávněními, doporučujeme, abyste otevřeli okno příkazového řádku pro vývojáře pomocí možnosti **Spustit jako správce** . V systému Windows 10 kliknutím pravým tlačítkem otevřete místní nabídku okna příkazového řádku a pak zvolte možnost **Další**, **Spustit jako správce**.

## <a name="see-also"></a>Viz také

[Použití sady nástrojů MSVC z příkazového řádku](building-on-the-command-line.md)<br/>
[Referenční zdroje k linkeru MSVC](reference/linking.md)<br/>
[Možnosti linkeru MSVC](reference/linker-options.md)<br/>
[Reference k kompilátoru MSVC](reference/compiling-a-c-cpp-program.md)<br/>
[Parametry kompilátoru MSVC](reference/compiler-options.md)
