---
title: Obcházení problémových oblastí pomocí programů s více vlákny | Dokumentace Microsoftu
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
ms.openlocfilehash: 4da775a8b068db830d161936a1ca93890d54a1f2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425399"
---
# <a name="avoiding-problem-areas-with-multithread-programs"></a>Obcházení problémových oblastí pomocí programů s více vlákny

Existuje několik problémů, které můžete narazit při vytváření, propojení nebo spuštění vícevláknový C programu. Některé běžné problémy jsou popsány v následující tabulce. (Podobné informace z hlediska knihovny MFC naleznete v tématu [Multithreading: Programovací tipy](multithreading-programming-tips.md).)

|Problém|Pravděpodobná příčina|
|-------------|--------------------|
|Zobrazí okno se zprávou znázorňující, že váš program způsobila narušení ochrany.|Mnoho programovacích chyb systému Win32 způsobit narušení ochrany. Obvyklou příčinou narušení ochrany je nepřímým přiřazením dat do ukazatele s hodnotou null. Vzhledem k tomu, že výsledkem pokusu o přístup k paměti, která nepatří k němu program, objeví se narušení ochrany.<br /><br /> Kompilace programu s informacemi o ladění a spusťte ho pomocí ladicího programu v prostředí Visual C++ je snadný způsob, jak zjistit příčinu narušení ochrany. Pokud dojde k selhání ochrany, Windows předává řízení ladicímu programu a se kurzor na řádek, který způsobil problém.|
|Aplikace generuje mnoho chyb kompilace a odkaz.|Nastavením úroveň upozornění kompilátoru do jednoho z jeho nejvyšší hodnoty a budete věnovat pozornost varovným zprávy upozornění může eliminovat řadu potenciální problémy. Pomocí možnosti pro úrovně upozornění úrovně 4 na úroveň 3, můžete zjistit neúmyslnému data převody, chybí prototypy funkcí a používání funkcí jiné než ANSI.|

## <a name="see-also"></a>Viz také

[Multithreading s použitím jazyka C a prostředí Win32](multithreading-with-c-and-win32.md)