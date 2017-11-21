---
title: "Postupy: Implementace sledování v kódu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: CRectTracker class [MFC], implementing trackers
ms.assetid: baaeca2c-5114-485f-bf58-8807db1bc973
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a0b90332ea2f582287eb9b799b12368d0b397d0e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-implement-tracking-in-your-code"></a>Postupy: Implementace sledování v kódu
Ke sledování OLE položku, je nutné zajistit určité události související s položkou, například kliknutí na položku nebo aktualizace zobrazení dokumentu. Ve všech případech je dostačující deklarovat dočasného [crecttracker –](../mfc/reference/crecttracker-class.md) objektu a pracovat s položka prostřednictvím tohoto objektu.  
  
 Když uživatel vybere položku nebo vloží objekt se příkaz nabídky, je nutné inicializovat ke sledovacímu modulu za správné stylů představující stav položky OLE. Následující tabulka popisuje konvence používané OCLIENT vzorku. Další informace o těchto styly najdete v tématu `CRectTracker`.  
  
### <a name="container-styles-and-states-of-the-ole-item"></a>Styly kontejneru a stavy položky OLE  
  
|Styl zobrazí|Stav položky OLE|  
|---------------------|-----------------------|  
|Desítkovém ohraničení|Položka je propojena.|  
|Pevné ohraničení|Vložené položky v dokumentu|  
|Změnit velikost obslužných rutin|Aktuálně je vybraná položka|  
|Šrafované ohraničení|Položka je aktuálně místní active|  
|Šrafování vzor překryvy položky|Položky na serveru je otevřený|  
  
 Může zpracovávat tento inicializace snadno pomocí procedury, která kontroluje stav položky OLE a nastaví příslušná stylů. **SetupTracker** funkce najít v ukázce OCLIENT ukazuje inicializace sledovací modul. Parametry pro tuto funkci jsou adresu ke sledovacímu modulu *pTracker*; ukazatel na položku klienta, která souvisí s sledovací modul, `pItem`; a ukazatel na obdélníku, *pTrueRect*. Úplnější příklad této funkce, najdete v části ukázka MFC OLE [OCLIENT](../visual-cpp-samples.md).  
  
 **SetupTracker** příklad kódu představuje jedinou funkci; řádky funkce jsou spolu s diskuzi o funkce funkce:  
  
 [!code-cpp[NVC_MFCOClient#1](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_1.cpp)]  
  
 Ke sledovacímu modulu se inicializuje pomocí nastavení minimální velikosti a vymazání styl ke sledovacímu modulu.  
  
 [!code-cpp[NVC_MFCOClient#2](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_2.cpp)]  
  
 Následující řádky zkontrolujte, jestli je aktuálně vybrané položky a jestli je položka propojené v dokumentu nebo jej. Obslužné rutiny změny velikosti umístěný uvnitř ohraničení se přidají do styl, která určuje aktuálně vybranou položku. Pokud je položka připojena k dokumentu, použije se styl ohraničení desítkovém. Pokud vložené položky, použije se pevné ohraničení.  
  
 [!code-cpp[NVC_MFCOClient#3](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_3.cpp)]  
  
 Následující kód překryvy otevřete položky s šrafované vzor, pokud je položka aktuálně.  
  
 [!code-cpp[NVC_MFCOClient#4](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_4.cpp)]  
  
 Tuto funkci můžete volat potom vždy, když má ke sledovacímu modulu, který se má zobrazit. Například volání této funkce z `OnDraw` funkce zobrazení třídy. Tím se aktualizuje ke sledovacímu modulu vzhled vždy, když je překreslen zobrazení. Úplný příklad, najdete v článku **CMainView::OnDraw** funkce vzorku MFC OLE [OCLIENT](../visual-cpp-samples.md).  
  
 Ve vaší aplikaci dojde k události, které vyžadují sledovací modul kódu, třeba změny velikosti, přesunutí nebo přístupů zjišťování. Tyto akce obvykle naznačují, že se pokus o přišla převzetí nebo přesunout položku. V těchto případech je nutné se rozhodnout, co byl převzat: Popisovač změny velikosti nebo část ohraničení mezi změnit velikost obslužné rutiny. `OnLButtonDown` Obslužné rutiny zpráv je vhodná k testování polohu myši ve vztahu k položce. Ujistěte se, volání `CRectTracker::HitTest`. Pokud se test vrátí něco kromě **CRectTracker::hitOutside**, položka je se změnila velikost nebo přesunout. Proto byste měli volání `Track` – členská funkce. Najdete v článku **CMainView::OnLButtonDown** funkce umístěný v ukázce MFC OLE [OCLIENT](../visual-cpp-samples.md) kompletní příklad.  
  
 `CRectTracker` Třída poskytuje několik různých kurzoru tvarů slouží k určení, zda přesunu, změnit velikost nebo přetáhněte operace probíhá. Ke zpracování této události, zkontrolujte, zda je vybrána položka aktuálně pod myší. Pokud je, ujistěte se, volání `CRectTracker::SetCursor`, nebo volejte výchozí obslužnou rutinu. Následující příklad je z ukázkové MFC OLE [OCLIENT](../visual-cpp-samples.md):  
  
 [!code-cpp[NVC_MFCOClient#5](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_5.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Snímače: Implementace snímačů ve vašich aplikacích OLE](../mfc/trackers-implementing-trackers-in-your-ole-application.md)

