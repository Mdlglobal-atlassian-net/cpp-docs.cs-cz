---
title: /ALLOWISOLATION (vyhledání manifestu)
ms.date: 11/04/2016
f1_keywords:
- /ALLOWISOLATION
- VC.Project.VCLinkerTool.AllowIsolation
helpviewer_keywords:
- -ALLOWISOLATION linker option
- /ALLOWISOLATION linker option
ms.assetid: 6d41851e-b3c1-4bdf-beaa-031773089d6f
ms.openlocfilehash: 2309a237ccd7ccb18a11b180c4f91bbf9055d70b
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418331"
---
# <a name="allowisolation-manifest-lookup"></a>/ALLOWISOLATION (vyhledání manifestu)

Určuje chování při vyhledávání manifestu.

## <a name="syntax"></a>Syntaxe

```
/ALLOWISOLATION[:NO]
```

## <a name="remarks"></a>Poznámky

**/ALLOWISOLATION:No** označuje knihovny DLL se načítají, jako kdyby byl žádný manifest a způsobí, že nastaví linker `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` bit ve volitelné hlavičce `DllCharacteristics` pole.

**/ ALLOWISOLATION** způsobí, že operační systém k vyhledání a načtení manifestu.

**/ ALLOWISOLATION** je výchozí nastavení.

Izolace zakázán pro spustitelný soubor, zavaděč Windows nebude pokoušet najít manifest aplikace pro nově vytvořený procesu. Nový proces nebude mít výchozí aktivační kontext, i v případě manifestu do spustitelného souboru nebo umístěný ve stejném adresáři jako spustitelný soubor s názvem <em>název spustitelného souboru</em>**. exe.manifest**.

Další informace najdete v tématu [referenční příručka souborů manifestu](/windows/desktop/SbsCs/manifest-files-reference).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **soubor manifestu** stránku vlastností.

1. Upravit **Povolit izolaci** vlastnost.

## <a name="see-also"></a>Viz také:

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)
