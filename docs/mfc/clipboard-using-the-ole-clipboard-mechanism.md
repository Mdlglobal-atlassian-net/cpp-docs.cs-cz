---
title: 'Schránka: Použití mechanismu schránky OLE | Microsoft Docs'
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
ms.openlocfilehash: d4940c614046e3ca407887e05e84c811a156d9c3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="clipboard-using-the-ole-clipboard-mechanism"></a>Schránka: Použití mechanismu schránky OLE
OLE používá standardní formáty a některé formáty OLE specifické pro přenos dat prostřednictvím schránky.  
  
 Při vyjmutí nebo zkopírování dat z aplikace, jsou data uložena do schránky, který se má použít později v operace vkládání. Tato data jsou v různých formátech. Když uživatel vybere možnost vložení dat ze schránky, můžete zvolit aplikace, které z těchto formátů používat. Aplikace by měly být zapsány do formátu, který obsahuje informace o většině zvolte, pokud uživatel konkrétně vyzve k zadání některých formátu, pomocí Vložit jinak. Než budete pokračovat, budete chtít přečíst [datové objekty a zdroje dat (OLE)](../mfc/data-objects-and-data-sources-ole.md) témata. Popisují základní informace o způsobu přenosu dat pracovní a jejich implementaci ve svých aplikacích.  
  
 Windows definuje počet standardní formáty, které lze použít pro přenos dat prostřednictvím schránky. Mezi ně patří metasoubory, text, rastrové obrázky a další. OLE definuje počet OLE specifické formáty také. Pro aplikace, které potřebují podrobnější informace než daný podle tyto standardní formáty je vhodné k registraci svých vlastních vlastní formáty schránky. Pomocí funkce rozhraní API Win32 [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) k tomu.  
  
 Například aplikace Microsoft Excel zaregistruje vlastní formát pro tabulek. Tento formát představuje mnohem víc informací, než je třeba, nemá rastrový obrázek. Tato data po vložení do aplikace, která podporuje formát tabulky, se zachovají všechny vzorce a hodnoty z tabulky a můžete aktualizovat v případě potřeby. Aplikace Microsoft Excel také vloží data do schránky ve formátech tak, že je můžete vložit jako položku OLE. Všechny OLE – kontejner dokumentu můžete vložit tyto informace jako vložené položky. Tato vložená položka se dá změnit pomocí aplikace Microsoft Excel. Schránka také obsahuje jednoduché rastrový obrázek vybrané oblasti v tabulce. To můžete být vložit také do dokumentu kontejnery OLE nebo do editory rastrového obrázku, jako je Malování. V případě rastrového obrázku ale neexistuje žádný způsob, jak pracovat s daty jako tabulku.  
  
 K načtení maximální množství informací ze schránky, aplikace zkontrolujte těchto vlastních formátů před vložením dat ze schránky.  
  
 Například pokud chcete povolit příkaz Cut, můžete napsat obslužnou rutinu přibližně takto:  
  
 [!code-cpp[NVC_MFCListView#3](../atl/reference/codesnippet/cpp/clipboard-using-the-ole-clipboard-mechanism_1.cpp)]  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Kopírování a vkládání dat](../mfc/clipboard-copying-and-pasting-data.md)  
  
-   [Přidání dalších formátů](../mfc/clipboard-adding-other-formats.md)  
  
-   [Použití schránky systému Windows](../mfc/clipboard-using-the-windows-clipboard.md)  
  
-   [OLE](../mfc/ole-background.md)  
  
-   [Objekty a data zdroje dat OLE a uniform přenosu dat](../mfc/data-objects-and-data-sources-ole.md)  
  
## <a name="see-also"></a>Viz také  
 [Schránka](../mfc/clipboard.md)

