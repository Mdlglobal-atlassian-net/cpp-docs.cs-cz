---
title: -ALLOWBIND (zabránění vazbě knihoven DLL) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.PreventDLLBinding
- /allowbind
dev_langs:
- C++
helpviewer_keywords:
- /ALLOWBIND linker option
- binding DLLs
- preventing DLL binding
- ALLOWBIND linker option
- -ALLOWBIND linker option
- DLLs [C++], preventing binding
ms.assetid: 30e37e24-12e4-407e-988a-39d357403598
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 536fc4f43cf227491ecae53cb5960e42ff79e081
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713619"
---
# <a name="allowbind-prevent-dll-binding"></a>/ALLOWBIND (Zabránit vazbě knihoven DLL)

```
/ALLOWBIND[:NO]
```

## <a name="remarks"></a>Poznámky

/ALLOWBIND:No nastaví bit v hlavičce knihovny DLL, které označuje Bind.exe, že image se nemůže vázat. Možná nebudete chtít knihovnu DLL, pokud je digitálně podepsané (vazba zneplatní podpis).

Můžete upravit existující knihovny DLL pro funkce /ALLOWBIND s [/ALLOWBIND](../../build/reference/allowbind.md) – možnost nástroje EDITBIN.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Rozbalte **vlastnosti konfigurace**, **Linkeru**a vyberte **příkazového řádku**.

1. Zadejte `/ALLOWBIND:NO` do **další možnosti**.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)<br/>
[BindImage – funkce](/windows/desktop/api/imagehlp/nf-imagehlp-bindimage)<br/>
[BindImageEx – funkce](/windows/desktop/api/imagehlp/nf-imagehlp-bindimageex)