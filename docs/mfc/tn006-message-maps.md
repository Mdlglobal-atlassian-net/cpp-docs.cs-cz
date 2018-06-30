---
title: 'TN006: Zpráva mapy | Microsoft Docs'
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
ms.openlocfilehash: 2c4bc820c6b54e055235c1bd29bd55ccfc032c92
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121673"
---
# <a name="tn006-message-maps"></a>TN006: Mapy zpráv

Tato poznámka popisuje zařízení MFC zpráva mapy.

## <a name="the-problem"></a>Problém

Microsoft Windows implementuje virtuální funkce do třídy oken, které používají svému zasílání zpráv zařízení. Z důvodu velkého počtu zpráv související se situací by poskytuje samostatné virtuální funkci pro každou zprávu Windows vytvořit prohibitively velké vtable.

Vzhledem k tomu, že počet zpráv definované v systému Windows v průběhu času mění, a protože aplikace můžete definovat vlastní zpráv systému Windows, mapy zpráv zadejte úroveň dereference, která zabraňuje rozhraní změny v zastavení existujícího kódu.

## <a name="overview"></a>Přehled

Knihovna MFC poskytuje alternativu k příkazu switch, který se používal v tradiční programy systému Windows pro zpracování zprávy odeslané do časového období. Mapování z zprávy do metod se dá definovat tak, aby po přijetí zprávy pomocí okna odpovídající metoda je volána automaticky. Pokud tuto funkci map zpráv je navržené tak, aby připomínaly virtuální funkce, ale má další výhody není možné s virtuální funkcí jazyka C++.

## <a name="defining-a-message-map"></a>Definování mapy zpráv

[DECLARE_MESSAGE_MAP –](reference/message-map-macros-mfc.md#declare_message_map) Makro deklaruje tři členy pro třídu.

- Soukromé pole položek AFX_MSGMAP_ENTRY názvem *_messageEntries*.

- Chráněná struktura AFX_MSGMAP názvem *messageMap* odkazující *_messageEntries* pole.

- A chráněná virtuální volaná funkce `GetMessageMap` , který vrací adresa *messageMap*.

Toto makro měly být umístěny v deklaraci všechny třídy pomocí mapy zpráv. Podle konvence je na konci deklaraci třídy. Příklad:

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

To je formát generované objekty AppWizard a ClassWizard při vytváření nové třídy. / / {{A / nebo}} závorky jsou potřebné pro ClassWizard.

Mapy zpráv tabulka je definována pomocí sadu makra, která rozšířit, aby položek mapování zpráv. Tabulku začíná [begin_message_map –](reference/message-map-macros-mfc.md#begin_message_map) makro volání, které definuje třídu, která používá tento mapy zpráv a nadřazené třídy, ke které se předávají neošetřené zprávy. V tabulce končí [end_message_map –](reference/message-map-macros-mfc.md#end_message_map) makro volání.

Mezi tyto dvě makro volání je záznam pro každou zprávu zpracovávat tento mapy zpráv. Všechny standardní zprávy Windows mají makro formuláře ON_WM_*MESSAGE_NAME* , generuje položku pro zprávy.

Podpis standardní funkce byla definována pro rozbalování parametry každou zprávu Windows a poskytování bezpečnost typů. Tyto podpisy najdete v souboru Afxwin.h v prohlášení o [CWnd](../mfc/reference/cwnd-class.md). Každé z nich je označené jako klíčové slovo **afx_msg** pro snazší identifikaci.

> [!NOTE]
> ClassWizard vyžaduje, abyste používali **afx_msg** – klíčové slovo v deklaracích zpráva mapování obslužné rutiny.

 Tyto funkce podpisy byly získány pomocí jednoduchého konvence. Název funkce vždy začíná `"On`". Následuje název zpráv systému Windows s "WM_" odebrat a první písmeno každého slova velkými písmeny. Pořadí parametrů je *wParam* následuje `LOWORD`(*lParam*) pak `HIWORD`(*lParam*). Nejsou předány nepoužité parametry. Všechny popisovače, které nejsou zabalené službou MFC – třídy se převedou na odkazy na příslušné objekty MFC. Následující příklad ukazuje, jak zpracovat zpráva WM_PAINT a způsobit, že `CMyWnd::OnPaint` zavolání funkce:

```cpp
BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    //{{AFX_MSG_MAP(CMyWnd)
    ON_WM_PAINT()
    //}}AFX_MSG_MAP
END_MESSAGE_MAP()
```

 V tabulce mapy zpráv musí být definovány mimo obor všechny funkce nebo definice třídy. Nesmí být umístěny v bloku extern "C".

> [!NOTE]
> ClassWizard upraví položek mapy zpráv, ke kterým dochází mezi / / {{a / nebo}} komentář závorky.

## <a name="user-defined-windows-messages"></a>Uživatelem definované zpráv systému Windows

Uživatelsky definované může být součástí mapy zpráv pomocí [on_message –](reference/message-map-macros-mfc.md#on_message) makro. Toto makro přijímá číslo zprávy a metoda ve tvaru:

```cpp
    // inside the class declaration
    afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);

    #define WM_MYMESSAGE (WM_USER + 100)

BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    ON_MESSAGE(WM_MYMESSAGE, OnMyMessage)
END_MESSAGE_MAP()
```

V tomto příkladu jsme vytvořit obslužnou rutinu pro vlastní zprávu, která má odvozený od standardní WM_USER základ pro uživatelsky definované ID zpráv systému Windows. Následující příklad ukazuje způsob volání této obslužné rutiny:

```cpp
CWnd* pWnd = ...;
pWnd->SendMessage(WM_MYMESSAGE);
```

Rozsah definovaný uživatelem zprávy, které tuto metodu použijte, musí být v rozsahu WM_USER do 0x7fff.

> [!NOTE]
> ClassWizard nepodporuje vstup on_message – obslužná rutina rutiny z ClassWizard uživatelského rozhraní. Musíte je ručně zadat v editoru Visual C++. ClassWizard bude analyzovat tyto položky a umožňují procházet je stejně jako všechny ostatní položky map zpráv.

## <a name="registered-windows-messages"></a>Zprávy Windows registrované

[RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947) funkce se používá k definování zprávu nové okno, která se musí být jedinečný v celém systému. On_registered_message – makro slouží ke zpracování těchto zpráv. Toto makro přijímá název *Celé_číslo TÉMĚŘ* proměnné, která obsahuje ID registrované windows zprávy. Příklad

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

Musí být registrovaný proměnná (WM_FIND v tomto příkladu) ID zpráv systému Windows *NEAR* proměnné z důvodu způsob on_registered_message – je implementována.

Rozsah definovaný uživatelem zprávy, které tuto metodu použijte, bude v rozsahu 0xC000 až 0xFFFF.

> [!NOTE]
> ClassWizard nepodporuje vstup on_registered_message – obslužná rutina rutiny z ClassWizard uživatelského rozhraní. Musíte je ručně zadat v textovém editoru. ClassWizard bude analyzovat tyto položky a umožňují procházet je stejně jako všechny ostatní položky map zpráv.

## <a name="command-messages"></a>Příkaz zprávy

Příkaz zprávy z nabídek a akcelerátorů jsou zpracovávány v mapy zpráv s on_command – makro. Toto makro přijme příkaz ID a metodu. Pouze konkrétní wm_command – zprávy, která je *wParam* rovna zadaný příkaz ID zpracováván pomocí metody popsané v položce map zpráv. Funkce člena obslužné rutiny příkazů žádné parametry a vrátí **void**. Makro má následující formát:

```cpp
ON_COMMAND(id, memberFxn)
```

Příkaz update zprávy jsou směrovány prostřednictvím shodný mechanismus, ale místo toho použít on_update_command_ui – makro. Funkce člena obslužné rutiny aktualizace příkazů trvat jeden parametr, odkazy [CCmdUI](../mfc/reference/ccmdui-class.md) objektu a vrátí **void**. Makro obsahuje formulář

```cpp
ON_UPDATE_COMMAND_UI(id, memberFxn)
```

Pokročilí uživatelé mohou použít on_command_ex – makro, což je rozšířená formu obslužné rutiny zpráv příkaz. Makro poskytuje větší on_command – funkce. Rozšířené obslužná rutina příkazu členské funkce trvat jeden parametr, **Celé_číslo** obsahující ID příkazu a vrátí **BOOL**. Návratová hodnota by měla být **TRUE** indikující, že příkaz byla zpracována. Jinak směrování bude pokračovat na další objekty cíl příkazu.

Příklady tyto formuláře:

- Uvnitř Resource.h (obvykle generovaných Visual C++)

    ```cpp
    #define    ID_MYCMD      100
    #define    ID_COMPLEX    101
    ```

- V deklaraci třídy

    ```cpp
    afx_msg void OnMyCommand();
    afx_msg void OnUpdateMyCommand(CCmdUI* pCmdUI);
    afx_msg BOOL OnComplexCommand(UINT nID);
    ```

- V definici mapy zpráv

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

 Pokročilí uživatelé dokáže zpracovat řadu příkazů pomocí jednoduchého příkazu obslužná rutina: [on_command_range –](reference/message-map-macros-mfc.md#on_command_range) nebo on_command_range_ex –. Další informace o těchto makra v dokumentaci produktu.

> [!NOTE]
> ClassWizard podporuje vytváření on_command – a on_update_command_ui – obslužné rutiny, ale nepodporuje vytváření on_command_ex – nebo on_command_range – obslužné rutiny. Třída Průvodce však analyzovat a umožňují procházet všechny čtyři příkaz obslužná rutina variant.

## <a name="control-notification-messages"></a>Zprávy s oznámením ovládacího prvku

Položka mapování zpráv odesílaných z podřízených ovládacích prvků do okna a mít navíc bit informací ve zprávě: ID ovládacího prvku. Obslužná rutina zpráv zadaná při načítání zpráv je volána, pouze v případě, že jsou splněné následující podmínky:

- Kód oznámení ovládacího prvku (vysoké slovo *lParam*), jako je například BN_CLICKED, odpovídá kód oznámení zadané v položce map zpráv.

- ID ovládacího prvku (*wParam*) odpovídá zadané v položce map zpráv ID ovládacího prvku.

Vlastní ovládací prvek zpráv s oznámením mohou používat [on_control –](reference/message-map-macros-mfc.md#on_control) makro definovat položku mapování zprávu s kódem vlastní oznámení. Formulář má tento – makro

```cpp
ON_CONTROL(wNotificationCode, id, memberFxn)
```

Pro rozšířené použití [on_control_range –](reference/message-map-macros-mfc.md#on_control_range) lze zpracovat určitý ovládací prvek oznámení z řadu ovládacích prvků pomocí stejné obslužné rutiny.

> [!NOTE]
> ClassWizard nepodporuje vytvoření obslužné rutiny on_control – nebo on_control_range – v uživatelském rozhraní. Musíte je ručně zadat pomocí textového editoru. ClassWizard bude analyzovat tyto položky a umožňují procházet je stejně jako všechny ostatní položek mapování zpráv.

Běžné ovládací prvky Windows použijte výkonnějšího [wm_notify –](http://msdn.microsoft.com/library/windows/desktop/bb775583) pro oznámení komplexní ovládacího prvku. Tato verze knihovny MFC má přímé podpory pro tuto novou zprávu pomocí ON_NOTIFY a on_notify_range – makra. Další informace o těchto makra v dokumentaci produktu.

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)  
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)  
