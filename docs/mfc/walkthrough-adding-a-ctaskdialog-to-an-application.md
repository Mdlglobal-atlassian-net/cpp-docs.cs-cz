---
title: 'Návod: Přidání objektu CTaskDialog do aplikace'
ms.date: 04/25/2019
helpviewer_keywords:
- CTaskDialog, adding
- walkthroughs [MFC], dialogs
ms.assetid: 3a62abb8-2d86-4bec-bdb8-5784d5f9a9f8
ms.openlocfilehash: 1a46cc7681a2556aee8e856be6ce1fd7cc01686a
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2019
ms.locfileid: "71096032"
---
# <a name="walkthrough-adding-a-ctaskdialog-to-an-application"></a>Návod: Přidání objektu CTaskDialog do aplikace

Tento návod zavádí [třídu objektu CTaskDialog](../mfc/reference/ctaskdialog-class.md) a ukazuje, jak ji přidat do aplikace.

Dialog `CTaskDialog` je dialogové okno úlohy, které nahrazuje okno se zprávou Windows v systému Windows Vista nebo novějším. `CTaskDialog` Vylepšuje původní okno se zprávou a přidává funkce. Okno se zprávou Windows se pořád podporuje v aplikaci Visual Studio.

> [!NOTE]
> Verze systému Windows starší než Windows Vista nepodporují `CTaskDialog`. Pokud chcete zobrazit zprávu uživateli, který spouští vaši aplikaci v dřívější verzi Windows, musíte naprogramovat alternativní dialogová okna. Můžete použít statickou metodu [objektu CTaskDialog:: podporuje](../mfc/reference/ctaskdialog-class.md#issupported) k určení za běhu, zda počítač uživatele může zobrazit `CTaskDialog`. Kromě toho `CTaskDialog` je k dispozici pouze v případě, že je vaše aplikace sestavena pomocí knihovny Unicode.

Nástroj `CTaskDialog` podporuje několik volitelných prvků pro shromáždění a zobrazení informací. `CTaskDialog` Může například zobrazit odkazy na příkazy, přizpůsobená tlačítka, přizpůsobené ikony a zápatí. Má `CTaskDialog` také několik metod, které vám umožňují zadat dotaz na stav dialogového okna úlohy, a určit tak volitelné prvky, které uživatel vybral.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu budete potřebovat následující komponenty:

- Visual Studio 2010 nebo novější

- Windows Vista nebo novější

## <a name="replacing-a-windows-message-box-with-a-ctaskdialog"></a>Výměna okna se zprávou Windows s objektu CTaskDialog

Následující postup ukazuje základní použití `CTaskDialog`nástroje, který má nahradit okno se zprávou systému Windows. Tento příklad také změní ikonu přidruženou k dialogovému oknu úkol. Změna ikony způsobí, že `CTaskDialog` se v okně se zprávou Windows zobrazí stejné.

### <a name="to-replace-a-windows-message-box-with-a-ctaskdialog"></a>Nahrazení okna se zprávou Windows pomocí objektu CTaskDialog

1. Použijte **Průvodce aplikací knihovny MFC** k vytvoření aplikace MFC se všemi výchozími nastaveními. Viz [Návod: Použití nových ovládacích prvků](walkthrough-using-the-new-mfc-shell-controls.md) prostředí MFC pro pokyny k otevření Průvodce pro vaši verzi sady Visual Studio.

1. Zavolejte ho *MyProject*.

1. K otevření souboru MyProject. cpp použijte **Průzkumník řešení** .

1. Přidejte `#include "afxtaskdialog.h"` za seznam zahrnutí.

1. Vyhledejte metodu `CMyProjectApp::InitInstance`. Vložte následující řádky kódu před `return TRUE;` příkaz. Tento kód vytvoří řetězce, které používáme v okně se zprávou Windows nebo v `CTaskDialog`.

    ```cpp
    CString message("My message to the user");
    CString dialogTitle("My Task Dialog title");
    CString emptyString;
    ```

1. Za kód z kroku 4 přidejte následující kód. Tento kód zaručuje, že počítač uživatele podporuje `CTaskDialog`. Pokud se dialogové okno nepodporuje, aplikace místo toho zobrazí okno se zprávou Windows.

    ```cpp
    if (CTaskDialog::IsSupported())
    {

    }
    else
    {
        AfxMessageBox(message);
    }
    ```

1. Vložte následující kód mezi závorky po `if` příkazu z kroku 5. Tento kód vytvoří `CTaskDialog`.

    ```cpp
    CTaskDialog taskDialog(message, emptyString, dialogTitle, TDCBF_OK_BUTTON);
    ```

1. Na dalším řádku přidejte následující kód. Tento kód nastaví ikonu upozornění.

    ```cpp
    taskDialog.SetMainIcon(TD_WARNING_ICON);
    ```

1. Na dalším řádku přidejte následující kód. Tento kód zobrazí dialogové okno úlohy.

    ```cpp
    taskDialog.DoModal();
    ```

Pokud nechcete, `CTaskDialog` aby se zobrazila stejná ikona jako v okně se zprávou Windows, můžete se vyhnout kroku 7. Pokud se tomuto kroku vyhnete, `CTaskDialog` nemá při zobrazení aplikace žádnou ikonu.

Zkompilujte a spusťte aplikaci. Po spuštění aplikace se zobrazí dialogové okno úlohy.

## <a name="adding-functionality-to-the-ctaskdialog"></a>Přidání funkcí do objektu CTaskDialog

Následující postup ukazuje, jak přidat funkce `CTaskDialog` , které jste vytvořili v předchozím postupu. Vzorový kód ukazuje, jak spustit konkrétní pokyny v závislosti na výběru uživatele.

### <a name="to-add-functionality-to-the-ctaskdialog"></a>Přidání funkce do objektu CTaskDialog

1. Přejděte na **prostředky**. Pokud **prostředky**nevidíte, můžete ho otevřít z nabídky **Zobrazit** .

1. Rozbalení **prostředky** , dokud nebudete moci vybrat složku **tabulky řetězců** . Rozbalte ho a dvakrát klikněte na položku **tabulka řetězců** .

1. Posuňte se do dolní části tabulky řetězců a přidejte novou položku. Změňte ID na `TEMP_LINE1`. Nastavte titulek na **příkazový řádek 1**.

1. Přidat další novou položku. Změňte ID na `TEMP_LINE2`. Nastavte titulek na **příkazový řádek 2**.

1. Přejděte zpět na MyProject. cpp.

1. Poté `CString emptyString;`přidejte následující kód:

    ```cpp
    CString expandedLabel("Hide extra information");
    CString collapsedLabel("Show extra information");
    CString expansionInfo("This is the additional information to the user,\nextended over two lines.");
    ```

1. `taskDialog.DoModal()` Vyhledejte příkaz a nahraďte tento příkaz následujícím kódem. Tento kód aktualizuje dialogové okno úlohy a přidá nové ovládací prvky:

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

1. Přidejte následující řádek kódu, který zobrazí dialogové okno úlohy uživateli a získá výběr uživatele:

    ```cpp
    INT_PTR result = taskDialog.DoModal();
    ```

1. Po volání metody `taskDialog.DoModal()`vložte následující kód. Tato část kódu zpracovává vstup uživatele:

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

V kódu v kroku 9 nahraďte komentáře, které začínají `PROCESS IF` kódem, který chcete provést za určitých podmínek.

Zkompilujte a spusťte aplikaci. Aplikace zobrazí dialogové okno úlohy, které používá nové ovládací prvky a další informace.

## <a name="displaying-a-ctaskdialog-without-creating-a-ctaskdialog-object"></a>Zobrazení objektu CTaskDialog bez vytvoření objektu objektu CTaskDialog

Následující postup ukazuje, jak zobrazit a `CTaskDialog` bez předchozího `CTaskDialog` vytvoření objektu. Tento příklad pokračuje v předchozích postupech.

### <a name="to-display-a-ctaskdialog-without-creating-a-ctaskdialog-object"></a>Zobrazení objektu CTaskDialog bez vytvoření objektu objektu CTaskDialog

1. Otevřete soubor MyProject. cpp, pokud již není otevřen.

1. Přejděte na pravou závorku `if (CTaskDialog::IsSupported())` příkazu.

1. Vložte následující kód bezprostředně před uzavírací závorku `if` příkazu ( `else` před blok):

    ```cpp
    HRESULT result2 = CTaskDialog::ShowDialog(L"My error message",
        L"Error",
        L"New Title",
        TEMP_LINE1,
        TEMP_LINE2);
    ```

Zkompilujte a spusťte aplikaci. Aplikace zobrazí dvě dialogová okna úlohy. První dialogové okno je ze sady **pro přidání funkce do objektu CTaskDialog** postupu; druhé dialogové okno se nachází v posledním postupu.

Tyto příklady neukazují všechny dostupné možnosti pro `CTaskDialog`, ale měly by vám pomáhat začít. Úplný popis třídy naleznete v tématu [Třída objektu CTaskDialog](../mfc/reference/ctaskdialog-class.md) .

## <a name="see-also"></a>Viz také:

[Dialogová okna](../mfc/dialog-boxes.md)<br/>
[CTaskDialog – třída](../mfc/reference/ctaskdialog-class.md)<br/>
[CTaskDialog::CTaskDialog](../mfc/reference/ctaskdialog-class.md#ctaskdialog)
