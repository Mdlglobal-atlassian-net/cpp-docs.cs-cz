---
title: CReBar – – třída
ms.date: 11/19/2018
f1_keywords:
- CReBar
- AFXEXT/CReBar
- AFXEXT/CReBar::AddBar
- AFXEXT/CReBar::Create
- AFXEXT/CReBar::GetReBarCtrl
helpviewer_keywords:
- CReBar [MFC], AddBar
- CReBar [MFC], Create
- CReBar [MFC], GetReBarCtrl
ms.assetid: c1ad2720-1d33-4106-8e4e-80aa84f93559
ms.openlocfilehash: 434232e8f99bf914b00379db53d4b4a37d24fe36
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502784"
---
# <a name="crebar-class"></a>CReBar – – třída

Ovládací panel, který poskytuje informace o rozložení, persistenci a stavu pro ovládací prvky matrice.

## <a name="syntax"></a>Syntaxe

```
class CReBar : public CControlBar
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CReBar –:: AddBar](#addbar)|Přidá do matrice pásmo.|
|[CReBar –:: Create](#create)|Vytvoří ovládací prvek matrice a připojí ho k `CReBar` objektu.|
|[CReBar::GetReBarCtrl](#getrebarctrl)|Umožňuje přímý přístup k základnímu běžnému ovládacímu prvku.|

## <a name="remarks"></a>Poznámky

Objekt matrice může obsahovat různé podřízené systémy Windows, obvykle jiné ovládací prvky, včetně textových polí, panelů nástrojů a seznamů. Objekt matrice může zobrazit jeho podřízená okna přes určenou rastrový obrázek. Vaše aplikace může automaticky měnit velikost matrice nebo uživatel může ručně změnit velikost matrice kliknutím nebo přetažením jeho panelu.

![Příklad RebarMenu](../../mfc/reference/media/vc4sc61.gif "Příklad RebarMenu")

## <a name="rebar-control"></a>Ovládací prvek matrice

Objekt matrice se chová podobně jako objekt Toolbar. Matrice používá k změně velikosti pásma mechanismus kliknutí a přetažením. Ovládací prvek matrice může obsahovat jeden nebo více pásem, přičemž každý z nich má libovolnou kombinaci panelu úchytů, rastrového obrázku, textového popisku a podřízeného okna. Pásma ale nemůžou obsahovat více než jedno podřízené okno.

`CReBar`k poskytnutí své implementace používá třídu [atributu CReBarCtrl](../../mfc/reference/crebarctrl-class.md) . Přístup k ovládacímu prvku matrice prostřednictvím [GetReBarCtrl](#getrebarctrl) můžete využít k využití možností přizpůsobení ovládacího prvku. Další informace o ovládacích prvcích matrice naleznete v `CReBarCtrl`tématu. Další informace o použití ovládacích prvků matrice naleznete v tématu [using atributu CReBarCtrl](../../mfc/using-crebarctrl.md).

> [!CAUTION]
>  Objekty ovládacích prvků matrice a matrice nepodporují ukotvení ovládacích panelů MFC. Pokud `CRebar::EnableDocking` je volána, vaše aplikace bude vyhodnotit.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CReBar`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxext. h

##  <a name="addbar"></a>CReBar –:: AddBar

Zavolejte tuto členskou funkci pro přidání pásma do matrice.

```
BOOL AddBar(
    CWnd* pBar,
    LPCTSTR pszText = NULL,
    CBitmap* pbmp = NULL,
    DWORD dwStyle = RBBS_GRIPPERALWAYS | RBBS_FIXEDBMP);

BOOL AddBar(
    CWnd* pBar,
    COLORREF clrFore,
    COLORREF clrBack,
    LPCTSTR pszText = NULL,
    DWORD dwStyle = RBBS_GRIPPERALWAYS);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
Ukazatel na `CWnd` objekt, který je podřízeným oknem, který má být vložen do matrice. Odkazovaný objekt musí mít WS_CHILD.

*lpszText*<br/>
Ukazatel na řetězec obsahující text, který se má zobrazit na matrice. Ve výchozím nastavení je NULL. Text obsažený v *lpszText* není součástí podřízeného okna; je na matrice.

*pbmp*<br/>
Ukazatel na `CBitmap` objekt, který se má zobrazit na pozadí matrice. Ve výchozím nastavení je NULL.

*dwStyle*<br/>
Hodnota DWORD obsahující styl, který má být použit pro matrice. Úplný seznam stylů pásma najdete v popisu [](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) funkcevREBARBANDINFOstruktuře`fStyle` Win32.

*clrFore*<br/>
Hodnota COLORREF, která představuje barvu popředí matrice.

*clrBack*<br/>
Hodnota COLORREF, která představuje barvu pozadí matrice.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#1](../../mfc/reference/codesnippet/cpp/crebar-class_1.cpp)]

##  <a name="create"></a>CReBar –:: Create

Zavolejte tuto členskou funkci pro vytvoření matrice.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = RBS_BANDBORDERS,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,
    UINT nID = AFX_IDW_REBAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Ukazatel na `CWnd` objekt, jehož okno systému Windows je nadřazeným prvkem stavového řádku. Normálně okno rámce.

*dwCtrlStyle*<br/>
Styl ovládacího prvku matrice Ve výchozím nastavení RBS_BANDBORDERS, který zobrazuje úzké řádky pro oddělit sousední pásma v rámci ovládacího prvku matrice. Seznam stylů naleznete v tématu [styly ovládacího prvku matrice](/windows/win32/Controls/rebar-control-styles) v Windows SDK.

*dwStyle*<br/>
Styly okna matrice

*nID*<br/>
ID podřízeného okna matrice

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CReBar –:: AddBar](#addbar).

##  <a name="getrebarctrl"></a>CReBar –:: GetReBarCtrl

Tato členská funkce umožňuje přímý přístup k základnímu běžnému ovládacímu prvku.

```
CReBarCtrl& GetReBarCtrl() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt [atributu CReBarCtrl](../../mfc/reference/crebarctrl-class.md) .

### <a name="remarks"></a>Poznámky

Tuto členskou funkci volejte pro využití funkcí společného ovládacího prvku Windows matrice v části Přizpůsobení vašich matrice. Při volání `GetReBarCtrl`vrátí objekt reference `CReBarCtrl` k objektu, aby bylo možné použít kteroukoli z těchto členských funkcí.

Další informace o použití nástroje `CReBarCtrl` k přizpůsobení matrice najdete v tématu [použití atributu CReBarCtrl](../../mfc/using-crebarctrl.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#2](../../mfc/reference/codesnippet/cpp/crebar-class_2.cpp)]

## <a name="see-also"></a>Viz také:

[MFCIE Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CControlBar – třída](../../mfc/reference/ccontrolbar-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
