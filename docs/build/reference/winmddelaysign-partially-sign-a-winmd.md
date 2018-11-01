---
title: /WINMDDELAYSIGN (Částečné podepsání souboru winmd)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.WINMDDelaySign
ms.assetid: 445cd602-62cb-400a-8e3a-4beb6572724d
ms.openlocfilehash: 367dbe0e638e3748f259f22c1e3536bbd7398272
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605995"
---
# <a name="winmddelaysign-partially-sign-a-winmd"></a>/WINMDDELAYSIGN (Částečné podepsání souboru winmd)

Umožňuje částečný podpis souboru Windows Runtime Metadata (.winmd) tak, že vložíte veřejný klíč v souboru.

```
/WINMDDELAYSIGN[:NO]
```

## <a name="remarks"></a>Poznámky

Vypadá podobně jako [/delaysign](../../build/reference/delaysign-partially-sign-an-assembly.md) – možnost linkeru, které platí pro soubor winmd. Použití **winmddelaysign** Pokud chcete umístit pouze veřejný klíč v souboru .winmd. Ve výchozím nastavení, linker funguje jakoby **/winmddelaysign: No** byly zadány; to znamená, ho není podepsání souboru winmd.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **Linkeru** složky.

1. Vyberte **metadat Windows** stránku vlastností.

1. V **odložený podpis metadat Windows** rozevíracího seznamu vyberte požadovanou možnost.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)