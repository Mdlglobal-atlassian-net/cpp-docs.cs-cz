---
title: 'Postupy: Přidání nativní knihovny DLL do globální mezipaměti sestavení | Microsoft Docs'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], native
- GAC (global assembly cache), loading native DLLs
- native DLLs [C++]
ms.assetid: 25e8d78a-b197-4269-b4e9-237a544ab3c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b7363de172eabc664bcde1e3bf42f8cc499e4251
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
 [Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)