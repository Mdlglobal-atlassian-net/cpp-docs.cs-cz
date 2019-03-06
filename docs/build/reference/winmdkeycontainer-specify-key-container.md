---
title: /WINMDKEYCONTAINER (Určení kontejneru klíče)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.WINMDKEYCONTAINER
ms.assetid: c2fc44dc-7cb5-42b9-897f-1b124928f2f7
ms.openlocfilehash: 5424b928f80bf73aedb731f835b72d20bfd0c4a2
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416589"
---
# <a name="winmdkeycontainer-specify-key-container"></a>/WINMDKEYCONTAINER (Určení kontejneru klíče)

Určuje klíčový kontejner k podepsání souboru metadat Windows (.winmd).

```
/WINMDKEYCONTAINER:name
```

## <a name="remarks"></a>Poznámky

Vypadá podobně jako [/keycontainer](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md) – možnost linkeru, která se použije na soubor (.winmd).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **Linkeru** složky.

1. Vyberte **metadat Windows** stránku vlastností.

1. V **kontejneru klíčů metadat Windows** zadejte umístění.

## <a name="see-also"></a>Viz také:

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)
