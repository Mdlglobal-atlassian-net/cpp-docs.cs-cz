---
title: Architektura náhledu tisku | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- print preview [MFC], process
- previewing printing
- print preview [MFC], architecture
- printing [MFC], print preview
- print preview [MFC], modifications to MFC
ms.assetid: 0efc87e6-ff8d-43c5-9d72-9b729a169115
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9a5c3aee94f5c3a53f7e31c99a7c2edbfd624e8b
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931775"
---
# <a name="print-preview-architecture"></a>Architektura náhledu tisku
Tento článek vysvětluje, jak rozhraní MFC framework implementuje funkce náhledu tisku. Obsahuje následující témata:  
  
-   [Proces náhledu tisku](#_core_the_print_preview_process)  
  
-   [Úprava náhledu tisku](#_core_modifying_print_preview)  
  
 Náhledu tisku se poněkud liší od obrazovky zobrazení a tisk proto, že místo přímo kreslení obrázku na zařízení, musí aplikace simulovat tiskárny na obrazovce. K tomuto požadavku vyhovělo, knihovny Microsoft Foundation Class definuje speciální (nedokumentovanými) třídy odvozené od [třída CDC](../mfc/reference/cdc-class.md), názvem `CPreviewDC`. Všechny `CDC` objekty obsahovat dvě kontexty zařízení, ale obvykle jsou identické. V `CPreviewDC` objekt, jsou odlišné: první představuje tiskárny se simulated a druhý představuje obrazovky, na kterém je ve skutečnosti zobrazí výstup.  
  
##  <a name="_core_the_print_preview_process"></a> Proces náhledu tisku  
 Když uživatel vybere příkaz Náhled z **soubor** nabídce rozhraní framework vytvoří `CPreviewDC` objektu. Vždy, když vaše aplikace provádí operaci, která nastaví vlastnosti kontextu zařízení tiskárny, provádí rozhraní taky podobná operace v kontextu zařízení obrazovky. Například pokud vaše aplikace vybere písmo pro tisk, rozhraní vybere písmo pro zobrazení na obrazovce, která simuluje písmo tiskárny. Vždy, když vaše aplikace by odesílat výstup na tiskárnu, rozhraní místo toho odesílá výstup na obrazovku.  
  
 Náhledu tisku se také liší od tisk v pořadí, že každý nevykresluje stránek dokumentu. Během tisku, pokračuje rozhraní tiskové smyčky, dokud vykreslena určitý rozsah stránek. Během náhledu tisku jednu nebo dvě stránky se zobrazí, kdykoli a pak čeká aplikace; žádné další stránky se nezobrazí, dokud uživatel odpovídá. Během náhledu tisku musí aplikace také reagovat na zprávy WM_PAINT, stejně jako při obyčejnou obrazovky zobrazení.  
  
 [CView::OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) funkce je volána, když je volána režim náhledu, stejně, jako je na začátku tiskové úlohy. [Cprintinfo – struktura](../mfc/reference/cprintinfo-structure.md) funkci byl předán struktura obsahuje několik členů, jejichž hodnoty můžete nastavit, aby upravit určité charakteristické vlastnosti operace náhledu tisku. Například můžete nastavit *m_nNumPreviewPages* člen k určení, zda chcete zobrazit náhled dokumentu v režimu jednu stránku nebo dvě stránky.  
  
##  <a name="_core_modifying_print_preview"></a> Úprava náhledu tisku  
 Můžete místo snadno upravit chování a vzhled náhledu tisku v mnoha různými způsoby. Například můžete, mimo jiné:  
  
-   Způsobit okno náhledu tisku a zobrazit posuvník pro snadný přístup k libovolné stránce dokumentu.  
  
-   Náhledu tisku příčina udržovat pozici uživatele v dokumentu pomocí od jeho zobrazení na aktuální stránce.  
  
-   Způsobit různé inicializace pro náhledu tisku a tisku.  
  
-   Způsobit náhledu tisku stránky čísla zobrazit ve vlastních formátů.  
  
 Pokud budete vědět, jak dlouho je dokumentu a volání `SetMaxPage` s odpovídající hodnotou rozhraní tyto informace můžete použít v režimu náhledu, a také během tisku. Jakmile rozhraní nezná délka dokumentu, můžete získat okno náhledu s posuvníku panelu, které uživateli umožňují stránky a zpět v dokumentu v režimu preview. Pokud jste nenastavili délka dokumentu, rozhraní nelze umístit posouvací políčko označující aktuální umístění, takže rozhraní nepřidá posuvníku. V takovém případě uživatel musí používat tlačítka předchozí stránku a další stránku, na panelu ovládacího prvku okno náhledu na stránku prostřednictvím dokumentu.  
  
 Pro náhled tisku, může být užitečné pro přiřazení hodnoty k *m_nCurPage* členem `CPrintInfo`, přestože by nikdy uděláte obyčejnou vytisknout. Tento člen během obyčejnou tisku, přenáší informace z rozhraní ke třídě zobrazení. Toto je, jak rozhraní informuje zobrazení, stránky, která by měla být vytisknout.  
  
 Naopak při náhledu tisku režimu spuštění, *m_nCurPage* člen přenáší informace v opačném směru: ze zobrazení rozhraní. Rozhraní používá k určení, stránky, která by měla zobrazit jejich náhled napřed hodnotu tohoto člena. Výchozí hodnota tohoto člena je 1, takže první stránka dokumentu se zobrazí v původně. Můžete přepsat `OnPreparePrinting` pro tento člen číslo stránky se zobrazit v době byla vyvolána příkaz Náhled. Tímto způsobem aplikace udržuje aktuální pozici uživatele při přesunu z režim Normální zobrazení na režim náhledu.  
  
 V některých případech může být vhodné `OnPreparePrinting` k provedení různých inicializace v závislosti na tom, zda je volána pro tiskové úlohy nebo náhledu tisku. Můžete to zjistit tak, že prověří *m_bPreview* členské proměnné v `CPrintInfo` struktura. Tento člen je nastaven na **TRUE** při vyvolání náhledu tisku.  
  
 `CPrintInfo` Struktura také obsahuje člena s názvem *m_strPageDesc*, který slouží k formátování řetězce zobrazí v dolní části obrazovky v režimech jednostránkové a více stránek. Ve výchozím nastavení jsou tyto řetězce ve formátu "stránka *n*" a "stránky *n* - *m*,", ale můžete upravit *m_strPageDesc* z v rámci `OnPreparePrinting` a nastavte řetězce na něco komplikovanějších. V tématu [cprintinfo – struktura](../mfc/reference/cprintinfo-structure.md) v *odkaz knihovny MFC* Další informace.  
  
## <a name="see-also"></a>Viz také  
 [Tisk a náhled tisku](../mfc/printing-and-print-preview.md)   
 [Tisk](../mfc/printing.md)   
 [CView – třída](../mfc/reference/cview-class.md)   
 [CDC – třída](../mfc/reference/cdc-class.md)
