---
title: Zpracování příkazů v dokumentu
ms.date: 11/04/2016
helpviewer_keywords:
- message maps [MFC], in document class
- command handling [MFC]
- documents [MFC], message maps
- message handling [MFC], WM_COMMAND messages
- command handling [MFC], commands in documents
- documents [MFC], handling messages in
ms.assetid: c7375584-27af-4275-b2fd-afea476785d0
ms.openlocfilehash: d2f0a7271452ace9b9e06ff995af61881db4403c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548951"
---
# <a name="handling-commands-in-the-document"></a>Zpracování příkazů v dokumentu

Dokumentové třídy může také zpracovávat určité příkazy generovaných položek nabídky, tlačítek panelu nástrojů nebo přístupové klávesy. Ve výchozím nastavení `CDocument` zpracovává uložení a uložit jako příkazy v nabídce soubor pomocí serializace. Další příkazy, které mají vliv data mohou být zpracovány členských funkcí třídy dokumentu. Například v programu Scribble třídy `CScribDoc` poskytuje obslužnou rutinu pro úpravy Vymazat vše příkaz, který odstraní všechna data aktuálně uložené v dokumentu. Dokumenty můžou mít mapy zpráv, ale na rozdíl od zobrazení dokumentů nemůže zpracovat standardní zprávy Windows – pouze **wm_command –** zprávy, nebo "příkazy."

## <a name="see-also"></a>Viz také

[Použití dokumentů](../mfc/using-documents.md)

