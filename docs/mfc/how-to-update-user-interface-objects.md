---
title: 'Postupy: aktualizace objektů uživatelského rozhraní | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- menus [MFC], updating as context changes
- user interface objects [MFC], updating
- user interface objects [MFC]
- update handlers [MFC]
- enabling UI elements [MFC]
- disabling menus [MFC]
- updating user-interface objects [MFC]
- disabling UI elements [MFC]
- commands [MFC], updating UI
- enabling menus [MFC]
ms.assetid: 82f09773-c978-427b-b321-05a6143b7369
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8afe8f6f7594c2dff75125aa56a210505bf5301d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410582"
---
# <a name="how-to-update-user-interface-objects"></a>Postupy: aktualizace objektů uživatelského rozhraní

Položky nabídky a tlačítka panelu nástrojů obvykle mít více než jeden stav. Položky nabídky například je šedý (neaktivní) Pokud není k dispozici v kontextu k dispozici. Položky nabídky může také být zaškrtnuté nebo nezaškrtnuté. Je-li k dispozici také zakázat tlačítko panelu nástrojů nebo mohla být zařazena.

Kdo aktualizuje stav těchto položek, jak program změnit podmínky logicky, pokud příkaz, který zařizuje služba generuje položku nabídky, Řekněme, dokument, je vhodné, aby dokument aktualizovat položku nabídky. Dokument pravděpodobně obsahuje informace, na kterých je založena aktualizace.

Pokud příkaz obsahuje více objektů uživatelského rozhraní (třeba položku nabídky a tlačítka panelu nástrojů), jak jsou směrovány na stejnou funkci obslužné rutiny. To zapouzdřuje kódu aktualizace uživatelského rozhraní pro všechny objekty ekvivalentní uživatelského rozhraní na jednom místě.

Rozhraní poskytuje pohodlné rozhraní pro automatické aktualizace objektů uživatelského rozhraní. Můžete také provést aktualizaci jiným způsobem, ale rozhraní k dispozici je efektivní a snadno se používá.

Následující témata popisují použití obslužné rutiny aktualizace:

- [Kdy jsou volány obslužné rutiny aktualizace](../mfc/when-update-handlers-are-called.md)

- [ON_UPDATE_COMMAND_UI – makro](../mfc/on-update-command-ui-macro.md)

- [Ccmdui – třída](../mfc/the-ccmdui-class.md)

## <a name="see-also"></a>Viz také

[Nabídky](../mfc/menus-mfc.md)

