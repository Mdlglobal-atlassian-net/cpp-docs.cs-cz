---
title: "Výhody a kompromisy metodu použitou k propojení CRT | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: _ATL_MIN_CRT macro
ms.assetid: 49b485f7-9487-49e4-b12a-0f710b620e2b
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 13b4ef1599a5f59e1f01d551552cb03265e939ac
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
