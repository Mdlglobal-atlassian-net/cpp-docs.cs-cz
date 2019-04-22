---
title: Crebar – třída
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
ms.openlocfilehash: 5a87f70816e9342c7aa203a53d13699659cebb28
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58767259"
---
# <a name="crebar-class"></a>Crebar – třída

Ovládací panel, který poskytuje rozvržení, přetrvávání a informace o stavu pro prvky matrice.

## <a name="syntax"></a>Syntaxe

```
class CReBar : public CControlBar
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CReBar::AddBar](#addbar)|Přidá pásmo matrici.|
|[CReBar::Create](#create)|Vytvoří ovládací prvek matrice a připojí ho k `CReBar` objektu.|
|[CReBar::GetReBarCtrl](#getrebarctrl)|Umožňuje přímý přístup k podkladové běžný ovládací prvek.|

## <a name="remarks"></a>Poznámky

Matrice objekt může obsahovat řadu podřízených oken, obvykle další ovládací prvky, včetně textových polí, panely nástrojů a pole se seznamem. Objekt matrice můžete zobrazit jeho podřízených oken přes zadané rastrový obrázek. Vaše aplikace automaticky změnit velikost matrice nebo uživatele můžete ručně změnit velikost matrice můžete také kliknout nebo přetažením jeho úchytu panelu.

![Příklad RebarMenu](../../mfc/reference/media/vc4sc61.gif "příklad RebarMenu")

## <a name="rebar-control"></a>Matrice – ovládací prvek

Objekt matrice chová podobně jako objekt panelu nástrojů. Matrici používá kliknutím a přetažením mechanismus pro změnu velikosti jeho pruhy. Ovládacím prvkem matrice může obsahovat jeden nebo více pruhy s každou obsluhy vzdálené správy s libovolnou kombinací úchytu panelu, bitmapy, textový popisek a podřízené okno. Pruhy však nemůže obsahovat více než jeden podřízené okno.

`CReBar` používá [atributu CReBarCtrl](../../mfc/reference/crebarctrl-class.md) třídy a zadejte jeho implementaci. Přistupujete prostřednictvím ovládacího prvku rebar [getrebarctrl –](#getrebarctrl) využít možnosti vlastního nastavení ovládacího prvku. Další informace o ovládacích prvcích matrice, naleznete v tématu `CReBarCtrl`. Další informace o používání prvky matrice, naleznete v tématu [používání atributu CReBarCtrl](../../mfc/using-crebarctrl.md).

> [!CAUTION]
>  Matrice a objekty ovládacího prvku matrice nepodporují ovládací prvek MFC panelu ukotvení. Pokud `CRebar::EnableDocking` je volána, aplikace bude uplatnit.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CReBar`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxext.h

##  <a name="addbar"></a>  CReBar::AddBar

Voláním této členské funkce přidání svazku matrice.

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
Ukazatel `CWnd` objekt, který je podřízené okno, které má být vložen do matrice. Odkazovaný objekt musí mít WS_CHILD.

*lpszText*<br/>
Ukazatel na řetězec obsahující text, který se zobrazí na matrice. Ve výchozím nastavení s hodnotou NULL. Text součástí *lpszText* není součástí podřízené okno; se nachází na matrice, samotného.

*pbmp*<br/>
Ukazatel `CBitmap` objekt, který se má zobrazit na pozadí matrice. Ve výchozím nastavení s hodnotou NULL.

*dwStyle*<br/>
DWORD obsahující stylu použít matrice. Najdete v článku `fStyle` funkce Popis ve struktuře Win32 [REBARBANDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarbandinfoa) pro úplný seznam styly obsluhy vzdálené správy.

*clrFore*<br/>
COLORREF hodnotu, která představuje barvu popředí matrice.

*clrBack*<br/>
COLORREF hodnotu, která představuje barvu pozadí matrice.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#1](../../mfc/reference/codesnippet/cpp/crebar-class_1.cpp)]

##  <a name="create"></a>  CReBar::Create

Voláním této členské funkce vytvořit matrici.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = RBS_BANDBORDERS,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,
    UINT nID = AFX_IDW_REBAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Ukazatel `CWnd` objekt, jehož okno Windows je nadřazeného člena stavový řádek. Obvykle rámce okna.

*dwCtrlStyle*<br/>
Stylu ovládacího prvku rebar. Ve výchozím nastavení RBS_BANDBORDERS, která zobrazuje úzký řádky k oddělení sousední pruhy v ovládacím prvku matrice. Zobrazit [– styly ovládacího prvku Rebar](/windows/desktop/Controls/rebar-control-styles) v sadě Windows SDK pro seznam styly.

*dwStyle*<br/>
Styly oken matrice.

*nID*<br/>
ID prvku matrice podřízené okno.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CReBar::AddBar](#addbar).

##  <a name="getrebarctrl"></a>  CReBar::GetReBarCtrl

Tato členská funkce umožňuje přímý přístup k podkladové běžný ovládací prvek.

```
CReBarCtrl& GetReBarCtrl() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na [atributu CReBarCtrl](../../mfc/reference/crebarctrl-class.md) objektu.

### <a name="remarks"></a>Poznámky

Voláním této členské funkce, abyste mohli využívat funkce Windows běžné ovládacího prvku rebar. v přizpůsobení vašich matrice. Při volání `GetReBarCtrl`, vrátí objekt a odkaz `CReBarCtrl` objektu, můžete použít buď sadu členské funkce.

Další informace o používání `CReBarCtrl` přizpůsobit vaší matrice, přečtěte si článek [používání atributu CReBarCtrl](../../mfc/using-crebarctrl.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#2](../../mfc/reference/codesnippet/cpp/crebar-class_2.cpp)]

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC MFCIE](../../overview/visual-cpp-samples.md)<br/>
[CControlBar – třída](../../mfc/reference/ccontrolbar-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
