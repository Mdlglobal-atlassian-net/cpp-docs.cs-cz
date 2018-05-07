---
title: Výstupní třídy (kontextu zařízení) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.output
dev_langs:
- C++
helpviewer_keywords:
- device contexts [MFC], classes
- screen output classes [MFC]
- printing classes [MFC]
- window drawing classes [MFC]
- painting classes [MFC]
- output classes [MFC]
ms.assetid: 35fd6435-a38e-42c6-a3fa-cd6f39370fc3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 85571e2173d9dc4e900d63e982a91571fafc103e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="output-device-context-classes"></a>Výstupní třídy (třídy kontextu zařízení)
Tyto třídy zapouzdřovat různé typy kontexty zařízení k dispozici v systému Windows.  
  
 Většina tříd, následující zapouzdřovat popisovač pro kontextu zařízení systému Windows. Kontext zařízení je objekt Windows, který obsahuje informace o atributech kreslení zařízení, například zobrazení nebo tiskárnu. Všechny kreslení volání prostřednictvím objektu kontextu zařízení. Další třídy odvozené od `CDC` zapouzdření funkce specializované kontextu zařízení, včetně podpory pro metasoubory systému Windows.  
  
 [CDC](../mfc/reference/cdc-class.md)  
 Základní třída pro kontexty zařízení. Použít přímo pro přístup k celé zobrazení a pro přístup k nondisplay kontexty například tiskárny.  
  
 [CPaintDC](../mfc/reference/cpaintdc-class.md)  
 Použít v kontextu zobrazení `OnPaint` členské funkce systému windows. Automaticky volá `BeginPaint` na vytváření a `EndPaint` na odstranění.  
  
 [CClientDC](../mfc/reference/cclientdc-class.md)  
 Kontextu zobrazení pro klientské oblasti systému windows. Použít, například k vykreslení v okamžitou reakci na události myši.  
  
 [CWindowDC](../mfc/reference/cwindowdc-class.md)  
 Zobrazení kontext pro celý systém windows, včetně klienta i nonclient oblastí.  
  
 [CMetaFileDC](../mfc/reference/cmetafiledc-class.md)  
 Kontext zařízení pro metasoubory systému Windows. WMF obsahuje posloupnost grafiky zařízení rozhraní GDI příkazy, které může být přehraje na virtuálním pevném vytvořit bitovou kopii. Volání členských funkcí `CMetaFileDC` se zaznamenávají do metasoubory.  
  
## <a name="related-classes"></a>Související třídy  
 [CPoint](../atl-mfc-shared/reference/cpoint-class.md)  
 Blokování dvojice souřadnic (x, y).  
  
 [CSize](../atl-mfc-shared/reference/csize-class.md)  
 Obsahuje vzdálenost, relativní umístění nebo spárované hodnoty.  
  
 [CRect](../atl-mfc-shared/reference/crect-class.md)  
 Obsahuje souřadnice obdélníkovou oblastí.  
  
 [CRgn](../mfc/reference/crgn-class.md)  
 Zapouzdří GDI oblast pro manipulaci s eliptické, polygonálních nebo nestandardní oblasti v rámci časového období. Používá ve spojení s výstřižek členské funkce ve třídě `CDC`.  
  
 [Crecttracker –](../mfc/reference/crecttracker-class.md)  
 Zobrazí a zpracovává uživatelské rozhraní pro změnu velikosti a přesunutí obdélníková objekty.  
  
 [CColorDialog](../mfc/reference/ccolordialog-class.md)  
 Poskytuje standardní dialogové okno pro výběr barvy.  
  
 [CFontDialog](../mfc/reference/cfontdialog-class.md)  
 Poskytuje standardní dialogové okno pro výběr písmo.  
  
 [CPrintDialog](../mfc/reference/cprintdialog-class.md)  
 Poskytuje standardní dialogové okno pro tisk souboru.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../mfc/class-library-overview.md)

