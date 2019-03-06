---
title: /MANIFESTDEPENDENCY (Určit závislosti manifestu)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.AdditionalManifestDependencies
helpviewer_keywords:
- MANIFESTDEPENDENCY linker option
- /MANIFESTDEPENDENCY linker option
- -MANIFESTDEPENDENCY linker option
ms.assetid: e4b68313-33a2-4c3e-908e-ac2b9f7d6a73
ms.openlocfilehash: debff86b506545862ce4054bf4e210cdb8a29185
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418396"
---
# <a name="manifestdependency-specify-manifest-dependencies"></a>/MANIFESTDEPENDENCY (Určit závislosti manifestu)

```
/MANIFESTDEPENDENCY:manifest_dependency
```

## <a name="remarks"></a>Poznámky

/ MANIFESTDEPENDENCY umožňuje zadat atributy, které budou umístěny do \<závislost > části souboru manifestu.

Zobrazit [volbu/manifest (vytvoření Side-by-Side manifestu sestavení)](../../build/reference/manifest-create-side-by-side-assembly-manifest.md) informace o tom, jak vytvořit soubor manifestu.

Další informace o \<závislost > části souboru manifestu naleznete v tématu [konfiguračních souborů vydavatele](/windows/desktop/SbsCs/publisher-configuration-files).

/ MANIFESTDEPENDENCY informace může být předán linkeru v jednom ze dvou způsobů:

- Přímo na příkazovém řádku (nebo v souboru odpovědí) s /MANIFESTDEPENDENCY.

- Prostřednictvím [komentář](../../preprocessor/comment-c-cpp.md) direktivy pragma.

Následující příklad ukazuje komentář /MANIFESTDEPENDENCY předány prostřednictvím direktivy pragma

```cpp
#pragma comment(linker, "\"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"")
```

Výsledek bude následující položka v souboru manifestu:

```xml
<dependency>
  <dependentAssembly>
    <assemblyIdentity type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*' />
  </dependentAssembly>
</dependency>
```

Stejné /MANIFESTDEPENDENCY komentářů mohou být předány do příkazového řádku takto:

```cmd
"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"
```

Linker se shromažďování /MANIFESTDEPENDENCY komentáře, odstranění duplicitních položek a pak přidejte výsledný řetězec XML do souboru manifestu.  Pokud linker zjistí konfliktní záznamy, v souboru manifestu bude poškozena a se aplikaci nepodaří spustit (záznam může přidat do protokolu událostí udávající příčiny selhání).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **soubor manifestu** stránku vlastností.

1. Upravit **Další závislosti manifestu** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

1. Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalManifestDependencies%2A>.

## <a name="see-also"></a>Viz také:

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)
