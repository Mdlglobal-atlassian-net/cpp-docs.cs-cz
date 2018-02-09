---
title: "Třídy dialogových oken | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.classes.dialog
dev_langs:
- C++
helpviewer_keywords:
- property sheet classes
- dialog box classes
- OLE common dialog classes
- common dialog classes [MFC]
- tab dialog boxes
ms.assetid: db75da23-4eff-4c6c-beae-79cf046fbce9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6d51529e5d04a8297c0d3824ab38c7d2045bc866
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2018
---
# <a name="dialog-box-classes"></a>Třídy dialogových oken
Třída `CDialog` a jejich odvozené třídy zapouzdření dialogového funkce. Vzhledem k tomu, že je zvláštní druh okna, dialogové okno `CDialog` je odvozený od `CWnd`. Vaše dialogové okno odvozovat z `CDialog` nebo některý z společné třídy dialogových oken pro standardní dialogová okna, jako je otevření nebo uložení souboru, tisk, výběr písma a barev, inicializaci operaci vyhledávání a nahrazování nebo provádění různých související s rozhraním OLE operace.  
  
 [CDialog](../mfc/reference/cdialog-class.md)  
 Základní třída pro všechny dialogových oken, modální a nemodální.  
  
 [CDataExchange](../mfc/reference/cdataexchange-class.md)  
 Poskytuje data exchange a informace o ověřování pro dialogová okna.  
  
## <a name="common-dialogs"></a>Společná dialogová okna  
 Tyto třídy dialogových oken pro zapouzdření společná dialogová okna systému Windows. Poskytují snadno použitelné implementace složitá dialogová okna.  
  
 [CCommonDialog](../mfc/reference/ccommondialog-class.md)  
 Základní třída pro všechny běžné dialogových oken.  
  
 [CFileDialog](../mfc/reference/cfiledialog-class.md)  
 Poskytuje standardní dialogové okno pro otevření nebo uložení souboru.  
  
 [CColorDialog](../mfc/reference/ccolordialog-class.md)  
 Poskytuje standardní dialogové okno pro výběr barvy.  
  
 [CFontDialog](../mfc/reference/cfontdialog-class.md)  
 Poskytuje standardní dialogové okno pro výběr písmo.  
  
 [CFindReplaceDialog](../mfc/reference/cfindreplacedialog-class.md)  
 Poskytuje standardní dialogové okno pro operaci vyhledávání a nahrazování.  
  
 [CPrintDialog](../mfc/reference/cprintdialog-class.md)  
 Poskytuje standardní dialogové okno pro tisk souboru.  
  
 [CPrintDialogEx](../mfc/reference/cprintdialogex-class.md)  
 Poskytuje seznam vlastností Tisk systému Windows.  
  
 [CPageSetupDialog](../mfc/reference/cpagesetupdialog-class.md)  
 Zapouzdří služeb poskytovaných běžných nastavení stránky dialogové okno s dodatečnou podporou pro nastavení a úprava tisku okraje.  
  
## <a name="ole-common-dialogs"></a>Společná dialogová okna OLE  
 OLE přidá společná dialogová okna několik do systému Windows. Tyto třídy zapouzdřovat běžné dialogových oken OLE.  
  
 [COleDialog](../mfc/reference/coledialog-class.md)  
 Používá rozhraní tak, aby obsahovala běžné implementace pro všechny dialogových oken OLE. Všechny třídy dialogových oken v kategorii uživatelského rozhraní jsou odvozené z této základní třídy. `COleDialog`nelze použít přímo.  
  
 [COleInsertDialog](../mfc/reference/coleinsertdialog-class.md)  
 Zobrazí dialogové okno Vložit objekt, standardní uživatelské rozhraní, pro vkládání nové OLE propojené nebo vložené položky.  
  
 [COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md)  
 Zobrazí Vložit jinak dialogové okno, standardní uživatelské rozhraní pro implementaci příkaz Upravit Vložit jinak.  
  
 [COleLinksDialog](../mfc/reference/colelinksdialog-class.md)  
 Zobrazí dialogové okno Upravit odkazy, standardní uživatelské rozhraní pro úpravy informace o propojené položky.  
  
 [COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md)  
 Zobrazí dialogové okno Změnit ikonu, standardní uživatelské rozhraní pro změny, které ikony přidružené OLE vložené nebo propojené položky.  
  
 [COleConvertDialog](../mfc/reference/coleconvertdialog-class.md)  
 Zobrazí dialogové okno převést, standardní uživatelské rozhraní pro převod OLE – položky z jednoho typu do jiného.  
  
 [COlePropertiesDialog](../mfc/reference/colepropertiesdialog-class.md)  
 Zapouzdří běžné vlastnosti OLE dialogové okno. Společná dialogová okna OLE vlastnosti poskytují snadný způsob, jak zobrazit a upravit vlastnosti položky OLE dokumentu v souladu s normami systému Windows.  
  
 [COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md)  
 Zobrazí dialogové okno aktualizace, standardní uživatelské rozhraní k aktualizaci všech propojení v dokumentu. Dialogové okno obsahuje indikátor průběhu k označení, jak blízko aktualizace je dokončen.  
  
 [COleChangeSourceDialog](../mfc/reference/colechangesourcedialog-class.md)  
 Zobrazí dialogové okno Změnit zdroj, standardní uživatelské rozhraní pro změnu cílová nebo zdrojová odkazu.  
  
 [COleBusyDialog](../mfc/reference/colebusydialog-class.md)  
 Zobrazí zaneprázdněný Server a Server neodpovídá dialogových oknech, standardní uživatelské rozhraní pro zpracování volání do zaneprázdněn aplikací. Obvykle zobrazují automaticky pomocí [COleMessageFilter](../mfc/reference/colemessagefilter-class.md) implementace.  
  
## <a name="property-sheet-classes"></a>Třídy seznamu vlastností  
 Třídy seznamu vlastností vlastnost umožňují aplikacím pomocí vlastností, také známé jako záložkách dialogová okna. Seznam vlastností jsou účinný způsob, jak uspořádat velký počet prvků v dialogovém okně jeden.  
  
 [CPropertyPage](../mfc/reference/cpropertypage-class.md)  
 Poskytuje na jednotlivých stránkách v rámci seznamu vlastností. Odvození třídy z `CPropertyPage` pro jednotlivé stránky, které chcete přidat do vašeho seznamu vlastností.  
  
 [CPropertySheet](../mfc/reference/cpropertysheet-class.md)  
 Poskytuje rámečku pro více stránky vlastností. Odvození třídě vlastnost list z `CPropertySheet` rychle implementovat vaše vlastností.  
  
 [COlePropertyPage](../mfc/reference/colepropertypage-class.md)  
 Zobrazí vlastnosti OLE řízení v grafickém rozhraní, podobně jako dialogové okno.  
  
## <a name="html-based-dialog-classes"></a>Třídy dialogových oken ve formátu HTML  
 [CDHtmlDialog](../mfc/reference/cdhtmldialog-class.md)  
 Použít k vytvoření dialogových oken, které implementují své uživatelské rozhraní s prostředky HTML místo dialogové okno.  
  
 [CMultiPageDHtmlDialog](../mfc/reference/cmultipagedhtmldialog-class.md)  
 Zobrazí více stránek HTML postupně a zpracovává události z každé stránce.  
  
## <a name="related-classes"></a>Související třídy  
 Tyto třídy nejsou dialogová okna samo o sobě, ale použijte dialogové okno pole šablony a máte hodně chování dialogová okna.  
  
 [CDialogBar](../mfc/reference/cdialogbar-class.md)  
 Ovládací prvek panel, který je založený na šabloně dialogové okno pole.  
  
 [CFormView](../mfc/reference/cformview-class.md)  
 Posuňte zobrazení, jejichž rozložení je definována v poli šablony dialogového okna. Odvození třídy z `CFormView` implementovat uživatelské rozhraní založené na pole šablony dialogového okna.  
  
 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)  
 Nabízí způsob zobrazení přímo připojený k objektu sady záznamů objekt DAO (Data Access). Jako všechna zobrazení formuláře `CDaoRecordView` je založená na šabloně dialogové okno pole.  
  
 [CRecordView](../mfc/reference/crecordview-class.md)  
 Nabízí způsob zobrazení přímo připojený k objektu sady záznamů připojení ODBC (Open Database). Jako všechna zobrazení formuláře `CRecordView` je založená na šabloně dialogové okno pole.  
  
 [CPrintInfo](../mfc/reference/cprintinfo-structure.md)  
 Struktura obsahující informace o úloze nebo tiskového náhledu. Používá architektura pro tisk z [CView](../mfc/reference/cview-class.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../mfc/class-library-overview.md)

