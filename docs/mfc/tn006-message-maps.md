---
title: 'TN006: Mapy zpráv'
ms.date: 06/25/2018
f1_keywords:
- vc.messages.maps
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
ms.openlocfilehash: 489db046910cc4b44e381b3f9056cfe8f8b7ccfa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511116"
---
# <a name="tn006-message-maps"></a>TN006: Mapy zpráv

Tato poznámka popisuje zařízení mapy zpráv knihovny MFC.

## <a name="the-problem"></a>Problém

Systém Microsoft Windows implementuje virtuální funkce v oknech třídy, které používají své zařízení pro zasílání zpráv. Kvůli velkému počtu zpráv, které zajišťují samostatné virtuální funkce pro každou zprávu Windows, by se vytvořila samostatná Velká tabulka vtable.

Vzhledem k tomu, že počet systémem definovaných zpráv systému Windows se v průběhu času mění a protože aplikace mohou definovat vlastní zprávy systému Windows, poskytují mapy zpráv úroveň dereference, která zabraňuje změnám rozhraní v přerušení stávajícího kódu.

## <a name="overview"></a>Přehled

Knihovna MFC poskytuje alternativu k příkazu switch, který byl použit v tradičních aplikacích pro systém Windows ke zpracování zpráv odesílaných do okna. Mapování zpráv na metody lze definovat tak, aby při přijetí zprávy oknem bylo odpovídající metoda volána automaticky. Toto zařízení pro mapování zpráv je navrženo tak, aby bylo podobné virtuálním funkcím, ale C++ má další výhody, které s virtuálními funkcemi nejsou možné.

## <a name="defining-a-message-map"></a>Definování mapy zpráv

Makro [DECLARE_MESSAGE_MAP](reference/message-map-macros-mfc.md#declare_message_map) deklaruje tři členy třídy.

- Soukromé pole AFX_MSGMAP_ENTRYch záznamů s názvem *_messageEntries*.

- Chráněná struktura AFX_MSGMAP s názvem *messageMap* , která odkazuje na pole *_messageEntries* .

- Chráněná virtuální funkce s `GetMessageMap` názvem, která vrací adresu *messageMap*.

Toto makro by mělo být vloženo do deklarace jakékoli třídy pomocí map zpráv. Podle konvence je na konci deklarace třídy. Příklad:

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

Jedná se o formát generovaný AppWizard a ClassWizard při vytváření nových tříd. Závorky//{{a/}} jsou potřeba pro ClassWizard.

Tabulka mapy zpráv je definována pomocí sady maker, které se rozbalí na položky mapování zpráv. Tabulka začíná voláním makra [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) , které definuje třídu, která je zpracována touto mapou zprávy, a nadřazenou třídou, do které jsou předány neošetřené zprávy. Tabulka končí voláním makra [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map) .

Mezi těmito dvěma voláními makra je položka pro každou zprávu, kterou má tato mapa zpráv zpracovat. Každá standardní zpráva Windows má makro ON_WM_*MESSAGE_NAME* , které generuje položku pro tuto zprávu.

Byl definován podpis standardní funkce pro rozbalení parametrů každé zprávy systému Windows a zajištění bezpečnosti typů. Tyto signatury lze nalézt v souboru afxwin. h v deklaraci [CWnd](../mfc/reference/cwnd-class.md). Každá z nich je označena klíčovým slovem **afx_msg** pro snadnější identifikaci.

> [!NOTE]
> ClassWizard vyžaduje, abyste v deklaracích obslužných rutin mapování zpráv používali klíčové slovo **afx_msg** .

Signatury těchto funkcí byly odvozeny pomocí jednoduché konvence. Název funkce vždy začíná `"On`řetězcem ". Následuje název zprávy Windows s odebraným "WM_" a první písmeno každého slova na velká písmena. Pořadí parametrů je *wParam* `LOWORD`následované (*lParam*) Then `HIWORD`(*lParam*). Nepoužité parametry nejsou předány. Všechny obslužné rutiny, které jsou zabaleny pomocí tříd knihovny MFC, jsou převedeny na ukazatele na příslušné objekty knihovny MFC. Následující příklad ukazuje, jak zpracovat zprávu WM_PAINT a způsobit `CMyWnd::OnPaint` volání funkce:

```cpp
BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    //{{AFX_MSG_MAP(CMyWnd)
    ON_WM_PAINT()
    //}}AFX_MSG_MAP
END_MESSAGE_MAP()
```

Tabulka map zpráv musí být definována mimo rozsah jakékoli definice funkce nebo třídy. Neměl by být umístěn v externím bloku "C".

> [!NOTE]
> ClassWizard změní položky mapování zpráv, ke kterým dochází v závorkách//{{a//}}.

## <a name="user-defined-windows-messages"></a>Uživatelem definované zprávy systému Windows

Uživatelem definované zprávy mohou být součástí mapy zpráv pomocí makra [ON_MESSAGE](reference/message-map-macros-mfc.md#on_message) . Toto makro přijme číslo zprávy a metodu formuláře:

```cpp
    // inside the class declaration
    afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);

    #define WM_MYMESSAGE (WM_USER + 100)

BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    ON_MESSAGE(WM_MYMESSAGE, OnMyMessage)
END_MESSAGE_MAP()
```

V tomto příkladu vytvoříme obslužnou rutinu pro vlastní zprávu, která má ID zprávy Windows odvozené ze standardního základu WM_USER pro uživatelem definované zprávy. Následující příklad ukazuje, jak zavolat tuto obslužnou rutinu:

```cpp
CWnd* pWnd = ...;
pWnd->SendMessage(WM_MYMESSAGE);
```

Rozsah uživatelem definovaných zpráv, které používají tento přístup, musí být v rozsahu WM_USER až 0x7FFF.

> [!NOTE]
> ClassWizard nepodporuje zadávání rutin obslužných rutin ON_MESSAGE z uživatelského rozhraní ClassWizard. Je nutné je zadat ručně z vizuálního C++ editoru. ClassWizard bude tyto položky analyzovat a umožní vám jejich procházení stejně jako jiné položky v mapě zpráv.

## <a name="registered-windows-messages"></a>Registrované zprávy systému Windows

Funkce [RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew) slouží k definování nové zprávy okna, u které je zaručeno, že bude v celém systému jedinečný. Makro ON_REGISTERED_MESSAGE slouží ke zpracování těchto zpráv. Toto makro přijme název proměnné *uint poblíž* , která obsahuje registrované ID zprávy systému Windows. Příklad

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

Registrovaná proměnná ID zprávy systému Windows (WM_FIND v tomto příkladu) musí být *poblíž* proměnné, protože je implementován způsob, jakým je implementováno ON_REGISTERED_MESSAGE.

Rozsah uživatelem definovaných zpráv, které používají tento přístup, bude v rozsahu 0xC000 až 0xFFFF.

> [!NOTE]
> ClassWizard nepodporuje zadávání rutin obslužných rutin ON_REGISTERED_MESSAGE z uživatelského rozhraní ClassWizard. Je nutné je ručně zadat z textového editoru. ClassWizard bude tyto položky analyzovat a umožní vám jejich procházení stejně jako jiné položky v mapě zpráv.

## <a name="command-messages"></a>Zprávy příkazů

Zprávy příkazů z nabídek a akcelerátorů jsou zpracovávány v mapách zpráv pomocí makra ON_COMMAND. Toto makro přijímá ID příkazu a metodu. Pouze konkrétní zpráva WM_COMMAND, která má *wParam* shodná se zadaným ID příkazu, je zpracována metodou určenou v položce mapování zpráv. Členské funkce obslužné rutiny příkazu nevyužívají žádné parametry a vracejí **typ void**. Makro má následující tvar:

```cpp
ON_COMMAND(id, memberFxn)
```

Zprávy o aktualizacích příkazu jsou směrovány stejným mechanismem, ale místo toho použijte Makro ON_UPDATE_COMMAND_UI. Členské funkce obslužné rutiny aktualizačního příkazu mají jeden parametr, ukazatel na objekt [CCmdUI –](../mfc/reference/ccmdui-class.md) a vracejí **typ void**. Makro má formulář

```cpp
ON_UPDATE_COMMAND_UI(id, memberFxn)
```

Pokročilí uživatelé mohou používat makro ON_COMMAND_EX, což je rozšířená forma obslužných rutin zpráv příkazu. Makro poskytuje nadmnožinu funkcí ON_COMMAND. Rozšířené funkce členů obslužných rutin příkazu mají jeden parametr, typ **uint** , který obsahuje ID příkazu, a vrací **bool**. Návratová hodnota by měla být **true** , aby označovala, že byl příkaz zpracován. V opačném případě bude směrování pokračovat dalšími cílovými objekty příkazu.

Příklady těchto forem:

- Uvnitř Resource. h (obvykle generované pomocí vizuálu C++)

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

- Uvnitř definice mapy zpráv

    ```cpp
    ON_COMMAND(ID_MYCMD, OnMyCommand)
    ON_UPDATE_COMMAND_UI(ID_MYCMD, OnUpdateMyCommand)
    ON_COMMAND_EX(ID_MYCMD, OnComplexCommand)
    ```

- V implementačním souboru

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

Pokročilí uživatelé mohou zpracovat rozsah příkazů pomocí jediné obslužné rutiny příkazu: [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range) nebo ON_COMMAND_RANGE_EX. Další informace o těchto makrech najdete v dokumentaci k produktu.

> [!NOTE]
> ClassWizard podporuje vytváření obslužných rutin ON_COMMAND a ON_UPDATE_COMMAND_UI, ale nepodporuje vytváření obslužných rutin ON_COMMAND_EX nebo ON_COMMAND_RANGE. Průvodce třídami ale bude analyzovat a umožní vám procházet všechny čtyři varianty obslužných rutin příkazu.

## <a name="control-notification-messages"></a>Řízení zpráv s oznámením

Zprávy, které jsou odeslány z podřízených ovládacích prvků do okna, mají další bitovou informaci ve své položce mapování zpráv: ID ovládacího prvku. Obslužná rutina zprávy zadaná v položce mapování zpráv je volána pouze v případě, že jsou splněny následující podmínky:

- Kód oznámení ovládacího prvku (vysoké slovo *lParam*), například BN_CLICKED, odpovídá kódu oznámení uvedenému v položce mapování zpráv.

- ID ovládacího prvku (*wParam*) odpovídá ID ovládacího prvku zadaného v položce mapování zpráv.

Zprávy s oznámením vlastního ovládacího prvku mohou použít makro [ON_CONTROL](reference/message-map-macros-mfc.md#on_control) k definování položky mapování zpráv s vlastním kódem oznámení. Toto makro má formulář

```cpp
ON_CONTROL(wNotificationCode, id, memberFxn)
```

Pro pokročilé použití [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range) lze použít ke zpracování konkrétního oznámení ovládacího prvku z řady ovládacích prvků pomocí stejné obslužné rutiny.

> [!NOTE]
> ClassWizard nepodporuje vytváření obslužných rutin ON_CONTROL nebo ON_CONTROL_RANGE v uživatelském rozhraní. Je nutné je ručně zadat pomocí textového editoru. ClassWizard bude tyto položky analyzovat a umožní vám jejich procházení stejně jako jakékoli jiné položky mapování zpráv.

Běžné ovládací prvky Windows využívají výkonnější [WM_NOTIFY](/windows/win32/controls/wm-notify) pro komplexní oznámení o řízení. Tato verze knihovny MFC má přímou podporu této nové zprávy pomocí maker ON_NOTIFY a ON_NOTIFY_RANGE. Další informace o těchto makrech najdete v dokumentaci k produktu.

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
