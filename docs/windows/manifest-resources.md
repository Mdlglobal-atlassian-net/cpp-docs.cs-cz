---
title: "Prostředky manifestu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- manifest resources
- resources [Visual Studio], manifest
ms.assetid: 8615334c-22a0-44c0-93e0-5924528c9917
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 56a41a7901e41f4c76fbb9fcbf5930ec97c3b866
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="manifest-resources"></a>Manifest prostředků
Prostředky manifestu jsou soubory XML, které popisují závislosti, které aplikace používá. Například v sadě Visual Studio, MFC generované v Průvodci souboru manifestu definuje což Windows běžného ovládacího prvku by aplikace měla použít knihovny DLL, verze 5.0 nebo 6.0:  
  
```  
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
  
 Pro aplikaci systému Windows XP nebo Windows Vista, prostředku manifestu nejen Určuje, že aplikace použijte nejnovější verzi běžné ovládací prvky Windows (verze 6.0, jak je vidět výše), ale také podporuje [Syslink řízení](http://msdn.microsoft.com/library/windows/desktop/bb760706).  
  
 Pokud chcete zobrazit verzi a typ informací obsažených v prostředku manifestu, můžete otevřít soubor v prohlížeč formátu XML nebo v sadě Visual Studio [textového editoru](http://msdn.microsoft.com/en-us/508e1f18-99d5-48ad-b5ad-d011b21c6ab1). Další informace najdete v tématu [otevření prostředku manifestu v editoru textu sady Visual Studio](../windows/how-to-open-a-manifest-resource.md).  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace o ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a prostředky řetězce přiřazení k vlastnosti, najdete v části [návod: použití prostředků pro lokalizaci pomocí technologie ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
## <a name="limitations"></a>Omezení  
 Může mít pouze jeden prostředku manifestu na modul.  
  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky](../mfc/controls-mfc.md)   
 [Práce se zdrojovými soubory](../windows/working-with-resource-files.md)