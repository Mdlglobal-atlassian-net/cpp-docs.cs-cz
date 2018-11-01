---
title: Třídy dialogových oken
ms.date: 11/04/2016
f1_keywords:
- vc.classes.dialog
helpviewer_keywords:
- property sheet classes
- dialog box classes
- OLE common dialog classes
- common dialog classes [MFC]
- tab dialog boxes
ms.assetid: db75da23-4eff-4c6c-beae-79cf046fbce9
ms.openlocfilehash: 3533a548f009a65462ce0d821d782db0ada9aa4b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490002"
---
# <a name="dialog-box-classes"></a>Třídy dialogových oken

Třída `CDialog` a její odvozené třídy zapouzdřují funkce dialogového okna. Protože je zvláštní druh okna, dialogové okno `CDialog` je odvozen z `CWnd`. Jsou odvozeny z třídy dialogového okna `CDialog` nebo použijte jednu z společné třídy dialogových oken pro standardní dialogová okna, jako je otevření nebo uložení souboru, tisk, výběru písma a barvy, zahajuje se operace hledání a nahrazování nebo provádění různých související s rozhraním OLE operace.

[CDialog](../mfc/reference/cdialog-class.md)<br/>
Základní třída pro všechna dialogová okna, modální a nemodální.

[CDataExchange](../mfc/reference/cdataexchange-class.md)<br/>
Poskytuje data systému exchange a informace o ověřování pro dialogová okna.

## <a name="common-dialogs"></a>Společná dialogová okna

Tyto třídy dialogových oken zapouzdření společná dialogová okna Windows. Poskytují snadno použitelné implementace složité dialogových oknech.

[Ccommondialog –](../mfc/reference/ccommondialog-class.md)<br/>
Základní třída pro všechny běžných dialogových oknech.

[CFileDialog](../mfc/reference/cfiledialog-class.md)<br/>
Poskytuje standardní dialogové okno pro otevření nebo uložení souboru.

[Ccolordialog –](../mfc/reference/ccolordialog-class.md)<br/>
Poskytuje standardní dialogové okno pro výběr barvy.

[Cfontdialog –](../mfc/reference/cfontdialog-class.md)<br/>
Poskytuje standardní dialogové okno pro výběr písma.

[CFindReplaceDialog.](../mfc/reference/cfindreplacedialog-class.md)<br/>
Poskytuje standardní dialogové okno pro operace hledání a nahrazení.

[Cprintdialog –](../mfc/reference/cprintdialog-class.md)<br/>
Poskytuje standardní dialogové okno pro tisk souboru.

[CPrintDialogEx](../mfc/reference/cprintdialogex-class.md)<br/>
Poskytuje seznam vlastností tisku Windows.

[Cpagesetupdialog –](../mfc/reference/cpagesetupdialog-class.md)<br/>
Zapouzdřuje služby poskytované dialogovým oknem běžných nastavení stránky Windows s další podporou nastavení a úprav okrajů tisku.

## <a name="ole-common-dialogs"></a>Společná dialogová okna OLE

Několik běžných dialogových oknech OLE přidá do Windows. Tyto třídy zapouzdření běžných dialogových oknech OLE.

[Coledialog –](../mfc/reference/coledialog-class.md)<br/>
Používá rozhraní tak, aby obsahovala běžné implementace pro všechna dialogová okna OLE. Všechny třídy dialogových oken v kategorii uživatelského rozhraní jsou odvozeny z této základní třídy. `COleDialog` nelze použít přímo.

[Coleinsertdialog –](../mfc/reference/coleinsertdialog-class.md)<br/>
Zobrazí dialogové okno Vložit objekt, tak se standardní uživatelské rozhraní pro vložení OLE nové propojené nebo vložené položky.

[Colepastespecialdialog –](../mfc/reference/colepastespecialdialog-class.md)<br/>
Zobrazí zvláštní vložení dialogové okno, standardní uživatelské rozhraní pro implementaci příkazu Upravit Vložit jinak.

[Colelinksdialog –](../mfc/reference/colelinksdialog-class.md)<br/>
Zobrazí dialogové okno Upravit odkazy, standardní uživatelské rozhraní pro úpravu informace o propojené položky.

[Colechangeicondialog –](../mfc/reference/colechangeicondialog-class.md)<br/>
Zobrazí dialogové okno změny ikony, standardní uživatelské rozhraní, že změníte ikony přidružené k OLE vložené nebo propojené položky.

[Coleconvertdialog –](../mfc/reference/coleconvertdialog-class.md)<br/>
Zobrazí dialogové okno převést, standardní uživatelské rozhraní pro převod OLE – položky z jednoho typu na jiný.

[Colepropertiesdialog –](../mfc/reference/colepropertiesdialog-class.md)<br/>
Zapouzdřuje dialogové okno vlastnosti OLE Windows běžné. Společná dialogová okna OLE vlastnosti poskytují snadný způsob, jak zobrazit a upravit vlastnosti dokumentu položky OLE v souladu se standardy Windows.

[Coleupdatedialog –](../mfc/reference/coleupdatedialog-class.md)<br/>
Zobrazí dialogové okno aktualizace, standardní uživatelské rozhraní pro aktualizaci všech odkazů v dokumentu. Dialogové okno obsahuje indikátor průběhu označuje, jak blízko bude dokončen.

[Colechangesourcedialog –](../mfc/reference/colechangesourcedialog-class.md)<br/>
Zobrazí dialogové okno Změnit zdroj, standardní uživatelské rozhraní pro změnu cílová nebo zdrojová odkazu.

[Colebusydialog –](../mfc/reference/colebusydialog-class.md)<br/>
Zobrazí Serverbusy dialogových oknech a Server neodpovídá, standardní uživatelské rozhraní pro zpracování volání zaneprázdněný aplikací. Obvykle automaticky zobrazí [colemessagefilter –](../mfc/reference/colemessagefilter-class.md) implementace.

## <a name="property-sheet-classes"></a>Třídy seznamu vlastností

Třídy seznamu vlastností umožňují aplikacím použít seznamy vlastností, označovaný také jako s kartami dialogová okna. Seznamy vlastností jsou efektivní způsob, jak uspořádat velké množství ovládacích prvků v dialogovém okně jednoho.

[CPropertyPage –](../mfc/reference/cpropertypage-class.md)<br/>
Poskytuje jednotlivých stránek v rámci seznamu vlastností. Odvodit třídu z `CPropertyPage` pro každou stránku přidat do vašeho seznamu vlastností.

[CPropertySheet](../mfc/reference/cpropertysheet-class.md)<br/>
Poskytuje rámce pro více stránek vlastností. Odvodit třídu list vaše vlastnost z `CPropertySheet` rychle implementovat vaše seznamy vlastností.

[COlePropertyPage –](../mfc/reference/colepropertypage-class.md)<br/>
Zobrazí vlastnosti OLE řízení v grafickém rozhraní, podobnému dialogovému oknu.

## <a name="html-based-dialog-classes"></a>Třídy dialogových oken založený na jazyce HTML

[CDHtmlDialog](../mfc/reference/cdhtmldialog-class.md)<br/>
Použít k vytváření dialogových oken, které implementují jejich uživatelské rozhraní pomocí HTML, spíše než dialogové okno prostředků.

[CMultiPageDHtmlDialog](../mfc/reference/cmultipagedhtmldialog-class.md)<br/>
Zobrazí postupně několik stránek HTML a zpracovává události z každé stránky.

## <a name="related-classes"></a>Související třídy

Tyto třídy nejsou dialogových oknech samo o sobě, ale pomocí šablon dialogového okna pole a mají velkou část chování dialogových oknech.

[CDialogBar –](../mfc/reference/cdialogbar-class.md)<br/>
Ovládací panel, který je založen na šablony dialogového okna.

[CFormView](../mfc/reference/cformview-class.md)<br/>
Posunout zobrazení, jejichž rozložení je definován v šabloně dialogu pole. Odvodit třídu z `CFormView` k implementaci uživatelského rozhraní založené na šablony dialogového okna.

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
Formulář obsahuje zobrazení přímo připojen k objektu sady záznamů objekt DAO (Data Access). Všechna zobrazení formulářů, jako jsou `CDaoRecordView` je založen na šabloně dialogu pole.

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
Formulář obsahuje zobrazení přímo připojen k objektu sady záznamů připojení ODBC (Open Database). Všechna zobrazení formulářů, jako jsou `CRecordView` je založen na šabloně dialogu pole.

[Cprintinfo –](../mfc/reference/cprintinfo-structure.md)<br/>
Struktury obsahující informace o úloze tisku nebo náhledu tisku. Používá tisk architektuře [CView](../mfc/reference/cview-class.md).

## <a name="see-also"></a>Viz také

[Přehled tříd](../mfc/class-library-overview.md)

