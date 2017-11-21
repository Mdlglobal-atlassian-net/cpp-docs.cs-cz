---
title: "Schránka: Přidání dalších formátů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- formats [MFC], Clipboard
- Clipboard, formats
- custom formats, placing on Clipboard
- custom formats
- registering custom Clipboard data formats
- custom Clipboard data formats
ms.assetid: aea58159-65ed-4385-aeaa-3d9d5281903b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 030deda8b46492dba76fb85702fa40f22b0db594
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="clipboard-adding-other-formats"></a>Schránka: Přidání dalších formátů
Toto téma vysvětluje, jak rozšířit seznam podporovaných formátů, zejména pro podporu technologie OLE. Téma [schránka: kopírování a vložit Data](../mfc/clipboard-copying-and-pasting-data.md) popisuje minimální implementace potřebných k podpoře kopírování a vkládání ze schránky. Pokud je to všechny implementujete, jsou pouze formáty umístit do schránky `CF_METAFILEPICT`, **CF_EMBEDSOURCE**, **CF_OBJECTDESCRIPTOR**a případně `CF_LINKSOURCE`. Většina aplikací potřebovat více formátů do schránky. než tyto tři.  
  
##  <a name="_core_registering_custom_formats"></a>Registrace vlastních formátů  
 Pokud chcete vytvořit vlastní formáty, postupujte stejným způsobem, který byste použili při registraci všechny vlastní formát schránky: předat název formát, který se **RegisterClipboardFormat** funkce a použít hodnoty jako ID formátu.  
  
##  <a name="_core_placing_formats_on_the_clipboard"></a>Formáty umístění do schránky  
 Chcete-li přidat více formátů těm, které jsou umístěny do schránky, je nutné přepsat `OnGetClipboardData` funkce třídy odvozené od buď `COleClientItem` nebo `COleServerItem` (v závislosti na tom, zda je nativní data, která mají být zkopírovány). V této funkci používejte následující postup.  
  
#### <a name="to-place-formats-on-the-clipboard"></a>Chcete-li formáty umístění do schránky  
  
1.  Vytvoření `COleDataSource` objektu.  
  
2.  Tento zdroj dat předat funkci, která přidá nativní datové formáty seznam podporovaných formátů voláním `COleDataSource::CacheGlobalData`.  
  
3.  Přidání standardní formáty voláním `COleDataSource::CacheGlobalData` pro každou standardní formát, které chcete podporovat.  
  
 Tento postup slouží v aplikaci MFC OLE ukázka [HIERSVR](../visual-cpp-samples.md) (Prozkoumat `OnGetClipboardData` členské funkce **CServerItem** – třída). V této ukázce jediným rozdílem je, že třetí krok není implementována, protože HIERSVR nepodporuje žádné jiné standardní formáty.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Objekty a data zdroje dat OLE a uniform přenosu dat](../mfc/data-objects-and-data-sources-ole.md)  
  
-   [OLE – přetažení](../mfc/drag-and-drop-ole.md)  
  
-   [OLE](../mfc/ole-background.md)  
  
## <a name="see-also"></a>Viz také  
 [Schránka: Použití mechanismu schránky OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)

