---
title: Obcházení výjimek vyvolaných objektů COM sestavených s volbou-clr | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interop [C++], CLR shutdown exceptions
- /clr compiler option [C++], CLR shutdown exceptions
- mixed assemblies [C++], CLR shutdown exceptions
- /clr compiler option [C++], COM objects
- interoperability [C++], CLR shutdown exceptions
- CLR shutdown exceptions [C++]
ms.assetid: 41249d83-4b51-4e46-866f-27f475f2498c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 687585d0b25c64f5575646de3cd4823e0a89988e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408969"
---
# <a name="avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr"></a>Obcházení výjimek na vypnutí CLR při spotřebě objektů COM sestavených s volbou /clr

Jakmile common language runtime (CLR) přejde do režimu vypnutí, nativní funkce mají omezený přístup ke službám CLR. Při pokusu o volání vydání na objekt modelu COM zkompilovaná **/CLR**, CLR přejde do nativního kódu a pak zpátky přechody do spravovaného kódu pro volání IUnknown::Release (který je definován ve spravovaném kódu). Modul CLR brání volání zpět do spravovaného kódu, protože se nachází v režimu vypnutí.

Chcete-li tento problém vyřešit, ujistěte se, že destruktory volat z verze metody obsahovat pouze nativního kódu.

## <a name="see-also"></a>Viz také

[Smíšená (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md)