---
title: Směrování příkazů
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, command routing
- command handling [MFC], routing commands
- handlers [MFC]
- handlers, command [MFC]
- command routing
ms.assetid: 9393a956-bdd4-47c5-9013-dbd680433f93
ms.openlocfilehash: add047984f5a32e505e8a739922daa137b5e671d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50541697"
---
# <a name="command-routing"></a>Směrování příkazů

Vaše odpovědnosti v práci s příkazy je omezená na vytváření map zpráv spojení mezi příkazy a příslušným obslužným funkcím, úloh, pro který použijete v okně Vlastnosti. Také musíte napsat obslužné rutiny většinu příkazů.

Windows se obvykle posílají do okna hlavního rámce, ale příkaz zprávy pak jsou směrovány na jiné objekty. Rozhraní framework směruje příkazů pomocí standardní posloupnost příkaz cílové objektů, z nichž jeden má mít obslužnou rutinu pro příkaz. Každý objekt cíl příkazu ověří jeho mapy zprávy zobrazíte, pokud může zpracovávat příchozí zprávy.

Různé třídy cíl příkazu zkontrolujte že mapy vlastních zpráv v různých časech. Třída obvykle směruje příkazu k určitým objektům a umožnit jim první příležitosti v příkazu. Pokud žádná z těchto objektů zpracovává příkaz, původní třídy kontroluje svůj vlastní mapu zpráv. Potom pokud ho nelze zadat samotná obslužná rutina, se může směrovat příkaz ještě další cíle příkazů. V tabulce [trasy standardní příkaz](#_core_standard_command_route) níže ukazuje, jak každý z třídy struktury toto pořadí. Obecné pořadí, ve kterém směruje cíl příkazu příkazu je:

1. Na cíl příkazu jeho aktuálně aktivní podřízený objekt.

1. Na sebe sama.

1. Pro další cíle příkazů.

Jak nákladné je tento mechanismus směrování porovnání vaše obslužná rutina nemá v reakci na příkaz, je nízké náklady směrování. Berte v úvahu, že rozhraní framework generuje příkazy pouze v případě, že uživatel pracuje s objektem uživatelského rozhraní.

### <a name="_core_standard_command_route"></a> Standardní příkaz trasy

|Pokud objekt tohoto typu přijme příkaz. . .|Poskytuje samostatně a dalších objektů cíl příkazu příležitost dobře se zpracovat příkaz v tomto pořadí:|
|----------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
|Okno rámce MDI (`CMDIFrameWnd`)|1.  Aktivní `CMDIChildWnd`<br />2.  Toto okno rámce<br />3.  Aplikace (`CWinApp` objektu)|
|Okna rámce dokumentu (`CFrameWnd`, `CMDIChildWnd`)|1.  Aktivní zobrazení<br />2.  Toto okno rámce<br />3.  Aplikace (`CWinApp` objektu)|
|Zobrazit|1.  Toto zobrazení<br />2.  Dokument připojený k zobrazení|
|Dokument|1.  Tento dokument<br />2.  Šablona dokumentu, které jsou připojené k dokumentu|
|Dialogové okno|1.  Toto dialogové okno<br />2.  Okno, které vlastní dialogových oken<br />3.  Aplikace (`CWinApp` objektu)|

Pokud zmíníte číslované položky ve druhém sloupci v předchozí tabulce jiné objekty, jako je například dokument, najdete v odpovídající položku v prvním sloupci. Například při čtení v druhém sloupci, že zobrazení předá příkazu, který bude jeho dokumentu, naleznete v příspěvku "Dokumentů" v prvním sloupci sledovat další směrování.

## <a name="see-also"></a>Viz také

[Jakým způsobem volá framework obslužnou rutinu](../mfc/how-the-framework-calls-a-handler.md)

