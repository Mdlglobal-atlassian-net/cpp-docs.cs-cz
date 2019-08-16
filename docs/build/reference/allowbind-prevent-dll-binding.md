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
ms.openlocfilehash: d963a7145ab2e8c8872dc21c485bdc8f877b0b76
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493145"
---
# <a name="allowbind-prevent-dll-binding"></a>/ALLOWBIND (Zabránit vazbě knihoven DLL)

```
/ALLOWBIND[:NO]
```

## <a name="remarks"></a>Poznámky

/ALLOWBIND: v záhlaví knihovny DLL nejsou nastaveny žádné bity, které označují, že se k souboru BIND. exe nepovoluje svázat. Je možné, že nebudete mít vazbu na knihovnu DLL, pokud byla digitálně podepsaná (vazba zruší platnost podpisu).

Existující knihovnu DLL pro funkci/ALLOWBIND můžete upravit pomocí možnosti [/ALLOWBIND](allowbind.md) nástroje nástroje Editbin.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Rozbalte položku **Vlastnosti konfigurace**, **linker**a vyberte **příkazový řádek**.

1. Zadejte `/ALLOWBIND:NO` **Další možnosti**.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)<br/>
[BindImage – funkce](/windows/win32/api/imagehlp/nf-imagehlp-bindimage)<br/>
[BindImageEx – funkce](/windows/win32/api/imagehlp/nf-imagehlp-bindimageex)
