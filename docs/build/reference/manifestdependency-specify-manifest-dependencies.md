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
ms.openlocfilehash: 43239efe70cc555d1a7e03c5d67e99e40ccd480e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492707"
---
# <a name="manifestdependency-specify-manifest-dependencies"></a>/MANIFESTDEPENDENCY (Určit závislosti manifestu)

```
/MANIFESTDEPENDENCY:manifest_dependency
```

## <a name="remarks"></a>Poznámky

/MANIFESTDEPENDENCY umožňuje zadat atributy, které budou umístěny v \<části > závislostí souboru manifestu.

Informace o tom, jak vytvořit soubor manifestu, najdete v tématu [/manifest (Vytvoření manifestu souběžného sestavení)](manifest-create-side-by-side-assembly-manifest.md) .

Další informace o \<části > závislostí souboru manifestu najdete v tématu [konfigurační soubory vydavatele](/windows/win32/SbsCs/publisher-configuration-files).

/MANIFESTDEPENDENCY informace mohou být předány do linkeru jedním ze dvou způsobů:

- Přímo na příkazovém řádku (nebo v souboru odpovědí) pomocí/MANIFESTDEPENDENCY.

- Prostřednictvím direktivy pragma [Comment](../../preprocessor/comment-c-cpp.md) .

Následující příklad ukazuje/MANIFESTDEPENDENCY komentář předaný prostřednictvím direktivy pragma,

```cpp
#pragma comment(linker, "\"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"")
```

Výsledkem je následující položka v souboru manifestu:

```xml
<dependency>
  <dependentAssembly>
    <assemblyIdentity type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*' />
  </dependentAssembly>
</dependency>
```

Stejné komentáře/MANIFESTDEPENDENCY lze předat na příkazovém řádku následujícím způsobem:

```cmd
"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"
```

Linker bude shromažďovat komentáře/MANIFESTDEPENDENCY, eliminovat duplicitní položky a pak přidat výsledný řetězec XML do souboru manifestu.  Pokud linker najde konfliktní položky, soubor manifestu se poškodí a aplikace se nespustí (položka může být přidána do protokolu událostí, která indikuje zdroj selhání).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte stránku vlastností**souboru manifestu** **linkeru** >  **vlastnosti** > konfigurace.

1. Upravte vlastnost **Další závislosti manifestu** .

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

1. Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalManifestDependencies%2A>.

## <a name="see-also"></a>Viz také:

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)
