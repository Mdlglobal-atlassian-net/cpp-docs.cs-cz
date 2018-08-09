---
title: Přístup k informacím o verzi z programu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.version
dev_langs:
- C++
helpviewer_keywords:
- VerQueryValue
- version information, accessing from within programs
- GetFileVersionInfo
- version information
ms.assetid: 18622333-d9e8-4309-9465-677cd10c79b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 79520523ebeda2cb0260d1bc79d0b6b35d33aa23
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39646956"
---
# <a name="accessing-version-information-from-within-your-program"></a>Přístup k informacím o verzi z programu
### <a name="to-access-version-information-from-within-your-program"></a>Přístup k informacím o verzi z programu  
  
Pokud chcete přístup k informacím o verzi z programu, použijte [GetFileVersionInfo](http://msdn.microsoft.com/library/windows/desktop/ms647003.aspx) funkce a [Funkce VerQueryValue](http://msdn.microsoft.com/library/windows/desktop/ms647464.aspx) funkce.  
  
 Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Požadavky
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Editor informací o verzi](../windows/version-information-editor.md)   
 [Informace o verzi (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)