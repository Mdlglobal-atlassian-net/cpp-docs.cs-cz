---
title: 'Návod: Přidání objektu CTaskDialog do aplikace | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CTaskDialog, adding
- walkthroughs [MFC], dialogs
ms.assetid: 3a62abb8-2d86-4bec-bdb8-5784d5f9a9f8
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7b0d820b45b85b5dc20e82cb647c05f839e7ab41
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="walkthrough-adding-a-ctaskdialog-to-an-application"></a>Návod: Přidání objektu CTaskDialog do aplikace
Tento návod představuje [CTaskDialog třída](../mfc/reference/ctaskdialog-class.md) a ukazuje, jak přidat do vaší aplikace.  
  
 `CTaskDialog` Je dialogové okno úloh, který nahrazuje pole zpráv systému Windows v systému Windows Vista nebo novější. `CTaskDialog` Zlepšuje původní zprávou a přidá funkce. Pole zpráv systému Windows se pořád podporuje v sadě Visual Studio.  
  
> [!NOTE]
> Verzích Windows starších než Windows Vista nepodporují `CTaskDialog`. Možnost v dialogovém okně alternativní musí programu, pokud chcete zobrazit zprávu pro uživatele, který spouští aplikaci ve starší verzi systému Windows. Můžete použít statickou metodu [CTaskDialog::IsSupported](../mfc/reference/ctaskdialog-class.md#issupported) k určení za běhu, zda počítač uživatele můžete zobrazit `CTaskDialog`. Kromě toho `CTaskDialog` je k dispozici pouze když je aplikace vytvořené s knihovnou kódování Unicode.  
  
 `CTaskDialog` Podporuje několik volitelné prvky shromažďovat a zobrazovat informace. Například `CTaskDialog` může zobrazit příkaz odkazy, přizpůsobené tlačítka, přizpůsobené ikony a zápatí. `CTaskDialog` Také obsahuje několik metod, které vám umožní dotazování na stav dialogové okno úlohy, ve kterém lze určit, které volitelné prvky vybraného uživatele.  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
- Visual Studio 2010 nebo novější  
  
- Windows Vista nebo novější  
  
## <a name="replacing-a-windows-message-box-with-a-ctaskdialog"></a>Nahrazení objektu CTaskDialog systému Windows se zprávou  
 Následující postup předvádí nejzákladnější použití `CTaskDialog`, což je nahradit pole zpráv systému Windows. Tento příklad také změní ikony přidružené dialogové okno úloh. Změna na ikonu umožňuje `CTaskDialog` vypadají stejně do pole zpráv systému Windows.  
  
#### <a name="to-replace-a-windows-message-box-with-a-ctaskdialog"></a>Chcete nahradit objektu CTaskDialog systému Windows se zprávou  
  
1.  Vytvořte nový projekt aplikace knihovny MFC s výchozím nastavením. Volání `MyProject`.  
  
2.  Použití **Průzkumníku řešení** k otevření souboru MyProject.cpp.  
  
3.  Přidat `#include "afxtaskdialog.h"` po seznam obsahuje.  
  
4.  Najít metodu `CMyProjectApp::InitInstance`. Vložte následující řádky kódu před `return TRUE;` příkaz. Tento kód vytvoří řetězce, které používáme buď do pole zpráv systému Windows nebo ve `CTaskDialog`.  
  
 ```  
    CString message("My message to the user");

    CString dialogTitle("My Task Dialog title");

    CString emptyString;  
 ```  
  
5.  Přidejte následující kód po kód z kroku 4. Tento kód zaručuje, že počítač uživatele podporuje `CTaskDialog`. Pokud dialogu není podporován, zobrazí aplikace systému Windows se zprávou.  
  
 ```  
    if (CTaskDialog::IsSupported())  
 {  
 
 }  
    else 
 {  
    AfxMessageBox(message);

 }  
 ```  
  
6.  Vložte následující kód do závorek po `if` příkaz z kroku 5. Tento kód vytvoří `CTaskDialog`.  
  
 ```  
    CTaskDialog taskDialog(message,
    emptyString,
    dialogTitle,
    TDCBF_OK_BUTTON);

 ```  
  
7.  Na následujícím řádku přidejte následující kód. Tento kód nastaví ikona upozornění.  
  
 ```  
    taskDialog.SetMainIcon(TD_WARNING_ICON);

 ```  
  
8.  Na následujícím řádku přidejte následující kód. Tento kód zobrazí dialogové okno úloh.  
  
 ```  
    taskDialog.DoModal();

 ```  
  
 Krok 7 můžete vynechat, pokud nechcete, aby `CTaskDialog` zobrazíte ikonu stejné jako systému Windows se zprávou. Pokud není tento krok `CTaskDialog` nemá žádná ikona, pokud se aplikace zobrazí ho.  
  
 Zkompilování a spuštění aplikace. Aplikace se zobrazí dialogové okno úloha po jeho spuštění.  
  
## <a name="adding-functionality-to-the-ctaskdialog"></a>Přidání funkcí do objektu CTaskDialog  
 Následující postup ukazuje, jak přidat funkce `CTaskDialog` kterou jste vytvořili v předchozím postupu. Příklad kódu ukazuje, jak provádět konkrétní instrukce podle volby uživatele.  
  
#### <a name="to-add-functionality-to-the-ctaskdialog"></a>Objektu CTaskDialog přidat další funkce  
  
1.  Přejděte na **zobrazení prostředků**. Pokud nevidíte **zobrazení prostředků**, můžete otevřít z **zobrazení** nabídky.  
  
2.  Rozbalte **zobrazení prostředků** dokud můžete vybrat **tabulky řetězců** složky. Rozbalte ho a dvakrát klikněte na **tabulky řetězců** položku.  
  
3.  Přejděte k dolnímu okraji řetězec tabulku a přidat novou položku. Změnit ID na `TEMP_LINE1`. Nastavte popisek na **1 příkazového řádku**.  
  
4.  Přidejte další novou položku. Změnit ID na `TEMP_LINE2`. Nastavte popisek na **příkazového řádku 2**.  
  
5.  Přejděte zpět do MyProject.cpp.  
  
6.  Po `CString emptyString;`, přidejte následující kód:  
  
 ```  
    CString expandedLabel("Hide extra information");

    CString collapsedLabel("Show extra information");

    CString expansionInfo("This is the additional information to the user,\nextended over two lines.");

 ```  
  
7.  Najít `taskDialog.DoModal()` prohlášení a tento příkaz nahraďte následujícím kódem. Tento kód aktualizuje dialogové okno úloha a přidá nové ovládací prvky:  
  
 ```  
    taskDialog.SetMainInstruction(L"Warning");

 taskDialog.SetCommonButtons(TDCBF_YES_BUTTON | TDCBF_NO_BUTTON | TDCBF_CANCEL_BUTTON);

    taskDialog.LoadCommandControls(TEMP_LINE1,
    TEMP_LINE2);

    taskDialog.SetExpansionArea(expansionInfo,
    collapsedLabel,
    expandedLabel);

    taskDialog.SetFooterText(L"This is the a small footnote to the user");

    taskDialog.SetVerificationCheckboxText(L"Remember your selection");

 ```  
  
8.  Přidejte následující řádek kódu, který se zobrazí dialogové okno úloh pro uživatele a načte výběr uživatele:  
  
 ```  
    INT_PTR result = taskDialog.DoModal();

 ```  
  
9. Vložte následující kód po volání `taskDialog.DoModal()`. Tato část kódu zpracovává vstup uživatele:  
  
 ```  
    if (taskDialog.GetVerificationCheckboxState())  
 { *// PROCESS IF the user selects the verification checkbox   
 }  
 
    switch (result)  
 {  
    case TEMP_LINE1: *// PROCESS IF the first command line  
    break; 
    case TEMP_LINE2: *// PROCESS IF the second command line  
    break; 
    case IDYES: *// PROCESS IF the user clicks yes  
    break; 
    case IDNO: *// PROCESS IF the user clicks no  
    break; 
    case IDCANCEL: *// PROCESS IF the user clicks cancel  
    break; 
    default: *// This case should not be hit because closing the dialog box results in IDCANCEL  
    break; 
 }  
 ```  
  
 V kódu v kroku 9 Nahraďte komentáře, které začínají procesu, pokud se kód, který má být proveden za zadaných podmínek.  
  
 Zkompilování a spuštění aplikace. Aplikace zobrazí dialogové okno úloha, která využívá nové ovládací prvky a další informace.  
  
## <a name="displaying-a-ctaskdialog-without-creating-a-ctaskdialog-object"></a>Zobrazení objektu CTaskDialog bez vytvoření objektu CTaskDialog  
 Následující postup ukazuje, jak zobrazit `CTaskDialog` bez vytvoření první `CTaskDialog` objektu. Tento příklad pokračuje v předchozích postupech.  
  
#### <a name="to-display-a-ctaskdialog-without-creating-a-ctaskdialog-object"></a>Chcete-li zobrazit objektu CTaskDialog bez vytvoření objektu CTaskDialog  
  
1.  Pokud není otevřený, otevřete soubor MyProject.cpp.  
  
2.  Přejděte na pravou hranatou závorku pro `if (CTaskDialog::IsSupported())` příkaz.  
  
3.  Vložte následující kód bezprostředně před uzavírací závorku `if` – příkaz (před `else` bloku):  
  
 ```  
    HRESULT result2 = CTaskDialog::ShowDialog(L"My error message",
    L"Error",
    L"New Title",
    TEMP_LINE1,
    TEMP_LINE2);

 ```  
  
 Zkompilování a spuštění aplikace. Aplikace zobrazí dvě úlohy dialogových oken. První dialogové okno je z k přidání funkce do objektu CTaskDialog postupu; druhé dialogové okno je v posledním postupu.  
  
 Tyto příklady ukazují není k dispozici možnosti pro `CTaskDialog`, ale měli vám pomůže začít. V tématu [CTaskDialog třída](../mfc/reference/ctaskdialog-class.md) úplný popis třídy.  
  
## <a name="see-also"></a>Viz také  
 [Dialogová okna](../mfc/dialog-boxes.md)   
 [Třída objektu CTaskDialog](../mfc/reference/ctaskdialog-class.md)   
 [CTaskDialog::CTaskDialog](../mfc/reference/ctaskdialog-class.md#ctaskdialog)

