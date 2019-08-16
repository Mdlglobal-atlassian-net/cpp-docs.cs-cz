---
title: CLinkCtrl – třída
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
ms.openlocfilehash: 37d9e624c40f0d6aa7f3d3fa1ed3d97ffa478ee7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505706"
---
# <a name="clinkctrl-class"></a>CLinkCtrl – třída

Poskytuje funkce pro běžný ovládací prvek Windows SysLink.

## <a name="syntax"></a>Syntaxe

```
class CLinkCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CLinkCtrl::CLinkCtrl](#clinkctrl)|`CLinkCtrl` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CLinkCtrl::Create](#create)|Vytvoří ovládací prvek propojení a připojí ho k `CLinkCtrl` objektu.|
|[CLinkCtrl::CreateEx](#createex)|Vytvoří ovládací prvek propojení se rozšířenými styly a připojí ho k `CLinkCtrl` objektu.|
|[CLinkCtrl::GetIdealHeight](#getidealheight)|Načte ideální výšku ovládacího prvku propojení.|
|[CLinkCtrl::GetIdealSize](#getidealsize)|Vypočítá upřednostňovanou výšku textu odkazu pro aktuální ovládací prvek propojení v závislosti na zadané šířce propojení.|
|[CLinkCtrl::GetItem](#getitem)|Načte stavy a atributy položky ovládacího prvku odkaz.|
|[CLinkCtrl::GetItemID](#getitemid)|Načte ID položky ovládacího prvku odkaz.|
|[CLinkCtrl::GetItemState](#getitemstate)|Načte stav položky ovládacího prvku odkaz.|
|[CLinkCtrl::GetItemUrl](#getitemurl)|Načte adresu URL reprezentovanou položkou ovládacího prvku odkaz.|
|[CLinkCtrl::HitTest](#hittest)|Určuje, zda uživatel klikl na zadaný odkaz.|
|[CLinkCtrl::SetItem](#setitem)|Nastaví stavy a atributy položky ovládacího prvku odkaz.|
|[CLinkCtrl::SetItemID](#setitemid)|Nastaví ID položky ovládacího prvku odkaz.|
|[CLinkCtrl::SetItemState](#setitemstate)|Nastaví stav položky ovládacího prvku odkaz.|
|[CLinkCtrl::SetItemUrl](#setitemurl)|Nastaví adresu URL reprezentovanou položkou ovládacího prvku odkaz.|

## <a name="remarks"></a>Poznámky

"Ovládací prvek propojení" poskytuje pohodlný způsob, jak vkládat hypertextové odkazy do okna. Skutečný ovládací prvek je okno, které vykresluje označený text a spustí příslušné aplikace, když uživatel klikne na vložený odkaz. V rámci jednoho ovládacího prvku je podporováno více odkazů a lze k němu přistupovat pomocí indexu založeného na nule.

Tento ovládací prvek (a `CLinkCtrl` třída) je k dispozici pouze pro programy, které jsou spuštěny v systému Windows XP nebo novějším.

Další informace naleznete v tématu [ovládací prvek Syslink](/windows/win32/Controls/syslink-overview) v Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CLinkCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn. h

##  <a name="clinkctrl"></a>  CLinkCtrl::CLinkCtrl

`CLinkCtrl` Vytvoří objekt.

```
CLinkCtrl();
```

##  <a name="create"></a>CLinkCtrl:: Create

Vytvoří ovládací prvek propojení a připojí ho k `CLinkCtrl` objektu.

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
Ukazatel na řetězec zakončený nulou, který obsahuje označený text, který se má zobrazit. Další informace naleznete v části "označení a přístup k odkazům" v tématu [Přehled ovládacích prvků Syslink](/windows/win32/Controls/syslink-overview).

*dwStyle*<br/>
Určuje styl ovládacího prvku odkaz. Použití libovolné kombinace stylů ovládacích prvků. Další informace najdete v `Windows SDK` tématu [Běžné styly ovládacích prvků](/windows/win32/Controls/common-control-styles) .

*OBD*<br/>
Určuje velikost a polohu ovládacího prvku propojení. Může to být buď objekt [CRect](../../atl-mfc-shared/reference/crect-class.md) , nebo struktura [Rect](/windows/win32/api/windef/ns-windef-rect) .

*pParentWnd*<br/>
Určuje nadřazené okno ovládacího prvku odkaz. Nesmí mít hodnotu NULL.

*nID*<br/>
Určuje ID ovládacího prvku odkazu.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud byla inicializace úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

`CLinkCtrl` Vytvoříte objekt ve dvou krocích. Nejprve volejte konstruktor a potom zavolejte `Create`, čímž se vytvoří ovládací prvek propojení a připojí se `CLinkCtrl` k objektu. Chcete-li použít rozšířené styly systému Windows s ovládacím prvkem, zavolejte [CLinkCtrl:: CreateEx](#createex) namísto `Create`.

Druhá forma `Create` metody je zastaralá. Použijte první formulář, který určuje parametr *lpszLinkMarkup* .

### <a name="example"></a>Příklad

Následující příklad kódu definuje dvě proměnné s názvem `m_Link1` a `m_Link2`, které se používají pro přístup k dvěma ovládacím prvkům odkazů.

[!code-cpp[NVC_MFC_CLinkCtrl_s1#2](../../mfc/reference/codesnippet/cpp/clinkctrl-class_1.h)]

### <a name="example"></a>Příklad

Následující příklad kódu vytvoří jeden ovládací prvek propojení na základě umístění jiného ovládacího prvku propojení. Zavaděč prostředků vytvoří první ovládací prvek propojení při spuštění aplikace. Když aplikace vstoupí do metody OnInitDialog, vytvoříte druhý ovládací prvek propojení relativně k pozici prvního ovládacího prvku propojení. Pak změníte velikost druhého ovládacího prvku propojení tak, aby odpovídal textu, který se zobrazí.

[!code-cpp[NVC_MFC_CLinkCtrl_s1#1](../../mfc/reference/codesnippet/cpp/clinkctrl-class_2.cpp)]

##  <a name="createex"></a>CLinkCtrl::CreateEx

Vytvoří ovládací prvek propojení se rozšířenými styly a připojí ho k `CLinkCtrl` objektu.

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
Ukazatel na řetězec zakončený nulou, který obsahuje označený text, který se má zobrazit. Další informace naleznete v části "označení a přístup k odkazům" v tématu [Přehled ovládacích prvků Syslink](/windows/win32/Controls/syslink-overview).

*dwExStyle*<br/>
Určuje rozšířený styl ovládacího prvku odkaz. Seznam rozšířených stylů Windows naleznete v parametru *dwExStyle* pro [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) v Windows SDK.

*dwStyle*<br/>
Určuje styl ovládacího prvku odkaz. Použití libovolné kombinace stylů ovládacích prvků. Další informace najdete v tématu [Běžné styly ovládacích prvků](/windows/win32/Controls/common-control-styles) v Windows SDK.

*OBD*<br/>
Určuje velikost a polohu ovládacího prvku propojení. Může to být buď objekt [CRect](../../atl-mfc-shared/reference/crect-class.md) , nebo struktura [Rect](/windows/win32/api/windef/ns-windef-rect) .

*pParentWnd*<br/>
Určuje nadřazené okno ovládacího prvku odkaz. Nesmí mít hodnotu NULL.

*nID*<br/>
Určuje ID ovládacího prvku odkazu.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud byla inicializace úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Použijte `CreateEx` místo [vytvořit](#create) , pokud chcete použít rozšířené konstanty stylu Windows.

Druhá forma `CreateEx` metody je zastaralá. Použijte první formulář, který určuje parametr *lpszLinkMarkup* .

##  <a name="getidealheight"></a>  CLinkCtrl::GetIdealHeight

Načte ideální výšku ovládacího prvku propojení.

```
int GetIdealHeight() const;
```

### <a name="return-value"></a>Návratová hodnota

Ideální výška ovládacího prvku v pixelech

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [LM_GETIDEALHEIGHT](/windows/win32/Controls/lm-getidealheight), jak je popsáno v Windows SDK.

##  <a name="getidealsize"></a>CLinkCtrl::GetIdealSize

Vypočítá upřednostňovanou výšku textu odkazu pro aktuální ovládací prvek propojení v závislosti na zadané šířce propojení.

```
int GetIdealSize(
    int cxMaxWidth,
    SIZE* pSize) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*cxMaxWidth*|pro Maximální šířka propojení v pixelech|
|mimo \* *psize*|Ukazatel na strukturu [velikosti](/windows/win32/api/windef/ns-windef-size) Windows. Když tato metoda vrátí hodnotu, člen `SIZE` CY struktury obsahuje ideální výšku textu odkazu pro šířku textu propojení určenou parametrem *cxMaxWidth*. Člen *CX* struktury obsahuje skutečně potřebnou šířku textu odkazu.|

### <a name="return-value"></a>Návratová hodnota

Upřednostňovaná výška textu odkazu (v pixelech) Vrácená hodnota je stejná jako hodnota člena `SIZE` *CY* struktury.

### <a name="remarks"></a>Poznámky

Příklad `GetIdealSize` metody naleznete v příkladu v [CLinkCtrl:: Create](#create).

Tato metoda pošle zprávu [LM_GETIDEALSIZE](/windows/win32/Controls/lm-getidealsize) , která je popsána v Windows SDK.

##  <a name="getitem"></a>CLinkCtrl:: GetItem

Načte stavy a atributy položky ovládacího prvku odkaz.

```
BOOL GetItem(PLITEM pItem) const;
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Ukazatel na strukturu [litem](/windows/win32/api/commctrl/ns-commctrl-litem) pro příjem informací o položce.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [LM_GETITEM](/windows/win32/Controls/lm-getitem), jak je popsáno v Windows SDK.

##  <a name="getitemid"></a>  CLinkCtrl::GetItemID

Načte ID položky ovládacího prvku odkaz.

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

*iLink*<br/>
Index položky ovládacího prvku propojení

*strID*<br/>
Objekt [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) obsahující ID zadané položky.

*szID*<br/>
Řetězec zakončený hodnotou null obsahující ID zadané položky.

*cchID*<br/>
Velikost ve znacích *szID* vyrovnávací paměti.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

> [!NOTE]
>  Tato funkce také vrátí hodnotu FALSE, pokud je vyrovnávací paměť *szID nebo strID* menší než MAX_LINKID_TEXT.

### <a name="remarks"></a>Poznámky

Načte ID konkrétní položky ovládacího prvku propojení. Další informace najdete v tématu [LM_GETITEM](/windows/win32/Controls/lm-getitem) zprávy Win32 v Windows SDK.

##  <a name="getitemstate"></a>CLinkCtrl::GetItemState

Načte stav položky ovládacího prvku odkaz.

```
BOOL GetItemState(
    int iLink,
    UINT* pnState,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED) const;
```

### <a name="parameters"></a>Parametry

*iLink*<br/>
Index položky ovládacího prvku propojení

*pnState*<br/>
Hodnota zadané položky stavu.

*stateMask*<br/>
Kombinace příznaků popisujících, které položky stavu se mají získat. Seznam hodnot naleznete v popisu `state` člena ve struktuře [litem](/windows/win32/api/commctrl/ns-commctrl-litem) . Povolené položky jsou stejné jako ty, které jsou `state`povolené v.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Načte hodnotu zadané stavové položky konkrétní položky ovládacího prvku propojení. Další informace najdete v tématu [LM_GETITEM](/windows/win32/Controls/lm-getitem) zprávy Win32 v Windows SDK.

##  <a name="getitemurl"></a>  CLinkCtrl::GetItemUrl

Načte adresu URL reprezentovanou položkou ovládacího prvku odkaz.

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

*iLink*<br/>
Index položky ovládacího prvku propojení

*strUrl*<br/>
Objekt [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) obsahující adresu URL reprezentovanou zadanou položkou

*szUrl*<br/>
Řetězec zakončený hodnotou null obsahující adresu URL reprezentovanou zadanou položkou

*cchUrl*<br/>
Velikost ve znacích *szURL* vyrovnávací paměti.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

> [!NOTE]
>  Tato funkce také vrátí hodnotu FALSE, pokud je vyrovnávací paměť *szUrl nebo strURL* menší než MAX_LINKID_TEXT.

### <a name="remarks"></a>Poznámky

Načte adresu URL reprezentovanou zadanou položkou ovládacího prvku odkaz. Další informace najdete v tématu [LM_GETITEM](/windows/win32/Controls/lm-getitem) zprávy Win32 v Windows SDK.

##  <a name="hittest"></a>CLinkCtrl::HitTest

Určuje, zda uživatel klikl na zadaný odkaz.

```
BOOL HitTest(PLHITTESTINFO phti) const;
```

### <a name="parameters"></a>Parametry

*phti*<br/>
Ukazatel na `LHITTESTINFO` strukturu obsahující informace o propojení, na které uživatel kliknul.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [LM_HITTEST](/windows/win32/Controls/lm-hittest), jak je popsáno v Windows SDK.

##  <a name="setitem"></a>CLinkCtrl::SetItem

Nastaví stavy a atributy položky ovládacího prvku odkaz.

```
BOOL SetItem(PLITEM pItem);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Ukazatel na strukturu [litem](/windows/win32/api/commctrl/ns-commctrl-litem) obsahující informace, které mají být nastaveny.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [LM_SETITEM](/windows/win32/Controls/lm-setitem), jak je popsáno v Windows SDK.

##  <a name="setitemid"></a>CLinkCtrl::SetItemID

Načte ID položky ovládacího prvku odkaz.

```
BOOL SetItemID(
    int iLink,
    LPCWSTR szID);
```

### <a name="parameters"></a>Parametry

*iLink*<br/>
Index položky ovládacího prvku propojení

*szID*<br/>
Řetězec zakončený hodnotou null obsahující ID zadané položky.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Nastaví ID konkrétní položky ovládacího prvku propojení. Další informace najdete v tématu [LM_SETITEM](/windows/win32/Controls/lm-setitem) zprávy Win32 v Windows SDK.

##  <a name="setitemstate"></a>CLinkCtrl::SetItemState

Načte stav položky ovládacího prvku odkaz.

```
BOOL SetItemState(
    int iLink,
    UINT state,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED);
```

### <a name="parameters"></a>Parametry

*iLink*<br/>
Index položky ovládacího prvku propojení

*pnState*<br/>
Hodnota zadané položky stavu, která je nastavena.

*stateMask*<br/>
Kombinace příznaků, které popisují stavovou položku. Seznam hodnot naleznete v popisu `state` člena ve struktuře [litem](/windows/win32/api/commctrl/ns-commctrl-litem) . Povolené položky jsou stejné jako ty, které jsou `state`povolené v.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Nastaví hodnotu zadané stavové položky konkrétní položky ovládacího prvku propojení. Další informace najdete v tématu [LM_SETITEM](/windows/win32/Controls/lm-setitem) zprávy Win32 v Windows SDK.

##  <a name="setitemurl"></a>  CLinkCtrl::SetItemUrl

Nastaví adresu URL reprezentovanou položkou ovládacího prvku odkaz.

```
BOOL SetItemUrl(
    int iLink,
    LPCWSTR szUrl);
```

### <a name="parameters"></a>Parametry

*iLink*<br/>
Index položky ovládacího prvku propojení

*szUrl*<br/>
Řetězec zakončený hodnotou null obsahující adresu URL reprezentovanou zadanou položkou

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Nastaví adresu URL reprezentovanou zadanou položkou ovládacího prvku odkaz. Další informace najdete v tématu [LM_SETITEM](/windows/win32/Controls/lm-setitem) zprávy Win32 v Windows SDK.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)
