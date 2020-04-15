---
title: CReBar – třída
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
ms.openlocfilehash: c1379d1ef8effea0df564da1b43769bb9a11435d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363934"
---
# <a name="crebar-class"></a>CReBar – třída

Ovládací panel, který poskytuje informace o rozložení, trvalosti a stavu ovládacích prvků výztuže.

## <a name="syntax"></a>Syntaxe

```
class CReBar : public CControlBar
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[Crebar::AddBar](#addbar)|Přidá k výztuze pruh.|
|[Crebar::Vytvořit](#create)|Vytvoří ovládací prvek výztuže `CReBar` a připojí jej k objektu.|
|[Crebar::GetRebarctrl](#getrebarctrl)|Umožňuje přímý přístup k základní společný ovládací prvek.|

## <a name="remarks"></a>Poznámky

Objekt výztuže může obsahovat různé podřízené oken, obvykle další ovládací prvky, včetně editačních polí, panelů nástrojů a seznamů. Objekt výztuže může zobrazit podřízená okna přes zadanou bitmapu. Aplikace může automaticky změnit velikost výztuže nebo uživatel může ručně změnit velikost výztuže klepnutím nebo přetažením jeho úchopného zařízení.

![Příklad nabídky výsečí](../../mfc/reference/media/vc4sc61.gif "Příklad nabídky výsečí")

## <a name="rebar-control"></a>Ovládací prvek výztuže

Objekt výztuže se chová podobně jako objekt panelu nástrojů. Výztuž používá mechanismus kliknutí a přetažení ke změně velikosti pásem. Ovládací prvek výztuže může obsahovat jedno nebo více pásů, přičemž každé pásmo má libovolnou kombinaci úchytu, rastrového řádku, textového popisku a podřízeného okna. Pásma však nemůže obsahovat více než jedno podřízené okno.

`CReBar`používá [CReBarCtrl](../../mfc/reference/crebarctrl-class.md) třídy poskytnout jeho provádění. Můžete přistupovat k ovládacímu prvku výztuže prostřednictvím [GetReBarCtrl](#getrebarctrl) využít možnosti přizpůsobení ovládacího prvku. Další informace o ovládacích `CReBarCtrl`prvy naleznete v tématu . Další informace o použití ovládacích prvků výztuže naleznete [v tématu Using CReBarCtrl](../../mfc/using-crebarctrl.md).

> [!CAUTION]
> Objekty ovládacího prvku výztuže a výztuže nepodporují dokování řídicího panelu knihovny MFC. Pokud `CRebar::EnableDocking` je volána, bude aplikace uplatnit.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Ovládací panel CControl](../../mfc/reference/ccontrolbar-class.md)

`CReBar`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxext.h

## <a name="crebaraddbar"></a><a name="addbar"></a>Crebar::AddBar

Volání této členské funkce přidat pásmo výztuže.

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
Ukazatel na `CWnd` objekt, který je podřízeným oknem, které má být vloženo do výztuže. Odkazovaný objekt musí mít WS_CHILD.

*lpszText*<br/>
Ukazatel na řetězec obsahující text, který se má zobrazit na výztuze. Null ve výchozím nastavení. Text obsažený v *lpszText* není součástí podřízeného okna; je na samotné výztuze.

*pbmp*<br/>
Ukazatel na `CBitmap` objekt, který se má zobrazit na pozadí výztuže. Null ve výchozím nastavení.

*dwStyl*<br/>
DWORD obsahující styl, který se má použít na výztuhu. Úplný `fStyle` seznam stylů pásma naleznete v popisu funkce ve struktuře Win32 [REBARBANDINFO.](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow)

*clrFore*<br/>
Colorref hodnota, která představuje barvu popředí výztuže.

*zpět*<br/>
Colorref hodnota, která představuje barvu pozadí výztuže.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#1](../../mfc/reference/codesnippet/cpp/crebar-class_1.cpp)]

## <a name="crebarcreate"></a><a name="create"></a>Crebar::Vytvořit

Volání této členské funkce k vytvoření výztuže.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = RBS_BANDBORDERS,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,
    UINT nID = AFX_IDW_REBAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Ukazatel na `CWnd` objekt, jehož okno systému Windows je nadřazeným stavovým pruhem. Normálně okno rámu.

*dwCtrlStyl*<br/>
Styl ovládacího prvku výztuže. Ve výchozím nastavení RBS_BANDBORDERS, který zobrazuje úzké čáry pro oddělení sousedních pásem v ovládacím prvku výztuže. Seznam stylů naleznete v tématu [Styly ovládacích prvků](/windows/win32/Controls/rebar-control-styles) v sadě Windows SDK.

*dwStyl*<br/>
Styly oken výztuže.

*Nid*<br/>
Id podřízeného okna výztuže.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="example"></a>Příklad

  Viz příklad pro [CReBar::AddBar](#addbar).

## <a name="crebargetrebarctrl"></a><a name="getrebarctrl"></a>Crebar::GetRebarctrl

Tato členská funkce umožňuje přímý přístup k základní společný ovládací prvek.

```
CReBarCtrl& GetReBarCtrl() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt [CReBarCtrl.](../../mfc/reference/crebarctrl-class.md)

### <a name="remarks"></a>Poznámky

Volání této členské funkce využít funkce windows výztuže společného ovládacího prvku při přizpůsobování výztuže. Při volání `GetReBarCtrl`vrátí objekt odkazu na `CReBarCtrl` objekt, takže můžete použít jednu sadu členských funkcí.

Další informace o `CReBarCtrl` použití k přizpůsobení výztuže naleznete [v tématu Použití kláves CReBarCtrl](../../mfc/using-crebarctrl.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CReBarCtrl#2](../../mfc/reference/codesnippet/cpp/crebar-class_2.cpp)]

## <a name="see-also"></a>Viz také

[MFC ukázka MFCIE](../../overview/visual-cpp-samples.md)<br/>
[CControlBar – třída](../../mfc/reference/ccontrolbar-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
