---
title: Schránka | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- cutting and copying data
- copying data
- Clipboard
- Clipboard, programming
- transferring data
ms.assetid: a71b2824-1f14-4914-8816-54578d73ad4e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 48315b3608a5e66c2f94e1b06a038772dbb25bb4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380487"
---
# <a name="clipboard"></a>Schránka

Tato řada článků vysvětluje, jak implementovat podporu pro Windows schránky v aplikacích MFC. Schránka Windows se používá dvěma způsoby:

- Implementace standardních příkazů nabídky upravit, jako je vyjmutí, kopírování a vložení.

- Implementace jednotné data transfer přetažením a přetažení (OLE).

Schránka je standardní Windows metodu přenosu dat mezi zdrojem a cílem. Může být rovněž velmi užitečný v operacích OLE. S nástupem OLE existují dva mechanismy schránky ve Windows. Standardní rozhraní API schránky Windows je stále k dispozici, ale byla doplněna mechanismus pro přenos dat OLE. OLE jednotný přenos dat (UDT) podporuje vyjmutí, kopírování a vložení s schránky a přetažením.

Schránka je systémová služba sdílí celou relaci Windows, takže není nutné popisovač nebo své vlastní třídě. Správa pomocí členské funkce třídy do schránky [CWnd](../mfc/reference/cwnd-class.md).

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Kdy používat jednotlivé mechanismy schránky](../mfc/clipboard-when-to-use-each-clipboard-mechanism.md)

- [Pomocí rozhraní API pro tradiční schránky Windows](../mfc/clipboard-using-the-windows-clipboard.md)

- [Použití mechanismu schránky OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)

- [Kopírování a vkládání dat](../mfc/clipboard-copying-and-pasting-data.md)

- [Přidání dalších formátů](../mfc/clipboard-adding-other-formats.md)

- [Schránka Windows](https://msdn.microsoft.com/library/ms648709)

- [Provádění operace přetažení (OLE)](../mfc/drag-and-drop-ole.md)

## <a name="see-also"></a>Viz také

[Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)
