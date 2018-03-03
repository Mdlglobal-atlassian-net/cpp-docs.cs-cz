---
title: "Propojení s CRT ve vašem projektu knihovny ATL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DllMainCRTStartup
- wWinMainCRTStartup
- WinMainCRTStartup
dev_langs:
- C++
helpviewer_keywords:
- CRT, linking with ATL
- WinMainCRTStartup method
- DllMainCRTStartup method
- wWinMainCRTStartup method
- ATL, C Run-Time library (CRT)
ms.assetid: 650957ae-362c-4ecf-8b03-5d49138e8b5b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 631426fece3960303d67d8929e99c404beaab998
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="linking-to-the-crt-in-your-atl-project"></a>Propojení s CRT ve vašem projektu knihovny ATL
[Běhové knihovny jazyka C](../c-runtime-library/crt-library-features.md) (CRT) poskytují mnoho užitečné funkce, které můžou programování mnohem snazší během vývoje ATL. Všechny projekty knihovny ATL propojit knihovny CRT. Uvidíte výhody a nevýhody propojení metoda v [výhody a poměry metoda použitá pro odkaz na CRT](../atl/benefits-and-tradeoffs-of-the-method-used-to-link-to-the-crt.md).  
  
## <a name="effects-of-linking-to-the-crt-on-your-program-image"></a>Důsledky propojení s CRT na bitové kopie programu  
 Pokud staticky propojit CRT kód z CRT je umístěn ve vaší spustitelné bitové kopie a není potřeba mít DLL Knihovny CRT existuje v systému pro spuštění bitové kopie. Pokud dynamicky propojit CRT odkazů na kód v knihovně DLL CRT jsou umístěny v bitové kopii, ale ne samotný kód. Aby bitové kopie na daný systém spouštět musí být DLL Knihovny CRT na daný systém. I když dynamicky propojíte CRT, můžete zjistit, že některé kódu můžete staticky propojené (například **DllMainCRTStartup**).  
  
 Při propojení vaší image je explicitně nebo implicitně zadat vstupní bod, který operační systém zavolá po načtení bitovou kopii. Pro knihovny DLL, je výchozí vstupní bod **DllMainCRTStartup**. EXE, je **WinMainCRTStartup**. Můžete přepsat výchozí s parametrem/Entry linkeru. Poskytuje implementaci pro CRT **DllMainCRTStartup**, **WinMainCRTStartup**, a **wWinMainCRTStartup** (vstupní bod kódování Unicode pro EXE). Tyto zadaný CRT vstupní body volání konstruktory na globální objekty a inicializace jiné datové struktury, které jsou používány některé funkce CRT. Tento kód pro spuštění přidá o 25 kB do bitové kopie, pokud je staticky propojený. Pokud je propojená dynamicky, je většina kódu v knihovně DLL, takže zůstává malá velikost vaší image.  
  
 Další informace najdete v tématu linkeru [/Entry (Symbol vstupního bodu)](../build/reference/entry-entry-point-symbol.md).  
  
## <a name="optimization-options"></a>Možnosti optimalizace  
 Pomocí možnosti linkeru /OPT:NOWIN98 můžete dál snížit prvku výchozí ATL podle 10 tisíc v expense z vyšší načítání čas v systémech Windows 98. Další informace o propojení možnosti najdete v tématu [/OPT (optimalizace)](../build/reference/opt-optimizations.md).  
  
## <a name="see-also"></a>Viz také  
 [Programování s použitím knihovny ATL a běhového kódu jazyka C](../atl/programming-with-atl-and-c-run-time-code.md)   
 [Knihovny DLL a chování běhové knihovny v jazyce Visual C++](../build/run-time-library-behavior.md)

