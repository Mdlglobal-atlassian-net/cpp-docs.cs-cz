---
title: 'TN006: Zprávy Maps | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 06/25/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.messages.maps
dev_langs:
- C++
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- ON_NOTIFY_RANGE macro [MFC]
- ON_COMMAND macro [MFC]
- ON_CONTROL_RANGE macro [MFC]
- ON_REGISTERED_MESSAGE macro [MFC]
- ON_NOTIFY message [MFC]
- ON_COMMAND_RANGE_EX macro [MFC]
- ON_MESSAGE macro [MFC]
- Windows messages [MFC], message maps
- ON_COMMAND_RANGE macro [MFC]
- TN006
- ON_CONTROL macro [MFC]
- ON_COMMAND_EX macro [MFC]
- message maps [MFC], Windows messaging
ms.assetid: af4b6794-4b40-4f1e-ad41-603c3b7409bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69aecab15ffb1914dbc8a6a6ae15fca307bc77ef
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386246"
---
# <a name="tn006-message-maps"></a>TN006: Mapy zpráv

Tato poznámka popisuje zařízení mapy zpráv knihovny MFC.

## <a name="the-problem"></a>Problém

Microsoft Windows implementuje virtuální funkce třídy oken, které používají jeho zasílání zpráv zařízení. Z důvodu velkého počtu zpráv, které jsou zapojené poskytuje samostatnou virtuální funkci pro každou zprávu Windows by vznikla nepřekonatelně velké vtable.

Vzhledem k tomu, že počet zpráv definované v systému Windows, které mění v průběhu času, a protože aplikace můžete definovat vlastní zprávy Windows, mapy zpráv zajišťují určitou úroveň dereference, který brání narušení stávajícího kódu rozhraní změny.

## <a name="overview"></a>Přehled

Knihovna MFC poskytuje alternativu k příkazu switch, který byl použit v tradičních aplikacích založených na Windows pro zpracování zprávy odeslané do okna. Mapování ze zprávy do metody může být definován tak, aby při příjmu zprávy podle časového období odpovídající metoda je volána automaticky. Mapování zpráv Azure je navržená tak, aby připomínaly virtuální funkce, ale neobsahuje další výhody, které není možné s virtuální funkcí jazyka C++.

## <a name="defining-a-message-map"></a>Definování mapy zpráv

[DECLARE_MESSAGE_MAP](reference/message-map-macros-mfc.md#declare_message_map) – Makro deklaruje tři členy třídy.

- Privátní pole AFX_MSGMAP_ENTRY položek, které se nazývá *_messageEntries*.

- Chráněná struktura AFX_MSGMAP volá *messageMap* , která odkazuje na *_messageEntries* pole.

- Chráněná virtuální funkce volaná `GetMessageMap` , který vrací adresa *messageMap*.

Toto makro měly být umístěny v deklaraci libovolné třídy pomocí mapy zpráv. Podle konvence je na konci deklarace třídy. Příklad:

```cpp
class CMyWnd : public CMyParentWndClass
{
    // my stuff...

protected:
    //{{AFX_MSG(CMyWnd)
    afx_msg void OnPaint();
    //}}AFX_MSG

    DECLARE_MESSAGE_MAP()
};
```

Toto je má formát generovaný nástrojem AppWizard a ClassWizard při vytváření nových tříd. / / {{A / nebo}} závorky jsou potřeba pro ClassWizard.

Tabulka mapu zpráv je definována s použitím sady makra, která rozbalte položky mapy zpráv. Začíná na tabulku [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) volání makra, která definuje třídu, která zpracovává tuto mapu zpráv a nadřazené třídy, do které se předávají nezpracované zprávy. V tabulce končí [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map) volání makra.

Mezi tyto dva – makro volání je záznam pro každou zprávu zpracovat tuto mapu zpráv. Všechny standardní zprávy Windows je makro formuláře ON_WM_*MESSAGE_NAME* záznam pro tuto zprávu, která generuje.

Signatura standardní funkce je definována pro rozbalení parametry každé zprávy Windows a zajištění bezpečnosti typů. Tyto podpisy lze nalézt v souboru Afxwin.h v prohlášení o [CWnd](../mfc/reference/cwnd-class.md). Každý z nich je označen klíčovým slovem **afx_msg** pro snadnější identifikaci.

> [!NOTE]
> ClassWizard vyžaduje použití **afx_msg** – klíčové slovo v deklaracích zpráva mapování obslužné rutiny.

Tyto funkce podpisy byly získány pomocí jednoduchého konvence. Název funkce vždy začíná `"On`". Následuje název zprávy Windows s "WM_" odebrat a první písmeno každého slova velké. Pořadí parametrů je *wParam* následovaný `LOWORD`(*lParam*) pak `HIWORD`(*lParam*). Nepoužité parametry nejsou předány. Všechny obslužné rutiny, které jsou zabaleny ve třídách knihovny MFC jsou převáděna na ukazatele na odpovídající objekty knihovny MFC. Následující příklad ukazuje, jak zpracovat zprávu WM_PAINT a způsobit, `CMyWnd::OnPaint` zavolání funkce:

```cpp
BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    //{{AFX_MSG_MAP(CMyWnd)
    ON_WM_PAINT()
    //}}AFX_MSG_MAP
END_MESSAGE_MAP()
```

Tabulka mapy zpráv musí být definovány mimo obor všechny funkce nebo definice třídy. By neměl být umístit do bloku extern "C".

> [!NOTE]
> ClassWizard slouží k úpravě položek mapy zpráv, ke kterým dochází mezi / / {{a / nebo}} komentář závorky.

## <a name="user-defined-windows-messages"></a>Uživatelem definované zprávy Windows

Uživatelem definované zprávy může být součástí mapy zpráv pomocí [ON_MESSAGE](reference/message-map-macros-mfc.md#on_message) – makro. Toto makro přijímá číslo zprávy a metodu ve tvaru:

```cpp
    // inside the class declaration
    afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);

    #define WM_MYMESSAGE (WM_USER + 100)

BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    ON_MESSAGE(WM_MYMESSAGE, OnMyMessage)
END_MESSAGE_MAP()
```

V tomto příkladu jsme navázat obslužnou rutinu pro vlastní zprávu, která má ID zpráv Windows odvozený od standardního WM_USER základ pro uživatelem definované zprávy. Následující příklad ukazuje, jak volat tuto obslužnou rutinu:

```cpp
CWnd* pWnd = ...;
pWnd->SendMessage(WM_MYMESSAGE);
```

Rozsah definovaný uživatelem zprávy, které tuto metodu použijte, musí být v rozsahu WM_USER do 0x7fff.

> [!NOTE]
> ClassWizard nepodporuje zadání rutiny obslužná rutina ON_MESSAGE z uživatelského rozhraní ClassWizard. Musíte je ručně zadat z editoru Visual C++. ClassWizard bude parsovat tyto položky a umožňují procházet stejně jako všechny ostatní položky mapování zpráv.

## <a name="registered-windows-messages"></a>Zprávy Windows registrované

[RegisterWindowMessage](https://msdn.microsoft.com/library/windows/desktop/ms644947) funkce se používá k definování novou zprávu okna, která je zaručeně jedinečná v celém systému. ON_REGISTERED_MESSAGE makro se používá ke zpracování těchto zpráv. Toto makro přijímá název *UINT TÉMĚŘ* proměnnou, která obsahuje windows registrované ID zprávy. Příklad

```cpp
class CMyWnd : public CMyParentWndClass
{
public:
    CMyWnd();

    //{{AFX_MSG(CMyWnd)
    afx_msg LRESULT OnFind(WPARAM wParam, LPARAM lParam);
    //}}AFX_MSG

    DECLARE_MESSAGE_MAP()
};

static UINT NEAR WM_FIND = RegisterWindowMessage("COMMDLG_FIND");

BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    //{{AFX_MSG_MAP(CMyWnd)
    ON_REGISTERED_MESSAGE(WM_FIND, OnFind)
    //}}AFX_MSG_MAP
END_MESSAGE_MAP()
```

Musí být registrované proměnná ID zprávy Windows (WM_FIND v tomto příkladu) *NEAR* proměnné vzhledem ke způsobu ON_REGISTERED_MESSAGE je implementováno.

Rozsah definovaný uživatelem zpráv, které tuto metodu použijte, bude v rozsahu 0xC000 do 0xFFFF.

> [!NOTE]
> ClassWizard nepodporuje zadání rutiny obslužná rutina ON_REGISTERED_MESSAGE z uživatelského rozhraní ClassWizard. Musíte je ručně zadat v textovém editoru. ClassWizard bude parsovat tyto položky a umožňují procházet stejně jako všechny ostatní položky mapování zpráv.

## <a name="command-messages"></a>Zprávy příkazů

Příkaz zprávy z nabídek a akcelerátorů jsou zpracovány v mapy zpráv s ON_COMMAND – makro. Toto makro přijímá ID příkazu a metody. Pouze konkrétní wm_command – zprávy, který má *wParam* rovna zadaný příkaz ID zařizuje služba metody popsané v položce mapování zprávy. Členské funkce obslužné rutiny příkazů nemít žádné parametry a vrátí **void**. Makro má následující formát:

```cpp
ON_COMMAND(id, memberFxn)
```

Příkaz update zprávy se směrují prostřednictvím shodný mechanismus, ale místo toho použijte ON_UPDATE_COMMAND_UI – makro. Příkaz update obslužná rutina členské funkce přijímají jediný parametr, ukazatel [ccmdui –](../mfc/reference/ccmdui-class.md) objekt a vracet **void**. Makro má tvar

```cpp
ON_UPDATE_COMMAND_UI(id, memberFxn)
```

Pokročilí uživatelé mohou použít ON_COMMAND_EX – makro, což je rozšířený formát obslužné rutiny zprávy příkazů. Makro nabízí nadmnožinu funkcí ON_COMMAND. Rozšířené obslužná rutina příkazu členské funkce přijímají jediný parametr, **UINT** , která obsahuje Identifikátor příkazu a vrátit **BOOL**. Návratová hodnota by měla být **TRUE** k označení, že příkaz byla zpracována. Jinak směrování bude pokračovat na další příkaz cílové objektů.

Příklady z těchto forem:

- Uvnitř Resource.h (obvykle generované Visual C++)

    ```cpp
    #define    ID_MYCMD      100
    #define    ID_COMPLEX    101
    ```

- Uvnitř deklarace třídy

    ```cpp
    afx_msg void OnMyCommand();
    afx_msg void OnUpdateMyCommand(CCmdUI* pCmdUI);
    afx_msg BOOL OnComplexCommand(UINT nID);
    ```

- Uvnitř definice map zpráv

    ```cpp
    ON_COMMAND(ID_MYCMD, OnMyCommand)
    ON_UPDATE_COMMAND_UI(ID_MYCMD, OnUpdateMyCommand)
    ON_COMMAND_EX(ID_MYCMD, OnComplexCommand)
    ```

- V souboru implementace

    ```cpp
    void CMyClass::OnMyCommand()
    {
        // handle the command
    }

    void CMyClass::OnUpdateMyCommand(CCmdUI* pCmdUI)
    {
        // set the UI state with pCmdUI
    }

    BOOL CMyClass::OnComplexCommand(UINT nID)
    {
        // handle the command
        return TRUE;
    }
    ```

Pokročilí uživatelé dokáže zpracovat celou řadu příkazů pomocí jednoho příkazu rutiny: [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range) nebo ON_COMMAND_RANGE_EX. Další informace o těchto makrech v dokumentaci produktu.

> [!NOTE]
> ClassWizard podporuje vytváření ON_COMMAND a ON_UPDATE_COMMAND_UI obslužné rutiny, ale nepodporuje vytváření ON_COMMAND_EX nebo ON_COMMAND_RANGE obslužné rutiny. Průvodce třídami však bude parsovat a umožňují procházet všechny varianty obslužná rutina příkazu čtyři.

## <a name="control-notification-messages"></a>Zprávy s oznámením ovládacího prvku

Položka mapy zprávy odeslané z podřízených ovládacích prvků do okna mít speciální bit informací ve zprávě: ID ovládacího prvku. Obslužná rutina zprávy zadaný v položku mapování zpráv je volána, pouze pokud jsou splněny následující podmínky:

- Kód oznámení ovládacího prvku (vysoká slova *lParam*), jako je například BN_CLICKED, odpovídá oznámení kód určený v záznamu map zpráv.

- ID ovládacího prvku (*wParam*) odpovídá ID ovládacího prvku, který je zadán v mapování zprávy položce.

Použít vlastní ovládací prvek zpráv s oznámením [ON_CONTROL](reference/message-map-macros-mfc.md#on_control) – makro definovat položku mapování zprávu s kódem vlastní oznámení. Toto makro má tvar

```cpp
ON_CONTROL(wNotificationCode, id, memberFxn)
```

Pokročilé využití [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range) je možné zpracovat oznámení určitý ovládací prvek z celou řadu ovládacích prvků se stejnou obslužnou rutinu.

> [!NOTE]
> ClassWizard nepodporuje vytvoření obslužné rutiny ON_CONTROL nebo ON_CONTROL_RANGE v uživatelském rozhraní. Musíte je ručně zadat v textovém editoru. ClassWizard bude parsovat tyto položky a umožňují procházet stejně jako všechny ostatní položky mapování zprávy.

Použití běžných ovládacích prvků Windows výkonnějšího [WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583) pro komplexní řízení oznámení. Tato verze knihovny MFC má přímou podporu pro tuto novou zprávu pomocí ON_NOTIFY a on_notify_range – makra. Další informace o těchto makrech v dokumentaci produktu.

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
