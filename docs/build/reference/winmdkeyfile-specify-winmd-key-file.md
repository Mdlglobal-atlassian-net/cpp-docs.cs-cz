---
title: /WINMDFILE (Určení souboru klíče winmd)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.WINMDKeyFile
ms.assetid: 65d88fdc-fff9-49ea-8cfc-b2f408741734
ms.openlocfilehash: 4b0c847bc5be6c73b78af4aa15b0074c712cc840
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2019
ms.locfileid: "57820400"
---
# <a name="winmdkeyfile-specify-winmd-key-file"></a>/WINMDFILE (Určení souboru klíče winmd)

Určuje klíč nebo dvojici klíčů k podepsání souboru Windows Runtime Metadata (.winmd).

```
/WINMDKEYFILE:filename
```

## <a name="remarks"></a>Poznámky

Vypadá podobně jako [/keyfile](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) – možnost linkeru, které platí pro soubor winmd.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **Linkeru** složky.

1. Vyberte **metadat Windows** stránku vlastností.

1. V **soubor klíče metadat Windows** zadejte umístění souboru.

## <a name="see-also"></a>Viz také:

[Odkaz na MSVC linkeru](linking.md)<br/>
[Možnosti Linkeru MSVC](linker-options.md)
