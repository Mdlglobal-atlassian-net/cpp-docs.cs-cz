---
title: Třída CLinkCtrl
ms.date: 11/04/2016
f1_keywords:
- CLinkCtrl
- AFXCMN/CLinkCtrl
- AFXCMN/CLinkCtrl::CLinkCtrl
- AFXCMN/CLinkCtrl::Create
- AFXCMN/CLinkCtrl::CreateEx
- AFXCMN/CLinkCtrl::GetIdealHeight
- AFXCMN/CLinkCtrl::GetIdealSize
- AFXCMN/CLinkCtrl::GetItem
- AFXCMN/CLinkCtrl::GetItemID
- AFXCMN/CLinkCtrl::GetItemState
- AFXCMN/CLinkCtrl::GetItemUrl
- AFXCMN/CLinkCtrl::HitTest
- AFXCMN/CLinkCtrl::SetItem
- AFXCMN/CLinkCtrl::SetItemID
- AFXCMN/CLinkCtrl::SetItemState
- AFXCMN/CLinkCtrl::SetItemUrl
helpviewer_keywords:
- CLinkCtrl [MFC], CLinkCtrl
- CLinkCtrl [MFC], Create
- CLinkCtrl [MFC], CreateEx
- CLinkCtrl [MFC], GetIdealHeight
- CLinkCtrl [MFC], GetIdealSize
- CLinkCtrl [MFC], GetItem
- CLinkCtrl [MFC], GetItemID
- CLinkCtrl [MFC], GetItemState
- CLinkCtrl [MFC], GetItemUrl
- CLinkCtrl [MFC], HitTest
- CLinkCtrl [MFC], SetItem
- CLinkCtrl [MFC], SetItemID
- CLinkCtrl [MFC], SetItemState
- CLinkCtrl [MFC], SetItemUrl
ms.assetid: d1cd876a-ecca-42db-8ac4-9cd327df0cd4
ms.openlocfilehash: aa1f630b448c60a0eeb6a905ed6eef6f84a2ff8c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372253"
---
# <a name="clinkctrl-class"></a>Třída CLinkCtrl

Poskytuje funkce běžného ovládacího prvku Windows SysLink.

## <a name="syntax"></a>Syntaxe

```
class CLinkCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CLinkCtrl::CLinkCtrl](#clinkctrl)|Vytvoří `CLinkCtrl` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CLinkCtrl::Vytvořit](#create)|Vytvoří ovládací prvek propojení a `CLinkCtrl` připojí jej k objektu.|
|[CLinkCtrl::CreateEx](#createex)|Vytvoří ovládací prvek propojení s rozšířenými `CLinkCtrl` styly a připojí ho k objektu.|
|[CLinkCtrl::GetIdealHeight](#getidealheight)|Načte ideální výšku ovládacího prvku propojení.|
|[CLinkCtrl::GetIdealSize](#getidealsize)|Vypočítá upřednostňovanou výšku textu propojení pro aktuální ovládací prvek propojení v závislosti na zadané šířce propojení.|
|[CLinkCtrl::GetItem](#getitem)|Načte stavy a atributy položky ovládacího prvku propojení.|
|[clinkctrl::GetItemID](#getitemid)|Načte ID položky ovládacího prvku propojení.|
|[CLinkCtrl::GetItemState](#getitemstate)|Načte stav položky ovládacího prvku propojení.|
|[CLinkCtrl::GetItemUrl](#getitemurl)|Načte adresu URL reprezentovanou položkou ovládacího prvku odkazu.|
|[CLinkCtrl::HitTest](#hittest)|Určuje, zda uživatel klepnul na zadaný odkaz.|
|[CLinkCtrl::SetItem](#setitem)|Nastaví stavy a atributy položky ovládacího prvku propojení.|
|[clinkctrl::SetItemID](#setitemid)|Nastaví ID položky ovládacího prvku propojení.|
|[CLinkCtrl::SetItemState](#setitemstate)|Nastaví stav položky ovládacího prvku propojení.|
|[CLinkCtrl::SetItemUrl](#setitemurl)|Nastaví adresu URL reprezentovanou položkou ovládacího prvku odkazu.|

## <a name="remarks"></a>Poznámky

"Ovládací prvek propojení" poskytuje pohodlný způsob, jak vložit hypertextové odkazy v okně. Skutečný ovládací prvek je okno, které vykresluje označený text a spouští příslušné aplikace, když uživatel klepne na vložený odkaz. Více odkazů jsou podporovány v rámci jednoho ovládacího prvku a lze přistupovat pomocí indexu založeného na nule.

Tento ovládací prvek `CLinkCtrl` (a tedy třída) je k dispozici pouze pro programy spuštěné v systému Windows XP a novější.

Další informace naleznete v [tématu SysLink Control](/windows/win32/Controls/syslink-overview) v sadě Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CLinkCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn.h

## <a name="clinkctrlclinkctrl"></a><a name="clinkctrl"></a>CLinkCtrl::CLinkCtrl

Vytvoří `CLinkCtrl` objekt.

```
CLinkCtrl();
```

## <a name="clinkctrlcreate"></a><a name="create"></a>CLinkCtrl::Vytvořit

Vytvoří ovládací prvek propojení a `CLinkCtrl` připojí jej k objektu.

```
virtual BOOL Create(
    LPCTSTR lpszLinkMarkup,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);

virtual BOOL Create(DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*lpszLinkMarkup*<br/>
Ukazatel na řetězec s nulovým ukončením, který obsahuje označený text, který se má zobrazit. Další informace naleznete v části "Označení a přístup k propojení" v tématu [Přehled ovládacích prvků SysLink](/windows/win32/Controls/syslink-overview).

*dwStyl*<br/>
Určuje styl ovládacího prvku propojení. Použijte libovolnou kombinaci stylů ovládacích prvků. Další informace naleznete `Windows SDK` v [tématu Běžné styly ovládacích prvků](/windows/win32/Controls/common-control-styles) v tématu.

*Rect*<br/>
Určuje velikost a umístění ovládacího prvku propojení. Může to být buď [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt nebo [RECT](/windows/win32/api/windef/ns-windef-rect) struktury.

*pParentWnd*<br/>
Určuje nadřazené okno ovládacího prvku propojení. Nesmí být null.

*Nid*<br/>
Určuje ID ovládacího prvku propojení.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byla inicializace úspěšná; jinak FALSE.

### <a name="remarks"></a>Poznámky

Objekt vytvoříte ve `CLinkCtrl` dvou krocích. Nejprve zavolejte konstruktoru `Create`a potom volání , který vytvoří `CLinkCtrl` ovládací prvek propojení a připojí jej k objektu. Chcete-li s ovládacím prvkem používat rozšířené styly oken, zavolejte místo něj `Create` [CLinkCtrl::CreateEx.](#createex)

Druhá forma `Create` metody je zastaralá. Použijte první formulář, který určuje parametr *lpszLinkMarkup.*

### <a name="example"></a>Příklad

Následující příklad kódu definuje dvě proměnné `m_Link1` `m_Link2`s názvem a , které se používají pro přístup ke dvěma ovládacím prvkům propojení.

[!code-cpp[NVC_MFC_CLinkCtrl_s1#2](../../mfc/reference/codesnippet/cpp/clinkctrl-class_1.h)]

### <a name="example"></a>Příklad

Následující příklad kódu vytvoří jeden ovládací prvek propojení na základě umístění jiného ovládacího prvku propojení. Zavaděč prostředků vytvoří první ovládací prvek propojení při spuštění aplikace. Když aplikace zadá Metodu OnInitDialog, vytvoříte druhý ovládací prvek propojení vzhledem k pozici prvního prvku propojení. Potom změníte velikost druhého ovládacího prvku propojení tak, aby odpovídal textu, který se zobrazí.

[!code-cpp[NVC_MFC_CLinkCtrl_s1#1](../../mfc/reference/codesnippet/cpp/clinkctrl-class_2.cpp)]

## <a name="clinkctrlcreateex"></a><a name="createex"></a>CLinkCtrl::CreateEx

Vytvoří ovládací prvek propojení s rozšířenými `CLinkCtrl` styly a připojí ho k objektu.

```
virtual BOOL CreateEx(
    LPCTSTR lpszLinkMarkup,
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);

virtual BOOL CreateEx(DWORD  dwExStyle,
    DWORD  dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT  nID);
```

### <a name="parameters"></a>Parametry

*lpszLinkMarkup*<br/>
Ukazatel na řetězec s nulovým ukončením, který obsahuje označený text, který se má zobrazit. Další informace naleznete v části "Označení a přístup k propojení" v tématu [Přehled ovládacích prvků SysLink](/windows/win32/Controls/syslink-overview).

*dwExStyl*<br/>
Určuje rozšířený styl ovládacího prvku propojení. Seznam rozšířených stylů systému Windows naleznete v parametru *dwExStyle* pro [createwindowex](/windows/win32/api/winuser/nf-winuser-createwindowexw) v sadě Windows SDK.

*dwStyl*<br/>
Určuje styl ovládacího prvku propojení. Použijte libovolnou kombinaci stylů ovládacích prvků. Další informace naleznete v [tématu Common Control Styles](/windows/win32/Controls/common-control-styles) in the Windows SDK.

*Rect*<br/>
Určuje velikost a umístění ovládacího prvku propojení. Může to být buď [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt nebo [RECT](/windows/win32/api/windef/ns-windef-rect) struktury.

*pParentWnd*<br/>
Určuje nadřazené okno ovládacího prvku propojení. Nesmí být null.

*Nid*<br/>
Určuje ID ovládacího prvku propojení.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byla inicializace úspěšná; jinak FALSE.

### <a name="remarks"></a>Poznámky

Místo `CreateEx` funkce [Vytvořit](#create) použijte rozšířené konstanty stylu systému Windows.

Druhá forma `CreateEx` metody je zastaralá. Použijte první formulář, který určuje parametr *lpszLinkMarkup.*

## <a name="clinkctrlgetidealheight"></a><a name="getidealheight"></a>CLinkCtrl::GetIdealHeight

Načte ideální výšku ovládacího prvku propojení.

```
int GetIdealHeight() const;
```

### <a name="return-value"></a>Návratová hodnota

Ideální výška ovládacího prvku v pixelech.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/lm-getidealheight)Win32 LM_GETIDEALHEIGHT , jak je popsáno v sadě Windows SDK.

## <a name="clinkctrlgetidealsize"></a><a name="getidealsize"></a>CLinkCtrl::GetIdealSize

Vypočítá upřednostňovanou výšku textu propojení pro aktuální ovládací prvek propojení v závislosti na zadané šířce propojení.

```
int GetIdealSize(
    int cxMaxWidth,
    SIZE* pSize) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*cxMaxWidth*|[v] Maximální šířka odkazu v pixelech.|
|[out] \* *pVelikost*|Ukazatel na strukturu [velikosti](/windows/win32/api/windef/ns-windef-size) systému Windows. Když tato metoda *cy* vrátí, cy `SIZE` člen struktury obsahuje ideální výšku textu propojení pro šířku textu propojení, která je určena *cxMaxWidth*. Člen *cx* struktury obsahuje šířku textu odkazu, která je skutečně potřebná.|

### <a name="return-value"></a>Návratová hodnota

Upřednostňovaná výška textu odkazu v obrazových bodech. Vrácená hodnota je stejná jako *cy* hodnota cy `SIZE` člen struktury.

### <a name="remarks"></a>Poznámky

Příklad metody naleznete `GetIdealSize` v příkladu [cLinkCtrl::Create](#create).

Tato metoda odešle [zprávu LM_GETIDEALSIZE,](/windows/win32/Controls/lm-getidealsize) která je popsána v sadě Windows SDK.

## <a name="clinkctrlgetitem"></a><a name="getitem"></a>CLinkCtrl::GetItem

Načte stavy a atributy položky ovládacího prvku propojení.

```
BOOL GetItem(PLITEM pItem) const;
```

### <a name="parameters"></a>Parametry

*pPoložka*<br/>
Ukazatel na strukturu [LITEM](/windows/win32/api/commctrl/ns-commctrl-litem) pro příjem informací o položce.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [LM_GETITEM](/windows/win32/Controls/lm-getitem)zprávy Win32 , jak je popsáno v sadě Windows SDK.

## <a name="clinkctrlgetitemid"></a><a name="getitemid"></a>clinkctrl::GetItemID

Načte ID položky ovládacího prvku propojení.

```
BOOL GetItemID(
    int iLink,
    CString& strID) const;

BOOL GetItemID(
    int iLink,
    LPWSTR szID,
    UINT cchID) const;
```

### <a name="parameters"></a>Parametry

*Ilink*<br/>
Index položky ovládacího prvku propojení.

*strID*<br/>
[CStringT](../../atl-mfc-shared/reference/cstringt-class.md) objekt obsahující ID zadané položky.

*szID*<br/>
Řetězec s ukončeným hodnotou null obsahující ID zadané položky.

*cchID*<br/>
Velikost ve znacích vyrovnávací paměti *szID.*

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

> [!NOTE]
> Tato funkce také vrátí hodnotu NEPRAVDA, pokud je vyrovnávací paměť *szID nebo strID* menší než MAX_LINKID_TEXT.

### <a name="remarks"></a>Poznámky

Načte ID určité položky ovládacího prvku propojení. Další informace naleznete ve zprávě Win32 [LM_GETITEM](/windows/win32/Controls/lm-getitem) v sadě Windows SDK.

## <a name="clinkctrlgetitemstate"></a><a name="getitemstate"></a>CLinkCtrl::GetItemState

Načte stav položky ovládacího prvku propojení.

```
BOOL GetItemState(
    int iLink,
    UINT* pnState,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED) const;
```

### <a name="parameters"></a>Parametry

*Ilink*<br/>
Index položky ovládacího prvku propojení.

*pnState*<br/>
Hodnota zadané položky stavu.

*maska stavu*<br/>
Kombinace příznaků popisujících položku stavu, kterou chcete získat. Seznam hodnot naleznete v popisu `state` člena ve struktuře [LITEM.](/windows/win32/api/commctrl/ns-commctrl-litem) Povolené položky jsou shodné `state`s položkami povolenými v .

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Načte hodnotu zadané položky stavu určité položky ovládacího prvku propojení. Další informace naleznete ve zprávě Win32 [LM_GETITEM](/windows/win32/Controls/lm-getitem) v sadě Windows SDK.

## <a name="clinkctrlgetitemurl"></a><a name="getitemurl"></a>CLinkCtrl::GetItemUrl

Načte adresu URL reprezentovanou položkou ovládacího prvku odkazu.

```
BOOL GetItemUrl(
    int iLink,
    CString& strUrl) const;

BOOL GetItemUrl(
    int iLink,
    LPWSTR szUrl,
    UINT cchUrl) const;
```

### <a name="parameters"></a>Parametry

*Ilink*<br/>
Index položky ovládacího prvku propojení.

*strUrl*<br/>
Objekt [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) obsahující adresu URL reprezentovanou zadanou položkou

*szUrl*<br/>
Řetězec s neplatným ukončováním obsahující adresu URL reprezentovanou zadanou položkou

*cchUrl*<br/>
Velikost ve znacích vyrovnávací paměti *szURL.*

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

> [!NOTE]
> Tato funkce také vrátí hodnotu NEPRAVDA, pokud je vyrovnávací paměť *szUrl nebo strUrl* menší než MAX_LINKID_TEXT.

### <a name="remarks"></a>Poznámky

Načte adresu URL reprezentovanou zadanou položkou ovládacího prvku propojení. Další informace naleznete ve zprávě Win32 [LM_GETITEM](/windows/win32/Controls/lm-getitem) v sadě Windows SDK.

## <a name="clinkctrlhittest"></a><a name="hittest"></a>CLinkCtrl::HitTest

Určuje, zda uživatel klepnul na zadaný odkaz.

```
BOOL HitTest(PLHITTESTINFO phti) const;
```

### <a name="parameters"></a>Parametry

*phti*<br/>
Ukazatel na `LHITTESTINFO` strukturu obsahující všechny informace o odkazu, na který uživatel klepnul.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [LM_HITTEST](/windows/win32/Controls/lm-hittest)zprávy Win32 , jak je popsáno v sadě Windows SDK.

## <a name="clinkctrlsetitem"></a><a name="setitem"></a>CLinkCtrl::SetItem

Nastaví stavy a atributy položky ovládacího prvku propojení.

```
BOOL SetItem(PLITEM pItem);
```

### <a name="parameters"></a>Parametry

*pPoložka*<br/>
Ukazatel na strukturu [LITEM](/windows/win32/api/commctrl/ns-commctrl-litem) obsahující informace, které mají být nastaveny.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [LM_SETITEM](/windows/win32/Controls/lm-setitem)zprávy Win32 , jak je popsáno v sadě Windows SDK.

## <a name="clinkctrlsetitemid"></a><a name="setitemid"></a>clinkctrl::SetItemID

Načte ID položky ovládacího prvku propojení.

```
BOOL SetItemID(
    int iLink,
    LPCWSTR szID);
```

### <a name="parameters"></a>Parametry

*Ilink*<br/>
Index položky ovládacího prvku propojení.

*szID*<br/>
Řetězec s ukončeným hodnotou null obsahující ID zadané položky.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Nastaví ID určité položky ovládacího prvku propojení. Další informace naleznete ve zprávě Win32 [LM_SETITEM](/windows/win32/Controls/lm-setitem) v sadě Windows SDK.

## <a name="clinkctrlsetitemstate"></a><a name="setitemstate"></a>CLinkCtrl::SetItemState

Načte stav položky ovládacího prvku propojení.

```
BOOL SetItemState(
    int iLink,
    UINT state,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED);
```

### <a name="parameters"></a>Parametry

*Ilink*<br/>
Index položky ovládacího prvku propojení.

*pnState*<br/>
Hodnota nastavené položky stavu zadaného stavu.

*maska stavu*<br/>
Kombinace příznaků popisujících nastavenou položku stavu. Seznam hodnot naleznete v popisu `state` člena ve struktuře [LITEM.](/windows/win32/api/commctrl/ns-commctrl-litem) Povolené položky jsou shodné `state`s položkami povolenými v .

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Nastaví hodnotu zadané položky stavu určité položky ovládacího prvku propojení. Další informace naleznete ve zprávě Win32 [LM_SETITEM](/windows/win32/Controls/lm-setitem) v sadě Windows SDK.

## <a name="clinkctrlsetitemurl"></a><a name="setitemurl"></a>CLinkCtrl::SetItemUrl

Nastaví adresu URL reprezentovanou položkou ovládacího prvku odkazu.

```
BOOL SetItemUrl(
    int iLink,
    LPCWSTR szUrl);
```

### <a name="parameters"></a>Parametry

*Ilink*<br/>
Index položky ovládacího prvku propojení.

*szUrl*<br/>
Řetězec s neplatným ukončováním obsahující adresu URL reprezentovanou zadanou položkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Nastaví adresu URL reprezentovanou zadanou položkou ovládacího prvku propojení. Další informace naleznete ve zprávě Win32 [LM_SETITEM](/windows/win32/Controls/lm-setitem) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)
