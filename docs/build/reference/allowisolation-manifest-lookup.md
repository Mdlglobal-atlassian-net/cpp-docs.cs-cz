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
ms.openlocfilehash: fe76e0d40a2a19a002136a7e095875ad2903d434
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818450"
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

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **soubor manifestu** stránku vlastností.

1. Upravit **Povolit izolaci** vlastnost.

## <a name="see-also"></a>Viz také:

[Odkaz na MSVC linkeru](linking.md)<br/>
[Možnosti Linkeru MSVC](linker-options.md)
