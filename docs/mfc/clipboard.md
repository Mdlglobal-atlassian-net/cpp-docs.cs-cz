---
title: Schránka
ms.date: 11/04/2016
helpviewer_keywords:
- cutting and copying data
- copying data
- Clipboard
- Clipboard, programming
- transferring data
ms.assetid: a71b2824-1f14-4914-8816-54578d73ad4e
ms.openlocfilehash: 1db089110904ab88eb9c0c111d9da4e4e6869c82
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127904"
---
# <a name="clipboard"></a>Schránka

Tato rodina článků vysvětluje, jak implementovat podporu pro schránku Windows v aplikacích MFC. Schránka Windows se používá dvěma způsoby:

- Implementace standardních příkazů nabídky pro úpravy, jako je například vyjmutí, kopírování a vložení.

- Implementace jednotného přenosu dat pomocí přetažení OLE

Schránka je standardní metodou Windows přenosu dat mezi zdrojem a cílem. Může být také velmi užitečné v operacích OLE. U nástupem technologie OLE existují dva mechanismy schránky ve Windows. Standardní rozhraní Windows schránka je stále k dispozici, ale bylo doplněno mechanismem přenosu dat OLE. Rozhraní UDT (OLE Uniform Data Transfer) podporuje vyjmutí, kopírování a vložení ve schránce a přetažení.

Schránka je systémová služba sdílená celou relací Windows, takže nemá popisovač ani třídu vlastního typu. Schránku můžete spravovat prostřednictvím členských funkcí třídy [CWnd](../mfc/reference/cwnd-class.md).

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace

- [Kdy používat jednotlivé mechanismy schránky](../mfc/clipboard-when-to-use-each-clipboard-mechanism.md)

- [Používání tradičních rozhraní Windows schránka API](../mfc/clipboard-using-the-windows-clipboard.md)

- [Použití mechanismu schránky OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)

- [Kopírování a vkládání dat](../mfc/clipboard-copying-and-pasting-data.md)

- [Přidávání dalších formátů](../mfc/clipboard-adding-other-formats.md)

- [Schránka Windows](/windows/win32/dataxchg/clipboard)

- [OLE – přetažení](../mfc/drag-and-drop-ole.md)

## <a name="see-also"></a>Viz také

[Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)
