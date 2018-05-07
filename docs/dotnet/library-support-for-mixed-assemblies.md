---
title: Podpora knihovny pro smíšená sestavení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- msvcm90[d].dll
- mixed assemblies [C++], library support
- msvcmrt[d].lib
- libraries [C++], mixed assemblies
ms.assetid: 1229595c-9e9d-414d-b018-b4e4c727576d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9fbb660d3f62c255ab81c7e77fef6c5d042efb12
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="library-support-for-mixed-assemblies"></a>Podpora knihovny pro smíšená sestavení
Podporuje použití standardní knihovny C++, knihovny (CRT), Visual C++ ATL a MFC pro aplikace, kompilovat s [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md). To umožňuje existující aplikace, které používají tyto knihovny používat taky funkce rozhraní .NET Framework.  
  
 Tato podpora zavádí následující nové knihovny DLL a import:  
  
-   Pokud kompilace s volbou/CLR Msvcmrt [d] .lib. Smíšená sestavení odkazuje na tato knihovna importu.  
  
 Tato podpora zajišťuje několik souvisejících výhod:  
  
-   CRT a standardní knihovny C++ jsou k dispozici pro smíšený i čistý kód. CRT a standardní knihovny C++ poskytuje nejsou ověřitelný; Nakonec voláními stále směrují stejné CRT a standardní knihovny C++ jako používáte z nativního kódu.  
  
-   Opravte jednotná zpracování výjimek v čisté a smíšené bitové kopie.  
  
-   Statické inicializace proměnných jazyka C++ v čisté a smíšené bitové kopie.  
  
-   Podpora pro proměnné na AppDomain a na proces ve spravovaném kódu.  
  
-   Řešení problémů zámek zavaděče použité smíšených knihoven DLL kompilovat v aplikaci Visual Studio 2003 a starších verzích.  
  
 Kromě toho tato podpora představuje následující omezení:  
  
-   Pro zkompilování kódu s/CLR je podporován pouze model CRT DLL.  
  
 Common language runtime (CLR) by měl aktualizovat na aktuální verzi jako není zaručena pro práci s předchozími verzemi. Kód vytvořené s nástroji tyto změny se nespustí na verze CLR 1.x.  
  
## <a name="see-also"></a>Viz také  
 [Smíšená (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md)