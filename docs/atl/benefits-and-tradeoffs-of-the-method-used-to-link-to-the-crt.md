---
title: Výhody a kompromisy metodu použitou k propojení CRT | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- _ATL_MIN_CRT macro
ms.assetid: 49b485f7-9487-49e4-b12a-0f710b620e2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b2835e88da11b8d8332226080eb860afd41c0702
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32355384"
---
# <a name="benefits-and-tradeoffs-of-the-method-used-to-link-to-the-crt"></a>Výhody a kompromisy metodu použitou k propojení CRT
Projekt můžete propojit s CRT dynamicky nebo staticky. Následující tabulka popisuje výhody a kompromisy účastnící se výběr jakou metodu použít.  
  
|Metoda|Výhody|Kompromis|  
|------------|-------------|--------------|  
|Staticky propojení s CRT<br /><br /> (**Runtime Library** nastavena na **jednovláknové**)|DLL Knihovny CRT není potřeba v systému, kde se spustí bitovou kopii.|O 25K spuštění kódu se přidá do bitové kopie, podstatně zvýšení jeho velikost.|  
|Dynamické propojování CRT<br /><br /> (**Runtime Library** nastavena na **Vícevláknová**)|Bitové kopie nevyžaduje CRT spouštěcí kód, proto je mnohem menší.|CRT knihovny DLL musí být na systémy bitovou kopii.|  
  
 Téma [propojení s CRT v projektu knihovny ATL](../atl/linking-to-the-crt-in-your-atl-project.md) popisuje, jak můžete vybrat způsob, ve kterém má být propojen s CRT.  
  
## <a name="see-also"></a>Viz také  
 [Programování s použitím knihovny ATL a běhového kódu jazyka C](../atl/programming-with-atl-and-c-run-time-code.md)   
 [Knihovny DLL a chování běhové knihovny jazyka Visual C++](../build/run-time-library-behavior.md)   
 [Funkce knihovny CRT](../c-runtime-library/crt-library-features.md)

