---
title: CMFCLinkCtrl Class
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
ms.openlocfilehash: 839448694cee17f5bc1a1e47f7c113026a1a4006
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "58776424"
---
# <a name="cmfclinkctrl-class"></a>CMFCLinkCtrl Class

`CMFCLinkCtrl` Třídy zobrazí tlačítko jako hypertextový odkaz a po kliknutí na tlačítko vyvolá cíl odkazu.

## <a name="syntax"></a>Syntaxe

```
class CMFCLinkCtrl : public CMFCButton
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CMFCLinkCtrl::SetURL](#seturl)|Zadaná adresa URL se zobrazí jako text tlačítka.|
|[CMFCLinkCtrl::SetURLPrefix](#seturlprefix)|Nastaví implicitní protokol (například "http:") adresy URL.|
|[CMFCLinkCtrl::SizeToContent](#sizetocontent)|Změní velikost tlačítka tak, aby obsahovala text tlačítka nebo rastrový obrázek.|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[CMFCLinkCtrl::OnDrawFocusRect](#ondrawfocusrect)|Volá se rozhraním před vykreslením obdélník tlačítka.|

## <a name="remarks"></a>Poznámky

Po kliknutí na tlačítko, který je odvozen z `CMFCLinkCtrl` třídy, rozhraní předá adresu URL na tlačítko jako parametr, který se `ShellExecute` metody. Pak bude `ShellExecute` metoda otevře cílové adresy URL.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak nastavit velikost `CMFCLinkCtrl` objekt a jak nastavit adresu url a popis ve `CMFCLinkCtrl` objektu. V tomto příkladu je součástí [nové ovládací prvky ukázka](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#9](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#10](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget –](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFCLinkCtrl](../../mfc/reference/cmfclinkctrl-class.md)

## <a name="requirements"></a>Požadavky

**Header:** afxlinkctrl.h

##  <a name="ondrawfocusrect"></a>  CMFCLinkCtrl::OnDrawFocusRect

Volá se rozhraním před vykreslením obdélník tlačítka.

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Ukazatel na kontext zařízení.

*rectClient*<br/>
[in] Obdélník, který odkaz ovládacího prvku za rozsahem.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu, pokud chcete použít vlastní kód chcete-li nakreslit obdélník na tlačítko.

##  <a name="seturl"></a>  CMFCLinkCtrl::SetURL

Zadaná adresa URL se zobrazí jako text tlačítka.

```
void SetURL(LPCTSTR lpszURL);
```

### <a name="parameters"></a>Parametry

*lpszURL*<br/>
[in] Text tlačítka pro zobrazení.

### <a name="remarks"></a>Poznámky

##  <a name="seturlprefix"></a>  CMFCLinkCtrl::SetURLPrefix

Nastaví implicitní protokol (například "http:") adresy URL.

```
void SetURLPrefix(LPCTSTR lpszPrefix);
```

### <a name="parameters"></a>Parametry

*lpszPrefix*<br/>
[in] Předpona protokolu URL.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte k nastavení předponu adresy URL. Předpona není zobrazena na tlačítka pro rozpoznávání tváře, ale slouží ke, přejděte na adresu URL cílové.

##  <a name="sizetocontent"></a>  CMFCLinkCtrl::SizeToContent

Změní velikost tlačítka tak, aby obsahovala text tlačítka nebo rastrový obrázek.

```
virtual CSize SizeToContent(
    BOOL bVCenter=FALSE,
    BOOL bHCenter=FALSE);
```

### <a name="parameters"></a>Parametry

*bVCenter*<br/>
[in] TRUE, pokud chcete text tlačítka a rastrový obrázek svisle mezi horní a dolní ovládací prvek odkazu; center v opačném případě hodnota FALSE. Výchozí hodnota je FALSE.

*bHCenter*<br/>
[in] TRUE, pokud chcete text tlačítka a rastrový obrázek vodorovně mezi levé a pravé straně ovládacího prvku odkazu; center v opačném případě hodnota FALSE. Výchozí hodnota je FALSE.

### <a name="return-value"></a>Návratová hodnota

A [CSize](../../atl-mfc-shared/reference/csize-class.md) objekt, který obsahuje novou velikost ovládacího prvku odkaz.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Clinkctrl – třída](../../mfc/reference/clinkctrl-class.md)<br/>
[Cmfcbutton – třída](../../mfc/reference/cmfcbutton-class.md)
