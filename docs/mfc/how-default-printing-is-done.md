---
title: "Jak probíhá výchozí tisk | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- default printing
- printing [MFC], default
- defaults, printing
ms.assetid: 0f698459-0fc9-4d43-97da-29cf0f65daa2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1270468432ed1588d7e79f656e258b8874e07f72
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-default-printing-is-done"></a>Jak probíhá výchozí tisk
Tento článek vysvětluje výchozí proces tisku v systému Windows z hlediska rozhraní MFC framework.  
  
 V aplikacích MFC třída zobrazení obsahuje členské funkce s názvem `OnDraw` obsahující kreslení kódu. `OnDraw`má ukazatel [CDC](../mfc/reference/cdc-class.md) objekt jako parametr. Aby `CDC` objekt představuje kontext zařízení pro příjem bitovou kopii vyprodukované `OnDraw`. Pokud okno zobrazení dokumentu obdrží [WM_PAINT](http://msdn.microsoft.com/library/windows/desktop/dd145213) zprávy, volání framework `OnDraw` a předává je kontext zařízení pro obrazovky ( [CPaintDC](../mfc/reference/cpaintdc-class.md) objekt specifické). Podle toho `OnDraw`vloží výstupu na obrazovku.  
  
 Při programování pro systém Windows, je velmi podobná odeslání výstupu na obrazovku odesílání výstup na tiskárnu. Je to proto, že rozhraní grafiky zařízení systému Windows (GDI) je nezávislý na hardwaru. Stejné funkce GDI můžete použít pro zobrazení na obrazovce nebo pro tisk jednoduše tak, že v kontextu příslušné zařízení. Pokud `CDC` objektu, který `OnDraw` obdrží představuje tiskárny, `OnDraw`výstupu přejde na tiskárnu.  
  
 Tato část popisuje, jak aplikace MFC můžete provádět jednoduché tisk bez nutnosti další úsilí na druhé straně. Rozhraní framework postará zobrazení dialogového okna Tisk a vytváření kontextu zařízení pro tiskárny. Když uživatel vybere příkaz Tisk v nabídce Soubor, zobrazení předá tento kontext zařízení k `OnDraw`, který vykreslí dokument na tiskárnu.  
  
 Existují však určité významné rozdíly mezi tisku a zobrazení na obrazovce. Při tisku, je nutné rozdělit do různých stránek a zobrazení je jeden po druhém, nikoli zobrazit libovolnou část je viditelná v okně dokumentu. Jako nezbytným důsledkem budete muset mít na paměti velikost papíru (jestli je velikost písmeno, právních nebo obálky). Můžete chtít tisku v různých orientace, jako třeba v režimu šířku i na výšku. Knihovny Microsoft Foundation Class nelze předpovědět, jak aplikace bude zpracovávat tyto problémy, takže poskytuje protokol můžete přidat tyto možnosti.  
  
 Že protokol je popsána v článku [více stránek dokumenty](../mfc/multipage-documents.md).  
  
## <a name="see-also"></a>Viz také  
 [Tisk](../mfc/printing.md)

