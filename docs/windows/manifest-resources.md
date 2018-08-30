---
title: Prostředky manifestu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- manifest resources
- resources [Visual Studio], manifest
ms.assetid: 8615334c-22a0-44c0-93e0-5924528c9917
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e1520cd301fa46fb4d9521fd6d4180ebd3710f67
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43218247"
---
# <a name="manifest-resources"></a>Manifest prostředků

Prostředky manifestu jsou soubory formátu XML, které popisují závislosti, které aplikace používá. Například v sadě Visual Studio manifestu soubor generované průvodcem MFC definuje které verze 5.0 nebo 6.0, Windows běžný ovládací prvek aplikace by měla používat knihovny DLL:

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

K zobrazení verze a typ informací obsažených v manifestu prostředek, můžete otevřít soubor v prohlížeči XML, nebo v sadě Visual Studio [textový Editor](https://msdn.microsoft.com/508e1f18-99d5-48ad-b5ad-d011b21c6ab1). Další informace najdete v tématu [otevření prostředku manifestu v editoru sady Visual Studio Text](../windows/how-to-open-a-manifest-resource.md).

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Walkthrough: Using Resources for Localization with ASP.NET](https://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).

## <a name="limitations"></a>Omezení

Můžete mít jenom jeden prostředek manifestu na modul.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Ovládací prvky](../mfc/controls-mfc.md)  
[Práce se zdrojovými soubory](../windows/working-with-resource-files.md)