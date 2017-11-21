---
title: "Obcházení problémových oblastí pomocí programů s více vlákny | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- multithreading [C++], troubleshooting
- errors [C++], multithreaded programs
- threading [C++], troubleshooting
- troubleshooting [C++], multithreading
ms.assetid: 06cc231d-bb5a-409d-8bd3-676c9e2a8c5b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9a6722e2cea4141a44bee43a162a73176ce35fea
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="avoiding-problem-areas-with-multithread-programs"></a>Obcházení problémových oblastí pomocí programů s více vlákny
Existuje několik problémů, které mohou nastat při vytváření, propojení nebo spuštěním programu vícevláknový C. Některé z běžnějších problémy jsou popsány v následující tabulce. (Podobné informace z hlediska MFC, najdete v části [Multithreading: tipy pro programování](../parallel/multithreading-programming-tips.md).)  
  
|Problém|Pravděpodobná příčina|  
|-------------|--------------------|  
|Zobrazí se okno se zprávou zobrazující, že váš program způsobila narušení ochrany.|Mnoho programovací chyby Win32 způsobí narušení ochrany. Obvyklou příčinou porušení zásad ochrany je nepřímé přiřazení dat ukazatelé s hodnotou null. Vzhledem k tomu, že výsledkem je program pokouší získat přístup k paměti, která nepatří k němu, je vydána narušení ochrany.<br /><br /> Snadný způsob, jak zjistit příčinu narušení ochrany je pro kompilaci váš program s informace o ladění a spusťte ho pomocí ladicího programu v prostředí Visual C++. Když dojde k selhání ochrany, systém Windows předá řízení ladicího programu a kurzor je nastavený na řádku, která způsobila problém.|  
|Program generuje mnoho chyb kompilace a odkaz.|Podle nastavení úrovně upozornění kompilátoru do jednoho z jeho nejvyšší hodnoty a budete věnovat pozornost varovným zprávy upozornění, že můžete eliminovat mnoho potenciální problémy. Pomocí úroveň 3 nebo úroveň 4 upozornění úrovně možnosti, můžete zjistit neúmyslné převody dat, chybějící prototypy funkcí a použití funkcí bez ANSI.|  
  
## <a name="see-also"></a>Viz také  
 [Multithreading s použitím jazyka C a Win32](../parallel/multithreading-with-c-and-win32.md)