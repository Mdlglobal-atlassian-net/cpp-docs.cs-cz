---
title: -Winmddelaysign (částečné podepsání winmd) souboru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.WINMDDelaySign
dev_langs:
- C++
ms.assetid: 445cd602-62cb-400a-8e3a-4beb6572724d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b31f6ae5baf9aadbb40b4b45f532b344b6b2e037
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723850"
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