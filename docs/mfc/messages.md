---
title: Zprávy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- messages, MFC
- messages [MFC]
ms.assetid: b1476310-a135-42ca-817c-444fb3675491
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f25c9cc70cec598f975bbd242af83597311bdc7c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392252"
---
# <a name="messages"></a>Zprávy

Smyčky zpráv v `Run` členské funkce třídy `CWinApp` načte zařazených do fronty zprávy generované různé události. Například když uživatel klikne myší, Windows odešle několik zprávy týkající se myši, jako je například WM_LBUTTONDOWN, když se stiskne levé tlačítko myši a WM_LBUTTONUP, když se uvolní levé tlačítko myši. Implementace smyčky zpráv aplikace odešle zprávu, která se příslušné okno.

Důležité kategorie zpráv, které jsou popsány v [kategorie zpráv](../mfc/message-categories.md).

## <a name="see-also"></a>Viz také

[Zprávy a příkazy v prostředí .NET Framework](../mfc/messages-and-commands-in-the-framework.md)

