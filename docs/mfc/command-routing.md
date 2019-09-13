---
title: Směrování příkazů
ms.date: 09/06/2019
helpviewer_keywords:
- MFC, command routing
- command handling [MFC], routing commands
- handlers [MFC]
- handlers, command [MFC]
- command routing
ms.assetid: 9393a956-bdd4-47c5-9013-dbd680433f93
ms.openlocfilehash: 8d1e1e59c56439c01655a1416df645ccc6922411
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907620"
---
# <a name="command-routing"></a>Směrování příkazů

Vaše zodpovědnost za práci s příkazy je omezená na to, aby připojení map zpráv mezi příkazy a jejich obslužnými rutinami bylo omezené na úlohu, pro kterou použijete [Průvodce třídou MFC](reference/mfc-class-wizard.md). Také je nutné napsat kód pro obslužné rutiny příkazů.

Zprávy systému Windows jsou obvykle odesílány do hlavního okna rámce, ale zprávy příkazů jsou poté směrovány do jiných objektů. Rozhraní směruje příkazy přes standardní sekvenci objektů příkazového cíle, přičemž jedna z nich by měla mít obslužnou rutinu pro příkaz. Každý objekt Target příkazu zkontroluje mapu zprávy a zjistí, zda může zpracovávat příchozí zprávu.

Různé třídy cílového příkazu kontrolují svoje vlastní mapy zpráv v různých časech. Třída obvykle směruje příkaz na určité jiné objekty, aby je bylo možné nejprve zadat v příkazu. Pokud žádný z těchto objektů nezpracovává příkaz, původní Třída zkontroluje svou vlastní mapu zpráv. Pokud pak nemůže dodávat obslužnou rutinu samu sebe, může to směrovat příkaz na ještě více cílů příkazu. Níže uvedená [trasa příkazu TABLE Standard](#_core_standard_command_route) ukazuje, jak každá z těchto tříd obsahuje strukturu této sekvence. Obecné pořadí, ve kterém cíl příkazu směruje příkaz:

1. Na svůj aktuálně aktivní podřízený objekt cílového příkazu.

1. Do sebe samé.

1. Do jiných cílů příkazu.

Jak nákladný je tento mechanismus směrování v porovnání s tím, co obslužná rutina reaguje na příkaz, náklady na směrování jsou nízké. Uvědomte si, že rozhraní generuje příkazy pouze v případě, že uživatel pracuje s objektem uživatelského rozhraní.

### <a name="_core_standard_command_route"></a>Standardní příkazová trasa

|Když objekt tohoto typu obdrží příkaz. . .|Sám sobě a jiným cílovým objektům příkazu umožní zpracovat příkaz v tomto pořadí:|
|----------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
|Okno rámce MDI (`CMDIFrameWnd`)|1.  Aktivně`CMDIChildWnd`<br />2.  Toto okno rámce<br />3.  Aplikace (`CWinApp` objekt)|
|Okno rámce dokumentu (`CFrameWnd`, `CMDIChildWnd`)|1.  Aktivní zobrazení<br />2.  Toto okno rámce<br />3.  Aplikace (`CWinApp` objekt)|
|Zobrazit|1.  Toto zobrazení<br />2.  Dokument připojený k zobrazení|
|Dokument|1.  Tento dokument<br />2.  Šablona dokumentu připojená k dokumentu|
|Dialogové okno|1.  Toto dialogové okno<br />2.  Okno, které vlastní dialogové okno<br />3.  Aplikace (`CWinApp` objekt)|

Kde číslované položky ve druhém sloupci v předchozí tabulce zmiňují jiné objekty, jako je například dokument, viz odpovídající položka v prvním sloupci. Například při čtení v druhém sloupci, který zobrazení předává příkaz do svého dokumentu, si přečtěte část "dokument" v prvním sloupci a sledujte směrování dál.

## <a name="see-also"></a>Viz také:

[Jakým způsobem volá framework obslužnou rutinu](../mfc/how-the-framework-calls-a-handler.md)
