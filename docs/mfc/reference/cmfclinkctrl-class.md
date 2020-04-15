---
title: CMFCLinkCtrl – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCLinkCtrl
- AFXLINKCTRL/CMFCLinkCtrl
- AFXLINKCTRL/CMFCLinkCtrl::SetURL
- AFXLINKCTRL/CMFCLinkCtrl::SetURLPrefix
- AFXLINKCTRL/CMFCLinkCtrl::SizeToContent
- AFXLINKCTRL/CMFCLinkCtrl::OnDrawFocusRect
helpviewer_keywords:
- CMFCLinkCtrl [MFC], SetURL
- CMFCLinkCtrl [MFC], SetURLPrefix
- CMFCLinkCtrl [MFC], SizeToContent
- CMFCLinkCtrl [MFC], OnDrawFocusRect
ms.assetid: 80f3874d-7cc8-410e-9ff1-62a225f5034b
ms.openlocfilehash: 1ef4e390d88f81d738d2ee18be6ba02843633011
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374393"
---
# <a name="cmfclinkctrl-class"></a>CMFCLinkCtrl – třída

Třída `CMFCLinkCtrl` zobrazí tlačítko jako hypertextový odkaz a vyvolá cíl odkazu po klepnutí na tlačítko.

## <a name="syntax"></a>Syntaxe

```
class CMFCLinkCtrl : public CMFCButton
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCLinkCtrl::SetURL](#seturl)|Zobrazí jako text tlačítka zadanou adresu URL.|
|[CMFCLinkCtrl::SetURLPrefix](#seturlprefix)|Nastaví implicitní protokol (například "http:") adresy URL.|
|[CMFCLinkctrl::SizeToContent](#sizetocontent)|Změní velikost tlačítka tak, aby obsahovalo text tlačítka nebo bitmapu.|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCLinkCtrl::OnDrawFocusRect](#ondrawfocusrect)|Volat rámci před nakreslena obdélník fokusu tlačítka.|

## <a name="remarks"></a>Poznámky

Po klepnutí na tlačítko, které `CMFCLinkCtrl` je odvozeno z třídy, rozhraní předá adresu URL tlačítka jako parametr `ShellExecute` metody. Poté `ShellExecute` metoda otevře cíl adresy URL.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak nastavit velikost `CMFCLinkCtrl` objektu a jak nastavit adresu URL `CMFCLinkCtrl` a popisek v objektu. Tento příklad je součástí [ukázky Nové ovládací prvky](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#9](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#10](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CmFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFCLinkCtrl](../../mfc/reference/cmfclinkctrl-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxlinkctrl.h

## <a name="cmfclinkctrlondrawfocusrect"></a><a name="ondrawfocusrect"></a>CMFCLinkCtrl::OnDrawFocusRect

Volat rámci před nakreslena obdélník fokusu tlačítka.

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení.

*rectClient*<br/>
[v] Obdélník, který ohraničuje ovládací prvek propojení.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu, pokud chcete použít vlastní kód k nakreslení obdélníku fokusu tlačítka.

## <a name="cmfclinkctrlseturl"></a><a name="seturl"></a>CMFCLinkCtrl::SetURL

Zobrazí jako text tlačítka zadanou adresu URL.

```
void SetURL(LPCTSTR lpszURL);
```

### <a name="parameters"></a>Parametry

*lpszURL*<br/>
[v] Text tlačítka, který se má zobrazit.

### <a name="remarks"></a>Poznámky

## <a name="cmfclinkctrlseturlprefix"></a><a name="seturlprefix"></a>CMFCLinkCtrl::SetURLPrefix

Nastaví implicitní protokol (například "http:") adresy URL.

```
void SetURLPrefix(LPCTSTR lpszPrefix);
```

### <a name="parameters"></a>Parametry

*lpszPrefix*<br/>
[v] Předpona protokolu URL.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte k nastavení předpony adresy URL. Předpona se nezobrazuje na ploše tlačítka, ale můžete ji použít k procházení cíle adresy URL.

## <a name="cmfclinkctrlsizetocontent"></a><a name="sizetocontent"></a>CMFCLinkctrl::SizeToContent

Změní velikost tlačítka tak, aby obsahovalo text tlačítka nebo bitmapu.

```
virtual CSize SizeToContent(
    BOOL bVCenter=FALSE,
    BOOL bHCenter=FALSE);
```

### <a name="parameters"></a>Parametry

*bVCenter*<br/>
[v] PRAVDA pro vystředění textu tlačítka a bitmapy svisle mezi horní a dolní částí ovládacího prvku propojení; jinak NEPRAVDA. Výchozí hodnota je FALSE.

*bHCenter*<br/>
[v] PRAVDA pro vystředění textu tlačítka a bitmapy vodorovně mezi levou a pravou stranou ovládacího prvku propojení; jinak NEPRAVDA. Výchozí hodnota je FALSE.

### <a name="return-value"></a>Návratová hodnota

[CSize](../../atl-mfc-shared/reference/csize-class.md) objekt, který obsahuje novou velikost ovládacího prvku propojení.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída CLinkCtrl](../../mfc/reference/clinkctrl-class.md)<br/>
[CMFCButton – třída](../../mfc/reference/cmfcbutton-class.md)
