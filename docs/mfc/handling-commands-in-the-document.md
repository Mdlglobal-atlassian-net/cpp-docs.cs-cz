---
title: "Zpracování příkazů v dokumentu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a8d27698d573e1dee539f93ab88015285648fa77
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="handling-commands-in-the-document"></a>Zpracování příkazů v dokumentu
Třídě dokument může také zpracovat určité příkazy vygenerované položky nabídky, tlačítek panelu nástrojů nebo klávesy akcelerátoru. Ve výchozím nastavení **CDocument** zpracovává uložení a uložit jako příkazy v nabídce soubor pomocí serializace. Další příkazy, které mají vliv data může být zpracována členské funkce dokumentu. Například v programu Scribble třídy `CScribDoc` poskytuje obslužnou rutinu pro úpravy Vymazat vše příkaz, který odstraní všechna data, které jsou aktuálně uloženy v dokumentu. Dokumenty může mít mapy zpráv, ale na rozdíl od zobrazení, nemůže zpracovat dokumenty standardní zprávy Windows – pouze **wm_command –** zprávy, nebo "příkazy."  
  
## <a name="see-also"></a>Viz také  
 [Použití dokumentů](../mfc/using-documents.md)

