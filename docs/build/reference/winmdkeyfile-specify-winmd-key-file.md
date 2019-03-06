---
title: /WINMDFILE (Určení souboru klíče winmd)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.WINMDKeyFile
ms.assetid: 65d88fdc-fff9-49ea-8cfc-b2f408741734
ms.openlocfilehash: 33481033267d6470db38f0b64e76f5be7b4cbe2f
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57425403"
---
# <a name="winmdkeyfile-specify-winmd-key-file"></a>/WINMDFILE (Určení souboru klíče winmd)

Určuje klíč nebo dvojici klíčů k podepsání souboru Windows Runtime Metadata (.winmd).

```
/WINMDKEYFILE:filename
```

## <a name="remarks"></a>Poznámky

Vypadá podobně jako [/keyfile](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) – možnost linkeru, které platí pro soubor winmd.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **Linkeru** složky.

1. Vyberte **metadat Windows** stránku vlastností.

1. V **soubor klíče metadat Windows** zadejte umístění souboru.

## <a name="see-also"></a>Viz také:

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)
