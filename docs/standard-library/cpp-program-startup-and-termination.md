---
title: Spuštění a ukončení programu C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- C++ Standard Library, program startup and termination
- terminating execution
- Function Main procedures
- control text streams
- startup code, and C++ program termination
- main function, program startup
ms.assetid: f72c8f76-f507-4ddd-a270-7b60f4fed625
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eec5c6d72152f2aaea8d77df7ca65bf5f5f5565b
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="c-program-startup-and-termination"></a>Spuštění a ukončení programu C++

Programu C++ provádí stejné operace stejně v spuštění programu a ukončení programu a navíc několik více podle zde uvedeného programu C.

Před cíl prostředí volá funkci `main`, a po ukládá veškeré konstantní počáteční hodnoty zadáte v všechny objekty, které mají statické trvání, program spouští všechny zbývající konstruktory pro tyto statické objekty. Pořadí provádění není zadaný v rozmezí jednotky překladu, ale můžete nicméně předpokládat, že některé [iostreams](../standard-library/iostreams-conventions.md) objekty jsou správně inicializovat pro použití těchto statické konstruktory. Tyto řízení textových datových proudů jsou:

- [CIN](../standard-library/iostream.md#cin) – pro standardní vstup.

- [cout](../standard-library/iostream.md#cout) – pro standardní výstup.

- [cerr](../standard-library/iostream.md#cerr) – bez vyrovnávací paměti standardní chyba výstupu.

- [clog](../standard-library/iostream.md#clog) – pro uložená do vyrovnávací paměti standardní chyba výstupu.

Můžete také použít tyto objekty v rámci destruktory pro statické objekty, volá se během ukončení programu.

Stejně jako u C, vrácení z `main` nebo volání `exit` volá všechny funkce, které jsou registrovány `atexit` v obráceném pořadí z registru. Výjimka vyvolaná z těchto registrovaných funkce volá `terminate`.

## <a name="see-also"></a>Viz také

[Standardní knihovna C++ – přehled](../standard-library/cpp-standard-library-overview.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
