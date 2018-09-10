---
title: -MANIFESTDEPENDENCY (určení závislostí manifestu) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.AdditionalManifestDependencies
dev_langs:
- C++
helpviewer_keywords:
- MANIFESTDEPENDENCY linker option
- /MANIFESTDEPENDENCY linker option
- -MANIFESTDEPENDENCY linker option
ms.assetid: e4b68313-33a2-4c3e-908e-ac2b9f7d6a73
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5b82bd32bec0e665f815563ccea2ee05f6ae5172
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44315415"
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

1. Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalManifestDependencies%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)