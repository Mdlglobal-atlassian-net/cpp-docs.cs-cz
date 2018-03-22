---
title: / POGOSAFEMODE (PGO spuštění v nouzovém režimu vlákno) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
f1_keywords:
- POGOSAFEMODE
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 886fbae5fbeb7606ec0321595f061d2262988170
ms.sourcegitcommit: ee7d74683af7631441c8c7f65ef5ceceaee4a5ee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="pogosafemode-run-pgo-in-thread-safe-mode"></a>/ POGOSAFEMODE (PGO spuštění v nouzovém režimu přístup z více vláken)

**Možnost /POGOSAFEMODE je zastaralé od ve Visual Studiu 2015**. Použití [/GENPROFILE: PŘESNÝ](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) a **/GENPROFILE:NOEXACT** možnosti místo. **/POGOSAFEMODE** – možnost linkeru Určuje, že je pro použití režimu vláken pro data zaznamenání profilu během optimalizace na základě profilu (PGO) cvičení spustí vytvořen instrumentovaného sestavení.

## <a name="syntax"></a>Syntaxe

> **/POGOSAFEMODE**

## <a name="remarks"></a>Poznámky

Optimalizace na základě profilu (PGO) má dva možné režimy profilování fázi: *rychlého režimu* a *nouzovém režimu*. Při vytváření profilu je v rychlého režimu, používá přírůstek instrukce ke zvýšení dat čítače. Instrukce přírůstek je rychlejší, ale není bezpečné pro přístup z více vláken. Při vytváření profilu je v nouzovém režimu, používá propojený přírůstek instrukce ke zvýšení dat čítače. Tento pokyn má stejné funkce jako pokyn přírůstek a bezpečné pro přístup z více vláken, ale je pomalejší.

**/POGOSAFEMODE** možnost nastaví instrumentovaného sestavení pomocí nouzového režimu. Tuto možnost lze použít, když zastaralé [/LTCG:PGINSTRUMENT](ltcg-link-time-code-generation.md) je zadán během fáze PGO instrumentace linkeru.

Ve výchozím nastavení vytváření profilů PGO funguje v rychlého režimu. **/ POGOSAFEMODE** je požadován, pouze pokud budete chtít použít nouzový režim.

Chcete-li spustit PGO profilace v nouzovém režimu, musíte použít buď **/GENPROFILE: PŘESNÝ** (doporučeno), nebo použijte proměnnou prostředí [PogoSafeMode](environment-variables-for-profile-guided-optimizations.md) nebo přepínač linkeru **/POGOSAFEMODE**, v závislosti na systému. Pokud provádíte profilace na x64 počítače, je potřeba použít přepínač linkeru. Pokud provádíte profilace na x86 počítače, můžete použít přepínač linkeru nebo definujte proměnnou prostředí na jakoukoli hodnotu před zahájením procesu instrumentace PGO.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **optimalizace** stránku vlastností.

1. V **vytvoření kódu v době odkaz** vlastnost, zvolte **profil optimalizace - nástrojích (nebo LTCG:PGInstrument)**.

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **příkazového řádku** stránku vlastností.

1. Zadejte **/POGOSAFEMODE** možnost do **další možnosti** pole. Zvolte **OK** uložte provedené změny.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[/ GENPROFILE a /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/LTCG](ltcg-link-time-code-generation.md)<br/>
[Optimalizace na základě profilu](../../build/reference/profile-guided-optimizations.md)<br/>
[Proměnné prostředí pro optimalizace na základě profilu](../../build/reference/environment-variables-for-profile-guided-optimizations.md)<br/>
