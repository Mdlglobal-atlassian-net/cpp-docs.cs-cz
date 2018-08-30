---
title: 'Schránka: Použití mechanismu schránky OLE | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- applications [OLE], Clipboard
- OLE Clipboard
- Clipboard [MFC], OLE formats
- OLE Clipboard, formats
- formats [MFC], Clipboard for OLE
ms.assetid: 229cc610-5bb1-435e-bd20-2c8b9964d1af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d37618dccabd576a67c8b82a8b8ab38246254070
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43214700"
---
# <a name="clipboard-using-the-ole-clipboard-mechanism"></a>Schránka: Použití mechanismu schránky OLE
OLE používá standardní formáty a některé specifické pro OLE – formáty pro přenos dat do schránky.  
  
 Při vyjmutí a kopírování dat z aplikace, jsou data uložena do schránky, který se má použít později v operacích vložit. Tato data jsou v různých formátech. Když uživatel vybere vložení dat ze schránky, aplikace můžete zvolit, které z těchto formátů používat. Aplikace by měly být zapsány vybrat formát, který obsahuje informace o většině, pokud uživatel konkrétně požádá o určitém formátu, pomocí Vložit jinak. Než budete pokračovat, budete chtít přečíst [datové objekty a zdroje dat (OLE)](../mfc/data-objects-and-data-sources-ole.md) témata. Popisují základní informace o jak datové přenosy práce a jak implementovat ve svých aplikacích.  
  
 Windows definuje počet standardní formáty, které lze použít pro přenos dat do schránky. Patří mezi ně metasoubory, text, rastrových obrázků a dalších. OLE definuje počet OLE konkrétní formáty, také. Pro aplikace, které potřebujete podrobnější informace než určené pomocí těchto standardní formáty je vhodné zaregistrovat svoje vlastní vlastní formáty schránky. Použití funkce rozhraní Win32 API [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) provedete to tak.  
  
 Například aplikace Microsoft Excel zaregistruje vlastního formátu pro tabulky. Tento formát přenáší mnohem víc informací, než je třeba, nemá rastrový obrázek. Když tato data budou vložena do aplikace, který podporuje formát tabulky, vzorců a hodnoty z tabulky se zachovají a je možné aktualizovat v případě potřeby. Aplikace Microsoft Excel také vloží data do schránky ve formátech, tak, že je můžete vložit jako položky OLE. Libovolném kontejneru OLE dokumentu můžete vložit tyto informace jako vloženou položku. Tato vložená položka lze změnit pomocí aplikace Microsoft Excel. Schránka také obsahuje jednoduché rastrový obrázek vybranou oblast na listu. To může také ho šlo vložit do dokumentu kontejnery OLE nebo do editorů rastrový obrázek, jako je Malování. V případě rastrový obrázek ale neexistuje žádný způsob, jak pracovat s daty jako tabulku.  
  
 K načtení maximální množství informací ze schránky, by měla aplikace zkontrolujte tyto vlastní formáty před vložením dat ze schránky.  
  
 Například pokud chcete povolit příkaz Vyjmout, můžete například napsat obslužnou rutinu přibližně takto:  
  
 [!code-cpp[NVC_MFCListView#3](../atl/reference/codesnippet/cpp/clipboard-using-the-ole-clipboard-mechanism_1.cpp)]  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací  
  
-   [Kopírování a vkládání dat](../mfc/clipboard-copying-and-pasting-data.md)  
  
-   [Přidání dalších formátů](../mfc/clipboard-adding-other-formats.md)  
  
-   [Použití schránky Windows](../mfc/clipboard-using-the-windows-clipboard.md)  
  
-   [OLE](../mfc/ole-background.md)  
  
-   [Objekty a data zdroje dat OLE a jednotné přenosu dat](../mfc/data-objects-and-data-sources-ole.md)  
  
## <a name="see-also"></a>Viz také  
 [Schránka](../mfc/clipboard.md)

