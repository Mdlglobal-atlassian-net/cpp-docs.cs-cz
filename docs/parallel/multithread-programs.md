---
title: Programy s více vlákny | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- threading [C++], about threading
- multithreading [C++], about threads
ms.assetid: 02443596-f7e1-48d0-b3a4-39ee0e54e444
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 88c39590f27597d29a27ab60bbc95c3c46dc862c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416861"
---
# <a name="multithread-programs"></a>Programy s více vlákny

Vlákno je v podstatě cesta provádění prostřednictvím programu. Také je nejmenší jednotka spuštění, která plánuje Win32. Vlákno se skládá ze zásobníku, stav registrech procesoru a položky v seznamu spuštění systému plánovače. Každé vlákno sdílejí všechny procesu prostředky.

Proces se skládá z jednoho nebo více vláken a kód, data a další prostředky programu v paměti. Typický program prostředky jsou otevřených souborů, semaforů a dynamicky přidělené paměti. Program provede při plánovači systému jeden z jeho vláken poskytuje řízení provádění. Plánovač Určuje, která vlákna spuštěna, a pokud by měly být spuštěny. Vlákna s nižší prioritou může být nutné počkejte na dokončení úloh vlákna s vyšší prioritou. Na počítačích s více procesory můžete přesunout Plánovač jednotlivá vlákna na různých procesorech vyvážit zatížení procesoru.

Každé vlákno v procesu funguje nezávisle na sobě. Pokud jste zviditelníte je k sobě navzájem vlákna spustit samostatně a jsou bez ohledu ostatní vlákna v procesu. Vlákna sdílení společných prostředků, ale musí koordinovat jejich práci s použitím semafory nebo jiným způsobem meziprocesová komunikace. Další informace o synchronizaci vláken naleznete v tématu [psaní programů s více vlákny pro Win32](writing-a-multithreaded-win32-program.md).

## <a name="see-also"></a>Viz také

[Multithreading s použitím jazyka C a prostředí Win32](multithreading-with-c-and-win32.md)