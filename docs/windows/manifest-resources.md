---
title: Manifest prostředků (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- manifest resources [C++]
- resources [C++], manifest
ms.assetid: 8615334c-22a0-44c0-93e0-5924528c9917
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2da93d1baaf95799c7ef68d6cc854d554fbe6c47
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429562"
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