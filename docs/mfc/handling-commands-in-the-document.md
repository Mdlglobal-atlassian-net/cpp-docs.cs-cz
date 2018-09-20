---
title: Zpracování příkazů v dokumentu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message maps [MFC], in document class
- command handling [MFC]
- documents [MFC], message maps
- message handling [MFC], WM_COMMAND messages
- command handling [MFC], commands in documents
- documents [MFC], handling messages in
ms.assetid: c7375584-27af-4275-b2fd-afea476785d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8845ea7c44fd5a34774db0508302f5959987cdc9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46441262"
---
# <a name="handling-commands-in-the-document"></a>Zpracování příkazů v dokumentu

Dokumentové třídy může také zpracovávat určité příkazy generovaných položek nabídky, tlačítek panelu nástrojů nebo přístupové klávesy. Ve výchozím nastavení `CDocument` zpracovává uložení a uložit jako příkazy v nabídce soubor pomocí serializace. Další příkazy, které mají vliv data mohou být zpracovány členských funkcí třídy dokumentu. Například v programu Scribble třídy `CScribDoc` poskytuje obslužnou rutinu pro úpravy Vymazat vše příkaz, který odstraní všechna data aktuálně uložené v dokumentu. Dokumenty můžou mít mapy zpráv, ale na rozdíl od zobrazení dokumentů nemůže zpracovat standardní zprávy Windows – pouze **wm_command –** zprávy, nebo "příkazy."

## <a name="see-also"></a>Viz také

[Použití dokumentů](../mfc/using-documents.md)

