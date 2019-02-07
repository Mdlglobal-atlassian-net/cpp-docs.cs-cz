---
title: Prostředky manifestu (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- manifest resources [C++]
- resources [C++], manifest
- resources [C++], opening
ms.assetid: 8615334c-22a0-44c0-93e0-5924528c9917
ms.openlocfilehash: 2d135cb2d512313f107eef7e95ec90d7972b68b4
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55850187"
---
# <a name="manifest-resources-c"></a>Prostředky manifestu (C++)

Prostředky manifestu v desktopové projekty C++, jsou soubory XML, které popisují závislosti, které aplikace používá. Například v sadě Visual Studio manifestu soubor generované průvodcem MFC definuje které verze 5.0 nebo 6.0, Windows běžný ovládací prvek aplikace by měla používat knihovny DLL:

```xml
<description>Your app description here</description>
<dependency>
    <dependentAssembly>
        <assemblyIdentity
            type="win32"
            name="Microsoft.Windows.Common-Controls"
            version="6.0.0.0"
            processorArchitecture="X86"
            publicKeyToken="6595b64144ccf1df"
            language="*"
        />
    </dependentAssembly>
</dependency>
```

Pro aplikace Windows XP nebo Windows Vista prostředku manifestu nejen Určuje, že aplikace používat nejnovější verzi Windows běžných ovládacích prvků (verze 6.0, jak je znázorněno výše), ale také podporuje [ovládací prvek Syslink](/windows/desktop/Controls/syslink-overview).

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*.

K zobrazení verze a typ informací obsažených v manifestu prostředek, můžete otevřít soubor v prohlížeči XML nebo textovém editoru sady Visual Studio. Otevření prostředku manifestu z [zobrazení prostředků](../windows/resource-view-window.md), prostředek se otevře v binárním formátu. Chcete-li zobrazit obsah manifestu prostředek ve formátu více zobrazitelné, je nutné otevřít prostředek z **Průzkumníka řešení**.

## <a name="to-open-a-manifest-resource-in-the-text-editor"></a>K otevření prostředku manifestu v textovém editoru

1. S projektem open v **Průzkumníka řešení**, rozbalte **soubory prostředků** složky.

1. Poklikejte na soubor .manifest.

   Se otevře v manifestu prostředek **textový Editor**.

## <a name="to-open-a-manifest-resource-in-another-editor"></a>K otevření prostředku manifestu v jiném editoru

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na soubor .manifest a zvolte **otevřít v programu...**  z místní nabídky.

1. V **otevřít v** dialogovém okně zadejte editor, který chcete použít a vyberte **otevřít**.

## <a name="limitations"></a>Omezení

Můžete mít jenom jeden prostředek manifestu na modul.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Ovládací prvky](../mfc/controls-mfc.md)<br/>
[Práce se zdrojovými soubory](../windows/working-with-resource-files.md)