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
ms.openlocfilehash: f3cce539d52bd04e97a6b5f84cbd833b05afb5bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62240571"
---
# <a name="handling-commands-in-the-document"></a>Zpracování příkazů v dokumentu

Dokumentové třídy může také zpracovávat určité příkazy generovaných položek nabídky, tlačítek panelu nástrojů nebo přístupové klávesy. Ve výchozím nastavení `CDocument` zpracovává uložení a uložit jako příkazy v nabídce soubor pomocí serializace. Další příkazy, které mají vliv data mohou být zpracovány členských funkcí třídy dokumentu. Například v programu Scribble třídy `CScribDoc` poskytuje obslužnou rutinu pro úpravy Vymazat vše příkaz, který odstraní všechna data aktuálně uložené v dokumentu. Dokumenty můžou mít mapy zpráv, ale na rozdíl od zobrazení dokumentů nemůže zpracovat standardní zprávy Windows – pouze **wm_command –** zprávy, nebo "příkazy."

## <a name="see-also"></a>Viz také:

[Použití dokumentů](../mfc/using-documents.md)
