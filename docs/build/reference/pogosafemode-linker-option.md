---
title: / POGOSAFEMODE (spustit PGO v nouzovém režimu vlákno)
ms.date: 03/14/2018
f1_keywords:
- POGOSAFEMODE
ms.openlocfilehash: bbb328bf67d7823305a43f1d61252747cf5ea29e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319717"
---
# <a name="pogosafemode-run-pgo-in-thread-safe-mode"></a>/ POGOSAFEMODE (spustit PGO v nouzovém režimu vlákno)

**Možnost /POGOSAFEMODE je zastaralé od verze Visual Studio 2015**. Použití [/genprofile: přesné](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) a **/GENPROFILE:NOEXACT** místo možnosti. **/POGOSAFEMODE** – možnost linkeru, určuje, že se vytvoří instrumentované sestavení pro použití režimu bezpečné pro vlákna pro data zaznamenání profilů během profilováním řízené optimalizace (PGO) tréninková spuštění.

## <a name="syntax"></a>Syntaxe

> **/POGOSAFEMODE**

## <a name="remarks"></a>Poznámky

Profilově řízené optimalizace (PGO) má během fáze vytváření profilů dva možné režimy: *rychlém režimu* a *Nouzový režim*. Když je profilování v rychlém režimu, používá pokyn přírůstek na zvýšení počtu čítačů dat. Instrukce přírůstek je rychlejší, ale není bezpečná pro vlákno. Když je profilování v nouzovém režimu, používá pokyn propojené přírůstek na zvýšení počtu čítačů dat. Tento pokyn má stejné funkce jako instrukce přírůstek má a je bezpečná pro vlákno, ale je pomalejší.

**/POGOSAFEMODE** parametr nastaví instrumentované sestavení pomocí nouzového režimu. Tato možnost může být pouze nepoužívá, pokud se zastaralou [/LTCG:PGINSTRUMENT](ltcg-link-time-code-generation.md) specifikovaném během fáze instrumentace linkeru PGO.

Ve výchozím nastavení PGO profilování pracuje v rychlém režimu. **/ POGOSAFEMODE** je vyžadováno pouze pokud budete chtít použít nouzový režim.

Pokud chcete spustit profilování PGO v nouzovém režimu, je nutné použít buď **/genprofile: přesné** (upřednostňováno), nebo použít proměnnou prostředí [PogoSafeMode](../environment-variables-for-profile-guided-optimizations.md) nebo přepínač linker **/POGOSAFEMODE**, v závislosti na systému. Pokud provádíte profilaci na x x64 počítače, je potřeba použít přepínač linkeru. Pokud provádíte profilaci na x x86 počítače, můžete použít přepínač linkeru nebo definovat proměnné prostředí na libovolnou hodnotu před zahájením procesu instrumentace PGO.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **optimalizace** stránku vlastností.

1. V **generování kódu při propojování** vlastnost, zvolte **optimalizace na základě profilu - instrumentovat (/ LTCG: pginstrument)**.

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **příkazového řádku** stránku vlastností.

1. Zadejte **/POGOSAFEMODE** možnost do **další možnosti** pole. Zvolte **OK** uložte provedené změny.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[/ GENPROFILE a /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/LTCG](ltcg-link-time-code-generation.md)<br/>
[Optimalizace na základě profilu](../profile-guided-optimizations.md)<br/>
[Proměnné prostředí pro optimalizace na základě profilu](../environment-variables-for-profile-guided-optimizations.md)<br/>
