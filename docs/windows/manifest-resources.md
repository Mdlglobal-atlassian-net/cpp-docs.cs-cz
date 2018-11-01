---
title: Prostředky manifestu (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- manifest resources [C++]
- resources [C++], manifest
ms.assetid: 8615334c-22a0-44c0-93e0-5924528c9917
ms.openlocfilehash: 081fd12a86c31973c7856ca7b9f3fcb129e2eb81
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578279"
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

K zobrazení verze a typ informací obsažených v manifestu prostředek, můžete otevřít soubor v prohlížeči XML nebo textovém editoru sady Visual Studio. Další informace najdete v tématu [otevření prostředku manifestu v editoru sady Visual Studio Text](../windows/how-to-open-a-manifest-resource.md).

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*.

## <a name="limitations"></a>Omezení

Můžete mít jenom jeden prostředek manifestu na modul.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Ovládací prvky](../mfc/controls-mfc.md)<br/>
[Práce se zdrojovými soubory](../windows/working-with-resource-files.md)