---
title: Propojení projektu ATL s Knihovnami CRT | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fad8209c680a782bd9800215e1e0affc7e2a98c8
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852494"
---
# <a name="linking-to-the-crt-in-your-atl-project"></a>Propojení projektu ATL s Knihovnami CRT
[C Run-Time Libraries](../c-runtime-library/crt-library-features.md) (CRT) poskytují mnoho užitečných funkcí, které umožňují programování mnohem jednodušší během vývoje knihovny ATL. Všechny projekty knihovny ATL propojení ke knihovně CRT. Můžete zobrazit výhodám a nevýhodám propojení metody v [výhody a nevýhody metody použité k připojení k CRT](../atl/benefits-and-tradeoffs-of-the-method-used-to-link-to-the-crt.md).  
  
## <a name="effects-of-linking-to-the-crt-on-your-program-image"></a>Účinky připojení k CRT na bitové kopie programu  
 Pokud staticky propojíte CRT, kód z CRT, nachází ve spustitelné bitové kopie a není potřeba mít knihovny DLL CRT, která je k dispozici v systému pro spuštění bitové kopie. Pokud dynamicky propojíte CRT, odkazy na kód v DLL Knihovně CRT jsou umístěny v bitové kopie, ale ne samotný kód. V pořadí pro vaši image pro spuštění na daném systému musí být CRT knihovny DLL v daném systému. I když dynamicky propojíte CRT, možná zjistíte, že nějaký kód může být staticky propojené (například `DllMainCRTStartup`).  
  
 Při propojování vaší image je explicitně nebo implicitně zadat vstupní bod, který operační systém zavolá po načtení obrázku. Pro knihovny DLL, je výchozí vstupní bod `DllMainCRTStartup`. Pro soubor EXE, je `WinMainCRTStartup`. Můžete přepsat výchozí možnost linker/Entry. Poskytuje implementaci pro CRT `DllMainCRTStartup`, `WinMainCRTStartup`, a `wWinMainCRTStartup` (vstupní bod kódu Unicode pro EXE). Tyto poskytované CRT vstupní body volání konstruktorů pro globální objekty a inicializujte další datové struktury, které jsou používány některé funkce CRT. Tento kód při spuštění přidá přibližně 25 tisíc do bitové kopie, pokud je staticky propojena. Pokud je dynamicky propojena, většina kódu je v knihovně DLL tak zůstane malá velikost vaší image.  
  
 Další informace najdete v tématu linkeru [/Entry (Symbol vstupního bodu)](../build/reference/entry-entry-point-symbol.md).  
  
## <a name="optimization-options"></a>Možnosti optimalizace  
 Pomocí možnosti linkeru NOWIN98 můžete dál snížit ovládacího prvku ATL výchozí pomocí 10 tisíc na expense z zvýšit čas v systémech Windows 98 načítání. Další informace o tvorbě možnosti, najdete v části [/OPT (optimalizace)](../build/reference/opt-optimizations.md).  
  
## <a name="see-also"></a>Viz také  
 [Programování s použitím knihovny ATL a běhového kódu jazyka C](../atl/programming-with-atl-and-c-run-time-code.md)   
 [Knihovny DLL a chování běhové knihovny v jazyce Visual C++](../build/run-time-library-behavior.md)

