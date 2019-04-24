---
title: Obcházení problémových oblastí pomocí programů s více vlákny
ms.date: 11/04/2016
helpviewer_keywords:
- multithreading [C++], troubleshooting
- errors [C++], multithreaded programs
- threading [C++], troubleshooting
- troubleshooting [C++], multithreading
ms.assetid: 06cc231d-bb5a-409d-8bd3-676c9e2a8c5b
ms.openlocfilehash: 3ceae832599243ffa0aad2b6fa67148e7ea30510
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62237061"
---
# <a name="avoiding-problem-areas-with-multithread-programs"></a>Obcházení problémových oblastí pomocí programů s více vlákny

Existuje několik problémů, které můžete narazit při vytváření, propojení nebo spuštění vícevláknový C programu. Některé běžné problémy jsou popsány v následující tabulce. (Podobné informace z hlediska knihovny MFC naleznete v tématu [Multithreading: Tipy pro programování](multithreading-programming-tips.md).)

|Problém|Pravděpodobná příčina|
|-------------|--------------------|
|Zobrazí okno se zprávou znázorňující, že váš program způsobila narušení ochrany.|Mnoho programovacích chyb systému Win32 způsobit narušení ochrany. Obvyklou příčinou narušení ochrany je nepřímým přiřazením dat do ukazatele s hodnotou null. Vzhledem k tomu, že výsledkem pokusu o přístup k paměti, která nepatří k němu program, objeví se narušení ochrany.<br /><br /> Kompilace programu s informacemi o ladění a spusťte ho pomocí ladicího programu v prostředí Visual C++ je snadný způsob, jak zjistit příčinu narušení ochrany. Pokud dojde k selhání ochrany, Windows předává řízení ladicímu programu a se kurzor na řádek, který způsobil problém.|
|Aplikace generuje mnoho chyb kompilace a odkaz.|Nastavením úroveň upozornění kompilátoru do jednoho z jeho nejvyšší hodnoty a budete věnovat pozornost varovným zprávy upozornění může eliminovat řadu potenciální problémy. Pomocí možnosti pro úrovně upozornění úrovně 4 na úroveň 3, můžete zjistit neúmyslnému data převody, chybí prototypy funkcí a používání funkcí jiné než ANSI.|

## <a name="see-also"></a>Viz také:

[Multithreading s použitím jazyka C a prostředí Win32](multithreading-with-c-and-win32.md)
