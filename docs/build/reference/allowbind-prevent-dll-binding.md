---
title: /ALLOWBIND (Zabránit vazbě knihoven DLL)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.PreventDLLBinding
- /allowbind
helpviewer_keywords:
- /ALLOWBIND linker option
- binding DLLs
- preventing DLL binding
- ALLOWBIND linker option
- -ALLOWBIND linker option
- DLLs [C++], preventing binding
ms.assetid: 30e37e24-12e4-407e-988a-39d357403598
ms.openlocfilehash: bd9976e434441d2480386ee6fa3d0315fd8d2ef5
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2019
ms.locfileid: "57818840"
---
# <a name="allowbind-prevent-dll-binding"></a>/ALLOWBIND (Zabránit vazbě knihoven DLL)

```
/ALLOWBIND[:NO]
```

## <a name="remarks"></a>Poznámky

/ALLOWBIND:No nastaví bit v hlavičce knihovny DLL, které označuje Bind.exe, že image se nemůže vázat. Možná nebudete chtít knihovnu DLL, pokud je digitálně podepsané (vazba zneplatní podpis).

Můžete upravit existující knihovny DLL pro funkce /ALLOWBIND s [/ALLOWBIND](allowbind.md) – možnost nástroje EDITBIN.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Rozbalte **vlastnosti konfigurace**, **Linkeru**a vyberte **příkazového řádku**.

1. Zadejte `/ALLOWBIND:NO` do **další možnosti**.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Odkaz na MSVC linkeru](linking.md)<br/>
[Možnosti Linkeru MSVC](linker-options.md)<br/>
[BindImage – funkce](/windows/desktop/api/imagehlp/nf-imagehlp-bindimage)<br/>
[BindImageEx – funkce](/windows/desktop/api/imagehlp/nf-imagehlp-bindimageex)
