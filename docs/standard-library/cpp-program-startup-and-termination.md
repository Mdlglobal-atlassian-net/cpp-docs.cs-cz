---
title: "Spuštění a ukončení programu C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- C++ Standard Library, program startup and termination
- terminating execution
- Function Main procedures
- control text streams
- startup code, and C++ program termination
- main function, program startup
ms.assetid: f72c8f76-f507-4ddd-a270-7b60f4fed625
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b5092b4b21a1eea11559c30aa95c747816f098e2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="c-program-startup-and-termination"></a>Spuštění a ukončení programu C++
Programu C++ provádí stejné operace stejně v spuštění programu a ukončení programu a navíc několik více podle zde uvedeného programu C.  
  
 Před cíl prostředí volá funkci `main`, a po ukládá veškeré konstantní počáteční hodnoty zadáte v všechny objekty, které mají statické trvání, program spouští všechny zbývající konstruktory pro tyto statické objekty. Pořadí provádění není zadaný v rozmezí jednotky překladu, ale můžete nicméně předpokládat, že některé [iostreams](../standard-library/iostreams-conventions.md) objekty jsou správně inicializovat pro použití těchto statické konstruktory. Tyto řízení textových datových proudů jsou:  
  
-   [CIN](../standard-library/iostream.md#cin) – pro standardní vstup.  
  
-   [cout](../standard-library/iostream.md#cout) – pro standardní výstup.  
  
-   [cerr](../standard-library/iostream.md#cerr) – bez vyrovnávací paměti standardní chyba výstupu.  
  
-   [clog](../standard-library/iostream.md#clog) – pro uložená do vyrovnávací paměti standardní chyba výstupu.  
  
 Můžete také použít tyto objekty v rámci destruktory pro statické objekty, volá se během ukončení programu.  
  
 Stejně jako u C, vrácení z `main` nebo volání `exit` volá všechny funkce, které jsou registrovány `atexit` v obráceném pořadí z registru. Výjimka vyvolaná z těchto registrovaných funkce volá `terminate`.  
  
## <a name="see-also"></a>Viz také  
 [Přehled knihovny C++ Standard](../standard-library/cpp-standard-library-overview.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

