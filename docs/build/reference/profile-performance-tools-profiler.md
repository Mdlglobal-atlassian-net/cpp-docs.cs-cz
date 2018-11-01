---
title: /PROFILE (profiler nástrojů výkonu)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.Profile
helpviewer_keywords:
- -PROFILE linker option
- /PROFILE linker option
ms.assetid: e676baa1-5063-47a3-a357-ba0d1f0d1699
ms.openlocfilehash: 26f4ba4efc20f5fee70b2937cdb943689c948888
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519912"
---
# <a name="profile-performance-tools-profiler"></a>/PROFILE (profiler nástrojů výkonu)

Vytvoří výstupní soubor, který lze použít s profilerem Performance Tools.

## <a name="syntax"></a>Syntaxe

```
/PROFILE
```

## <a name="remarks"></a>Poznámky

/ PROFILE zahrnuje následující možnosti linkeru:

- [/ OPT: REF](../../build/reference/opt-optimizations.md)

- / OPT: NOICF

- [/ INCREMENTAL: NO](../../build/reference/incremental-link-incrementally.md)

- [/ FIXED: NO](../../build/reference/fixed-fixed-base-address.md)

/ PROFILE přikazuje linkeru vygenerování části přemístění v bitové kopii programu.  Oddíl pro přemístění umožňuje profileru pro transformaci bitové kopie programu k získání dat profilu.

**/ PROFILE** je k dispozici pouze ve verzi Enterprise (vývoj v týmu).  Další informace o nástroj PREfast najdete v tématu [analýzy kódu pro C/C++ přehled](/visualstudio/code-quality/code-analysis-for-c-cpp-overview).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Rozbalte **vlastnosti konfigurace** uzlu.

1. Rozbalte **Linkeru** uzlu.

1. Vyberte **Upřesnit** stránku vlastností.

1. Upravit **profilu** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

1. Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Profile%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)