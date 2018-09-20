---
title: 'Postupy: Přidání nativní knihovny DLL do globální mezipaměti sestavení | Dokumentace Microsoftu'
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
ms.openlocfilehash: 74b24b96b28d8c5805a075a5ac1eee41173fc427
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431993"
---
# <a name="how-to-add-native-dll-to-global-assembly-cache"></a>Postupy: Přidání nativní knihovny DLL do globální mezipaměti sestavení

Nativní knihovnu DLL (ne COM) můžete umístit do globální mezipaměti sestavení.

## <a name="example"></a>Příklad

**/ ASSEMBLYLINKRESOURCE** umožňuje vložení do sestavení nativní knihovnu DLL.

Další informace najdete v tématu [/ASSEMBLYLINKRESOURCE (odkaz na prostředek rozhraní .NET Framework)](../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md).

```
/ASSEMBLYLINKRESOURCE:MyComponent.dll
```

## <a name="see-also"></a>Viz také

[Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)