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
ms.openlocfilehash: 7c799f3d44428643bccc2869255ffa4e9d194d70
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493140"
---
# <a name="allowisolation-manifest-lookup"></a>/ALLOWISOLATION (vyhledání manifestu)

Určuje chování při vyhledávání manifestu.

## <a name="syntax"></a>Syntaxe

```
/ALLOWISOLATION[:NO]
```

## <a name="remarks"></a>Poznámky

**/ALLOWISOLATION: No** označuje, že knihovny DLL jsou načteny, jako kdyby nebyl žádný manifest, a způsobí `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` , že linker nastaví bit v `DllCharacteristics` poli volitelné hlavičky.

**/ALLOWISOLATION** způsobí, že operační systém provede vyhledání a načtení manifestu.

Výchozí hodnota je **/ALLOWISOLATION** .

Pokud je izolace pro spustitelný soubor zakázaná, zavaděč Windows se nebude pokoušet najít manifest aplikace pro nově vytvořený proces. Nový proces nebude mít výchozí aktivační kontext, a to ani v případě, že ve spustitelném souboru existuje manifest, který je umístěn ve stejném adresáři jako spustitelný soubor s názvem <em>executable-Name</em> **. exe. manifest**.

Další informace najdete v referenčních informacích k [souborům manifestu](/windows/win32/SbsCs/manifest-files-reference).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte stránku vlastností**souboru manifestu** **linkeru** >  **vlastnosti** > konfigurace.

1. Upravte vlastnost **Allow izolace** .

## <a name="see-also"></a>Viz také:

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)
