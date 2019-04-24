---
title: Nastavení cesty a proměnných prostředí pro sestavení příkazového řádku
ms.custom: conceptual
ms.date: 11/04/2016
f1_keywords:
- include
- Lib
- Path
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
ms.openlocfilehash: fed3360294bec724af09b87e5abd7c6bb22fa285
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315388"
---
# <a name="set-the-path-and-environment-variables-for-command-line-builds"></a>Nastavení cesty a proměnných prostředí pro sestavení příkazového řádku

Sestavení z příkazového řádku nástroje Visual C++ vyžadují řady proměnných prostředí, která jsou přizpůsobená pro vaši konfiguraci instalace a sestavení. Při instalaci úlohy pro C++ pomocí instalačního programu sady Visual Studio vytvoří soubory vlastní příkaz nebo dávkové soubory, které nastavení proměnných prostředí vyžaduje. Instalační program použije tyto příkazové soubory k vytvořit zástupce v nabídce Windows Start otevřete okno příkazového řádku pro vývojáře. Tyto klávesové zkratky, nastavení proměnné prostředí pro konkrétní konfiguraci sestavení. Pokud chcete využívat nástroje příkazového řádku, můžete spustit jeden tyto klávesové zkratky, nebo můžete otevřít okno příkazového řádku prostý a poté spustíte jeden z vlastního příkazu soubory, které chcete nastavit konfigurační prostředí sestavení, sami. Další informace najdete v tématu [použít MSVC nástrojů z příkazového řádku](building-on-the-command-line.md).

Nástroje příkazového řádku jazyka Visual C++ použít CESTU, TMP, INCLUDE, LIB a LIBPATH proměnné prostředí a také použít jiné proměnné prostředí specifické pro vaše nainstalované nástroje, platformy a sady SDK. Dokonce i jednoduchý instalace sady Visual Studio může nastavit 20 nebo více proměnných prostředí. Protože hodnot těchto proměnných prostředí jsou specifické pro vaši instalaci a konfiguraci sestavení podle vlastního výběru a může změnit produktu aktualizace nebo upgrady, doporučujeme použít zástupce příkazového řádku pro vývojáře nebo jeden z přizpůsobit soubory příkazů, jejich nastavení místo nastavíte v prostředí Windows sami.

Pokud chcete zobrazit, které proměnné prostředí se nastavují pomocí zástupce příkazového řádku pro vývojáře, můžete příkaz SET. Otevřete okno příkazového řádku prostý a zachytit výstup příkazu SET pro směrný plán. Otevřete okno příkazového řádku pro vývojáře a zachytit výstup příkazu SET pro porovnání. Diff nástroje, jako je ten integrovaná v integrovaném vývojovém prostředí sady Visual Studio může být užitečné k porovnání proměnných prostředí a co je nastavena pomocí příkazového řádku pro vývojáře. Informace o konkrétní proměnné používané kompilátoru a linkeru, naleznete v tématu [proměnné prostředí CL](reference/cl-environment-variables.md).

> [!NOTE]
>  Několik nástrojů příkazového řádku nebo možnosti nástroje mohou vyžadovat oprávnění správce. Pokud máte oprávnění problémy, když je budete používat, doporučujeme otevřete okno příkazového řádku pro vývojáře s použitím **spustit jako správce** možnost. Ve Windows 10, klikněte pravým tlačítkem a otevřete místní nabídku pro okno příkazového řádku a pak zvolte **Další**, **spustit jako správce**.

## <a name="see-also"></a>Viz také:

[Použití sady nástrojů MSVC z příkazového řádku](building-on-the-command-line.md)<br/>
[Referenční zdroje k linkeru MSVC](reference/linking.md)<br/>
[Možnosti linkeru MSVC](reference/linker-options.md)<br/>
[Referenční zdroje ke kompilátorům MSVC](reference/compiling-a-c-cpp-program.md)<br/>
[Parametry kompilátoru MSVC](reference/compiler-options.md)
