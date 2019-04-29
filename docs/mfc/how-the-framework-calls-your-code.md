---
title: Jakým způsobem volá rámec váš kód
ms.date: 11/04/2016
helpviewer_keywords:
- control flow [MFC], MFC framework and your code
- events [MFC], command routing in MFC
- command routing [MFC], framework
- command handling [MFC], calling handlers and code in MFC
- events [MFC], event-driven programming
- MFC, calling code from
- MFC, calling code
- application-specific events [MFC]
- command routing [MFC], MFC
ms.assetid: 39e68189-a580-40d0-9e35-bf5cd24a8ecf
ms.openlocfilehash: 81b0749167391a841badff5494023a2ca5d3147e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407949"
---
# <a name="how-the-framework-calls-your-code"></a>Jakým způsobem volá rámec váš kód

Je důležité porozumět vztahu mezi zdrojový kód a kód v rámci MFC. Po spuštění aplikace nachází většina tok řízení v kódu rozhraní framework. Rozhraní framework spravuje smyčky zpráv, který získá zprávy z Windows, protože uživatel vybere příkazy a úpravy dat v zobrazení. Události, které rozhraní dokáže zpracovat samostatně nespoléhejte na váš kód vůbec. Například rozhraní ví, jak zavřete okna a ukončete aplikaci, v reakci na uživatelských příkazů. Jak zpracovává tyto úlohy, využívá rozhraní obslužné rutiny zpráv a virtuálních funkcí jazyka C++, abychom zajistili příležitostí k těmto událostem a reakce. Váš kód je ale; není v ovládacím prvku rozhraní je.

Pro události specifické pro aplikace volá rámec váš kód. Například když uživatel vybere příkaz nabídky, rozhraní směruje příkaz podél pořadí objektů jazyka C++: aktuální okno zobrazení a rámečku, dokument přidružený k zobrazení, Šablona dokumentu a objekt aplikace. Pokud některý z těchto objektů můžete zpracovat příkaz, je spuštění provedeno, volání funkce odpovídající obslužná rutina zprávy. Pro daný příkaz volání kódu může být té vaší nebo může být rozhraní framework.

Toto uspořádání se trochu znají programátoři se zkušenostmi s tradiční programování pro Windows nebo událostmi řízené programování.

Související témata bude číst co rozhraní jako se inicializuje a spustí aplikaci a poté vyčistí jako ukončení aplikace. Bude také pochopit, kde vejde kód, který píšete.

Další informace najdete v tématu [CWinApp – třída: Třída aplikace](../mfc/cwinapp-the-application-class.md) a [šablony dokumentů a proces vytváření dokumentů/zobrazení](../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="see-also"></a>Viz také:

[Sestavení na základě rozhraní .NET Framework](../mfc/building-on-the-framework.md)
