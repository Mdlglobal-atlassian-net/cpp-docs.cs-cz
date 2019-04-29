---
title: Obcházení výjimek vyvolaných objektů COM sestavených s volbou-clr
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], CLR shutdown exceptions
- /clr compiler option [C++], CLR shutdown exceptions
- mixed assemblies [C++], CLR shutdown exceptions
- /clr compiler option [C++], COM objects
- interoperability [C++], CLR shutdown exceptions
- CLR shutdown exceptions [C++]
ms.assetid: 41249d83-4b51-4e46-866f-27f475f2498c
ms.openlocfilehash: bafcfb4e8a8abfecc8491220202b63971bef1ac8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393828"
---
# <a name="avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr"></a>Obcházení výjimek na vypnutí CLR při spotřebě objektů COM sestavených s volbou /clr

Jakmile common language runtime (CLR) přejde do režimu vypnutí, nativní funkce mají omezený přístup ke službám CLR. Při pokusu o volání vydání na objekt modelu COM zkompilovaná **/CLR**, CLR přejde do nativního kódu a pak zpátky přechody do spravovaného kódu pro volání IUnknown::Release (který je definován ve spravovaném kódu). Modul CLR brání volání zpět do spravovaného kódu, protože se nachází v režimu vypnutí.

Chcete-li tento problém vyřešit, ujistěte se, že destruktory volat z verze metody obsahovat pouze nativního kódu.

## <a name="see-also"></a>Viz také:

[Smíšená (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md)
