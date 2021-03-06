---
title: /WINMDDELAYSIGN (Částečné podepsání souboru winmd)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.WINMDDelaySign
ms.assetid: 445cd602-62cb-400a-8e3a-4beb6572724d
ms.openlocfilehash: 5e6eab3fbc40543b634f03da826d3bd3477b9623
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316597"
---
# <a name="winmddelaysign-partially-sign-a-winmd"></a>/WINMDDELAYSIGN (Částečné podepsání souboru winmd)

Umožňuje částečný podpis souboru Windows Runtime Metadata (.winmd) tak, že vložíte veřejný klíč v souboru.

```
/WINMDDELAYSIGN[:NO]
```

## <a name="remarks"></a>Poznámky

Vypadá podobně jako [/delaysign](delaysign-partially-sign-an-assembly.md) – možnost linkeru, které platí pro soubor winmd. Použití **winmddelaysign** Pokud chcete umístit pouze veřejný klíč v souboru .winmd. Ve výchozím nastavení, linker funguje jakoby **/winmddelaysign: No** byly zadány; to znamená, ho není podepsání souboru winmd.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **Linkeru** složky.

1. Vyberte **metadat Windows** stránku vlastností.

1. V **odložený podpis metadat Windows** rozevíracího seznamu vyberte požadovanou možnost.

## <a name="see-also"></a>Viz také:

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)
