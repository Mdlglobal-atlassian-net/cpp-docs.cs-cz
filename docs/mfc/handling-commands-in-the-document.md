---
title: Zpracování příkazů v dokumentu | Microsoft Docs
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
ms.openlocfilehash: 7a1e848827b46d40c1ec39f2af4788e6957932c5
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929109"
---
# <a name="handling-commands-in-the-document"></a>Zpracování příkazů v dokumentu
Třídě dokument může také zpracovat určité příkazy vygenerované položky nabídky, tlačítek panelu nástrojů nebo klávesy akcelerátoru. Ve výchozím nastavení `CDocument` zpracovává uložení a uložit jako příkazy v nabídce soubor pomocí serializace. Další příkazy, které mají vliv data může být zpracována členské funkce dokumentu. Například v programu Scribble třídy `CScribDoc` poskytuje obslužnou rutinu pro úpravy Vymazat vše příkaz, který odstraní všechna data, které jsou aktuálně uloženy v dokumentu. Dokumenty může mít mapy zpráv, ale na rozdíl od zobrazení, nemůže zpracovat dokumenty standardní zprávy Windows – pouze **wm_command –** zprávy, nebo "příkazy."  
  
## <a name="see-also"></a>Viz také  
 [Použití dokumentů](../mfc/using-documents.md)

