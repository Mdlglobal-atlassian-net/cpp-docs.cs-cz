---
title: "Postupy: Přidání nativní knihovny DLL do globální mezipaměti sestavení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- DLLs [C++], native
- GAC (global assembly cache), loading native DLLs
- native DLLs [C++]
ms.assetid: 25e8d78a-b197-4269-b4e9-237a544ab3c8
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ef839617e80c668cd74458c397085b1166fdd70c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-add-native-dll-to-global-assembly-cache"></a>Postupy: Přidání nativní knihovny DLL do globální mezipaměti sestavení
Můžete uvést nativní knihovny DLL (ne COM) do globální mezipaměti sestavení.  
  
## <a name="example"></a>Příklad  
 **/ ASSEMBLYLINKRESOURCE** umožňuje vložit nativní knihovny DLL do sestavení.  
  
 Další informace najdete v tématu [/ASSEMBLYLINKRESOURCE (vytvořit odkaz na prostředek rozhraní .NET Framework)](../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md).  
  
```  
/ASSEMBLYLINKRESOURCE:MyComponent.dll  
```  
  
## <a name="see-also"></a>Viz také  
 [Pomocí zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)