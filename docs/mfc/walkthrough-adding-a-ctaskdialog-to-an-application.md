---
title: 'Návod: Přidání objektu CTaskDialog do aplikace | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CTaskDialog, adding
- walkthroughs [MFC], dialogs
ms.assetid: 3a62abb8-2d86-4bec-bdb8-5784d5f9a9f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0f803af896c1bb2a0e5f58e45f4ef9f588f4e66d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420477"
---
# <a name="walkthrough-adding-a-ctaskdialog-to-an-application"></a>Návod: Přidání objektu CTaskDialog do aplikace

Tento návod představuje [třídy CTaskDialog](../mfc/reference/ctaskdialog-class.md) , se dozvíte, jak je přidat do vaší aplikace.

`CTaskDialog` Je dialogové okno úloh, který nahrazuje okno zpráv Windows ve Windows Vista nebo novější. `CTaskDialog` Zlepšuje původní zprávou a přidá funkce. Okno zpráv Windows je stále podporována v sadě Visual Studio.

> [!NOTE]
> Verzích Windows starších než Windows Vista nepodporují `CTaskDialog`. Možnosti alternativní dialogového okna musí programu, pokud chcete zobrazit zprávu uživateli, který spouští vaši aplikaci na starší verzi Windows. Použijete statickou metodu [CTaskDialog::IsSupported](../mfc/reference/ctaskdialog-class.md#issupported) určit v době běhu, zda počítač uživatele můžete zobrazit `CTaskDialog`. Kromě toho `CTaskDialog` je k dispozici pouze při vytváření vaší aplikace s knihovnou kódování Unicode.

`CTaskDialog` Podporuje několik volitelné prvky k shromáždění a zobrazení informací. Například `CTaskDialog` může zobrazit příkaz odkazy, přizpůsobené tlačítka, vlastní ikony a zápatí. `CTaskDialog` Také obsahuje několik metod, které umožňují dotazování na stav úloh dialogových oken k určení volitelné prvky uživatel vybral.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu budete potřebovat následující komponenty:

- Visual Studio 2010 nebo novější

- Windows Vista nebo novější

## <a name="replacing-a-windows-message-box-with-a-ctaskdialog"></a>Nahrazení objektu CTaskDialog okno se zprávou Windows

Následující postup ukazuje základní použití `CTaskDialog`, který má nahradit okně se zprávou Windows. V tomto příkladu se také změní ikony přidružené k dialogové okno úloh. Změna ikony díky `CTaskDialog` zobrazí stejný jako v okně se zprávou Windows.

### <a name="to-replace-a-windows-message-box-with-a-ctaskdialog"></a>Nahraďte zprávou Windows objektu CTaskDialog

1. Vytvořte nový projekt aplikace knihovny MFC s výchozím nastavením. Pojmenujte ji *MyProject*.

2. Použití **Průzkumníka řešení** k otevření souboru MyProject.cpp.

3. Přidat `#include "afxtaskdialog.h"` po seznam zahrnuje.

4. Najít metodu `CMyProjectApp::InitInstance`. Vložte následující řádky kódu před `return TRUE;` příkazu. Tento kód vytvoří řetězce, které používáme v obou Windows okně se zprávou nebo v `CTaskDialog`.

    ```cpp
    CString message("My message to the user");
    CString dialogTitle("My Task Dialog title");
    CString emptyString;
    ```

5. Přidejte následující kód za kód z kroku 4. Tento kód zaručuje, že počítač uživatele podporuje `CTaskDialog`. Pokud dialogové okno není podporována, zobrazí aplikace Windows okno se zprávou.

    ```cpp
    if (CTaskDialog::IsSupported())
    {

    }
    else
    {
        AfxMessageBox(message);
    }
    ```

6. Vložte následující kód mezi závorkami po `if` příkaz z kroku 5. Tento kód vytvoří `CTaskDialog`.

    ```cpp
    CTaskDialog taskDialog(message, emptyString, dialogTitle, TDCBF_OK_BUTTON);
    ```

7. Na dalším řádku přidejte následující kód. Tento kód nastaví na ikonu upozornění.

    ```cpp
    taskDialog.SetMainIcon(TD_WARNING_ICON);
    ```

8. Na dalším řádku přidejte následující kód. Tento kód zobrazí dialogové okno úlohy.

    ```cpp
    taskDialog.DoModal();
    ```

Krok 7 můžete vynechat, pokud nechcete, aby `CTaskDialog` zobrazit ikonu stejné jako okně se zprávou Windows. Vynecháte-li tento krok `CTaskDialog` nemá žádná ikona, pokud aplikace zobrazí ji.

Kompilace a spuštění aplikace. Aplikace se zobrazí dialogové okno úloh po jeho spuštění.

## <a name="adding-functionality-to-the-ctaskdialog"></a>Přidání funkce objektu CTaskDialog

Následující postup ukazuje, jak přidat funkce, které `CTaskDialog` , kterou jste vytvořili v předchozím postupu. Příklad kódu ukazuje, jak provést konkrétní pokyny na základě výběrů uživatele.

### <a name="to-add-functionality-to-the-ctaskdialog"></a>Přidání funkčnosti do CTaskDialog

1. Přejděte **zobrazení prostředků**. Pokud nevidíte **zobrazení prostředků**, můžete otevřít z **zobrazení** nabídky.

2. Rozbalte **zobrazení prostředků** mohli vybrat **tabulka řetězců** složky. Rozbalte ji a dvakrát klikněte **tabulka řetězců** položka.

3. Posunout na konec tabulky řetězců a přidat novou položku. ID se má změnit `TEMP_LINE1`. Nastavte popisek na **1 příkazového řádku**.

4. Přidejte další novou položku. ID se má změnit `TEMP_LINE2`. Nastavte popisek na **příkazový řádek 2**.

5. Přejděte zpět na MyProject.cpp.

6. Po `CString emptyString;`, přidejte následující kód:

    ```cpp
    CString expandedLabel("Hide extra information");
    CString collapsedLabel("Show extra information");
    CString expansionInfo("This is the additional information to the user,\nextended over two lines.");
    ```

7. Najít `taskDialog.DoModal()` příkaz a nahraďte následující kód, který tento příkaz. Tento kód aktualizuje dialogové okno úloha a přidá nové ovládací prvky:

    ```cpp
    taskDialog.SetMainInstruction(L"Warning");
    taskDialog.SetCommonButtons(
        TDCBF_YES_BUTTON | TDCBF_NO_BUTTON | TDCBF_CANCEL_BUTTON);
    taskDialog.LoadCommandControls(TEMP_LINE1, TEMP_LINE2);
    taskDialog.SetExpansionArea(
        expansionInfo, collapsedLabel, expandedLabel);
    taskDialog.SetFooterText(L"This is the a small footnote to the user");
    taskDialog.SetVerificationCheckboxText(L"Remember your selection");
    ```

8. Přidejte následující řádek kódu, který zobrazí uživateli dialogové okno úloha a načte výběru uživatele:

    ```cpp
    INT_PTR result = taskDialog.DoModal();
    ```

9. Vložte následující kód po volání `taskDialog.DoModal()`. Tato část kódu zpracovává vstup uživatele:

    ```cpp
    if (taskDialog.GetVerificationCheckboxState())
    {
        // PROCESS IF the user selects the verification checkbox
    }

    switch (result)
    {
    case TEMP_LINE1:
        // PROCESS IF the first command line
        break;
    case TEMP_LINE2:
        // PROCESS IF the second command line
        break;
    case IDYES:
        // PROCESS IF the user clicks yes
        break;
    case IDNO:
        // PROCESS IF the user clicks no
        break;
    case IDCANCEL:
        // PROCESS IF the user clicks cancel
        break;
    default:
        // This case should not be hit because closing
        // the dialog box results in IDCANCEL
        break;
    }
    ```

V kódu v kroku 9 Nahraďte komentáře, které začínají IF procesu s kódem, který chcete spustit za zadaných podmínek.

Kompilace a spuštění aplikace. Aplikace se zobrazí dialogové okno úloh, používající nové ovládací prvky a další informace.

## <a name="displaying-a-ctaskdialog-without-creating-a-ctaskdialog-object"></a>Zobrazení objektu CTaskDialog bez vytvoření objektu CTaskDialog

Následující postup ukazuje, jak zobrazit `CTaskDialog` bez vytvoření první `CTaskDialog` objektu. Tento příklad pokračuje v předchozích postupech.

### <a name="to-display-a-ctaskdialog-without-creating-a-ctaskdialog-object"></a>Chcete-li zobrazit objektu CTaskDialog bez vytvoření objektu CTaskDialog

1. Otevřete soubor MyProject.cpp, pokud není otevřen.

2. Přejděte na pravou hranatou závorku pro `if (CTaskDialog::IsSupported())` příkazu.

3. Vložte následující kód bezprostředně před uzavírací závorku `if` – příkaz (před `else` bloku):

    ```cpp
    HRESULT result2 = CTaskDialog::ShowDialog(L"My error message",
        L"Error",
        L"New Title",
        TEMP_LINE1,
        TEMP_LINE2);
    ```

Kompilace a spuštění aplikace. Aplikace zobrazí dvě úlohy dialogových oknech. Dialogové okno první je z k přidání funkce k postupu CTaskDialog; Dialogové okno druhý je v posledním postupu.

Tyto příklady ukazují není k dispozici možnosti pro `CTaskDialog`, ale by měly pomoci vám začít. Zobrazit [třídy CTaskDialog](../mfc/reference/ctaskdialog-class.md) úplný popis třídy.

## <a name="see-also"></a>Viz také:

[Dialogová okna](../mfc/dialog-boxes.md)<br/>
[CTaskDialog – třída](../mfc/reference/ctaskdialog-class.md)<br/>
[CTaskDialog::CTaskDialog](../mfc/reference/ctaskdialog-class.md#ctaskdialog)
