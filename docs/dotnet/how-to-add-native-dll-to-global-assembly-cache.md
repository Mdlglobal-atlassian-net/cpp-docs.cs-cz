---
title: 'Postupy: Přidání nativní knihovny DLL do globální mezipaměti sestavení'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], native
- GAC (global assembly cache), loading native DLLs
- native DLLs [C++]
ms.assetid: 25e8d78a-b197-4269-b4e9-237a544ab3c8
ms.openlocfilehash: 1b11ebfae704ca1529113a00b463df728c85fe60
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641360"
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