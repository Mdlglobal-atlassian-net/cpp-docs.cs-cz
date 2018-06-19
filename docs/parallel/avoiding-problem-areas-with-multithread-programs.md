---
title: Obcházení problémových oblastí pomocí programů s více vlákny | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- multithreading [C++], troubleshooting
- errors [C++], multithreaded programs
- threading [C++], troubleshooting
- troubleshooting [C++], multithreading
ms.assetid: 06cc231d-bb5a-409d-8bd3-676c9e2a8c5b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5af4c1ca6a86b2cff457aee12e8337103ce7f42d
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686611"
---
# <a name="avoiding-problem-areas-with-multithread-programs"></a>Obcházení problémových oblastí pomocí programů s více vlákny
Existuje několik problémů, které mohou nastat při vytváření, propojení nebo spuštěním programu vícevláknový C. Některé z běžnějších problémy jsou popsány v následující tabulce. (Podobné informace z hlediska MFC, najdete v části [Multithreading: tipy pro programování](../parallel/multithreading-programming-tips.md).)  
  
|Problém|Pravděpodobná příčina|  
|-------------|--------------------|  
|Zobrazí se okno se zprávou zobrazující, že váš program způsobila narušení ochrany.|Mnoho programovací chyby Win32 způsobí narušení ochrany. Obvyklou příčinou porušení zásad ochrany je nepřímé přiřazení dat ukazatelé s hodnotou null. Vzhledem k tomu, že výsledkem je program pokouší získat přístup k paměti, která nepatří k němu, je vydána narušení ochrany.<br /><br /> Snadný způsob, jak zjistit příčinu narušení ochrany je pro kompilaci váš program s informace o ladění a spusťte ho pomocí ladicího programu v prostředí Visual C++. Když dojde k selhání ochrany, systém Windows předá řízení ladicího programu a kurzor je nastavený na řádku, která způsobila problém.|  
|Program generuje mnoho chyb kompilace a odkaz.|Podle nastavení úrovně upozornění kompilátoru do jednoho z jeho nejvyšší hodnoty a budete věnovat pozornost varovným zprávy upozornění, že můžete eliminovat mnoho potenciální problémy. Pomocí úroveň 3 nebo úroveň 4 upozornění úrovně možnosti, můžete zjistit neúmyslné převody dat, chybějící prototypy funkcí a použití funkcí bez ANSI.|  
  
## <a name="see-also"></a>Viz také  
 [Multithreading s použitím jazyka C a prostředí Win32](../parallel/multithreading-with-c-and-win32.md)