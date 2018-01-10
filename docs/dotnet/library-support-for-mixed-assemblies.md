---
title: "Podpora knihovny pro smíšená sestavení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- msvcm90[d].dll
- mixed assemblies [C++], library support
- msvcmrt[d].lib
- libraries [C++], mixed assemblies
ms.assetid: 1229595c-9e9d-414d-b018-b4e4c727576d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9b3bc50416eceac64c134a31a4d7384e33db69b4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="library-support-for-mixed-assemblies"></a>Podpora knihovny pro smíšená sestavení
Podporuje použití standardní knihovny C++, knihovny (CRT), Visual C++ ATL a MFC pro aplikace, kompilovat s [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md). To umožňuje existující aplikace, které používají tyto knihovny používat taky funkce rozhraní .NET Framework.  
  
 Tato podpora zavádí následující nové knihovny DLL a import:  
  
-   Pokud kompilace s volbou/CLR Msvcmrt [d] .lib. Smíšená sestavení odkazuje na tato knihovna importu.  
  
-   Msvcm90 [d] .dll a .lib Msvcurt [d] Pokud kompilace s volbou/CLR: pure. Knihovny DLL je kombinované sestavení poskytující spravované podpory čas spuštění C (CRT) a je součástí spravované sestavení nainstalované v globální mezipaměti sestavení (GAC). Čistá sestavení odkaz na tento knihovny importu a skončí vázán na Msvcm90.dll.  
  
 Tato podpora zajišťuje několik souvisejících výhod:  
  
-   CRT a standardní knihovny C++ jsou k dispozici pro smíšený i čistý kód. CRT a standardní knihovny C++ poskytuje nejsou ověřitelný; Nakonec voláními stále směrují stejné CRT a standardní knihovny C++ jako používáte z nativního kódu.  
  
-   Opravte jednotná zpracování výjimek v čisté a smíšené bitové kopie.  
  
-   Statické inicializace proměnných jazyka C++ v čisté a smíšené bitové kopie.  
  
-   Podpora pro proměnné na AppDomain a na proces ve spravovaném kódu.  
  
-   Řešení problémů zámek zavaděče použité smíšených knihoven DLL kompilovat v aplikaci Visual Studio 2003 a starších verzích.  
  
 Kromě toho tato podpora představuje následující omezení:  
  
-   Je podporován pouze model CRT DLL (pro kód kompilován s/CLR nebo/CLR: pure).  
  
-   Pokud tyto objekty používají knihovny jazyka Visual C++ (protože všechny objekty musí být čistý v bitové kopii čistý) není možné kombinovat čisté a smíšené objekty do jediného image. Pokud to uděláte, zobrazí se chyba propojování.  
  
 Common language runtime (CLR) by měl aktualizovat na aktuální verzi jako není zaručena pro práci s předchozími verzemi. Kód vytvořené s nástroji tyto změny se nespustí na verze CLR 1.x.  
  
## <a name="see-also"></a>Viz také  
 [Smíšená (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md)