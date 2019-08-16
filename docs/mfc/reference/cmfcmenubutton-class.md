---
title: CMFCMenuButton – třída
ms.date: 07/15/2019
f1_keywords:
- CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton::CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton::PreTranslateMessage
- AFXMENUBUTTON/CMFCMenuButton::SizeToContent
- AFXMENUBUTTON/CMFCMenuButton::m_bOSMenu
- AFXMENUBUTTON/CMFCMenuButton::m_bRightArrow
- AFXMENUBUTTON/CMFCMenuButton::m_bStayPressed
- AFXMENUBUTTON/CMFCMenuButton::m_hMenu
- AFXMENUBUTTON/CMFCMenuButton::m_nMenuResult
- AFXMENUBUTTON/CMFCMenuButton::m_bDefaultClick
helpviewer_keywords:
- CMFCMenuButton [MFC], CMFCMenuButton
- CMFCMenuButton [MFC], PreTranslateMessage
- CMFCMenuButton [MFC], SizeToContent
- CMFCMenuButton [MFC], m_bOSMenu
- CMFCMenuButton [MFC], m_bRightArrow
- CMFCMenuButton [MFC], m_bStayPressed
- CMFCMenuButton [MFC], m_hMenu
- CMFCMenuButton [MFC], m_nMenuResult
- CMFCMenuButton [MFC], m_bDefaultClick
ms.assetid: 53d3d459-1e5a-47c5-8b7f-2e61f6af5187
ms.openlocfilehash: d7c23cbda0a5af4dc3fa6b2d9f59497acc9bf5ff
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505213"
---
# <a name="cmfcmenubutton-class"></a>CMFCMenuButton – třída

Tlačítko, které zobrazí místní nabídku a sestavy pro výběry v nabídce uživatele.

## <a name="syntax"></a>Syntaxe

```
class CMFCMenuButton : public CMFCButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CMFCMenuButton::CMFCMenuButton](#cmfcmenubutton)|`CMFCMenuButton` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CMFCMenuButton::PreTranslateMessage](#pretranslatemessage)|Volá se rozhraním, aby se mohly překládat zprávy oken předtím, než se odesílají. (Overrides `CMFCButton::PreTranslateMessage`.)|
|[CMFCMenuButton::SizeToContent](#sizetocontent)|Změní velikost tlačítka v závislosti na velikosti textu a obrázku.|

### <a name="data-members"></a>Datové členy

|Name|Popis|
|----------|-----------------|
|[CMFCMenuButton::m_bOSMenu](#m_bosmenu)|Určuje, zda se má zobrazit místní nabídka výchozí systém nebo zda má být použita možnost [CContextMenuManager:: TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu).|
|[CMFCMenuButton::m_bRightArrow](#m_brightarrow)|Určuje, zda se místní nabídka zobrazí pod tlačítkem nebo napravo od tlačítka.|
|[CMFCMenuButton::m_bStayPressed](#m_bstaypressed)|Určuje, zda tlačítko nabídky změní svůj stav poté, co uživatel uvolní tlačítko.|
|[CMFCMenuButton::m_hMenu](#m_hmenu)|Popisovač připojené nabídky systému Windows.|
|[CMFCMenuButton::m_nMenuResult](#m_nmenuresult)|Identifikátor, který označuje, kterou položku uživatel vybral z místní nabídky.|
|[CMFCMenuButton::m_bDefaultClick](#m_bdefaultclick)| Povolí zpracování výchozího nastavení (text/obrázek tlačítka na tlačítku).|

## <a name="remarks"></a>Poznámky

Třída je odvozena z [třídy CMFCButton](../../mfc/reference/cmfcbutton-class.md) , která je zase odvozena od [třídy CButton.](../../mfc/reference/cbutton-class.md) `CMFCMenuButton` Proto můžete použít `CMFCMenuButton` ve svém kódu stejným způsobem jako při použití `CButton`.

Když vytvoříte `CMFCMenuButton`, musíte předat popisovač do přidružené místní nabídky. Dále zavolejte funkci `CMFCMenuButton::SizeToContent`. `CMFCMenuButton::SizeToContent`kontroluje, zda je velikost tlačítka dostačující pro zahrnutí šipky, která odkazuje na umístění, kde se zobrazí automaticky otevírané okno – konkrétně pod nebo vpravo od tlačítka.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak nastavit popisovač nabídky připojené k tlačítku, změnit velikost tlačítka podle jeho velikosti textu a obrázku a nastavit místní nabídku, která je zobrazena v rámci rozhraní. Tento fragment kódu je součástí [ukázky nové ovládací prvky](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#38](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#39](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxmenubutton. h

##  <a name="cmfcmenubutton"></a>CMFCMenuButton::CMFCMenuButton

Vytvoří nový objekt [CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md) .

```
CMFCMenuButton();
```

##  <a name="m_bosmenu"></a>CMFCMenuButton::m_bOSMenu

Logická členská proměnná, která určuje, která místní nabídka se zobrazí v rozhraní.

```
BOOL m_bOSMenu;
```

### <a name="remarks"></a>Poznámky

Pokud `m_bOSMenu` má hodnotu true, rozhraní zavolá zděděnou `TrackPopupMenu` metodu pro tento objekt. V opačném případě rozhraní volá [CContextMenuManager:: TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu).

##  <a name="m_brightarrow"></a>CMFCMenuButton::m_bRightArrow

Logická proměnná členu, která určuje umístění místní nabídky.

```
BOOL m_bRightArrow;
```

### <a name="remarks"></a>Poznámky

Když uživatel stiskne tlačítko nabídky, aplikace zobrazí místní nabídku. V rozhraní se zobrazí místní nabídka buď pod tlačítkem, nebo napravo od tlačítka. Tlačítko má také malou šipku, která označuje, kde se zobrazí místní nabídka. Pokud `m_bRightArrow` je hodnota true, rozhraní zobrazí místní nabídku napravo od tlačítka. V opačném případě se zobrazí místní nabídka pod tlačítkem.

##  <a name="m_bstaypressed"></a>CMFCMenuButton::m_bStayPressed

Logická členská proměnná, která určuje, zda se tlačítko nabídky zobrazí, když uživatel provede výběr z místní nabídky.

```
BOOL m_bStayPressed;
```

### <a name="remarks"></a>Poznámky

Pokud je `m_bStayPressed` člen false, tlačítko nabídky se nestiskne při použití tlačítka na tlačítko. V tomto případě se v rozhraní zobrazí pouze místní nabídka.

Pokud má `m_bStayPressed` člen hodnotu true, tlačítko nabídky se stiskne, jakmile uživatel klikne na tlačítko. Zůstane stisknutá, dokud uživatel nezavře místní nabídku, a to buď provedením výběru, nebo zrušením.

##  <a name="m_hmenu"></a>CMFCMenuButton::m_hMenu

Popisovač připojené nabídky

```
HMENU m_hMenu;
```

### <a name="remarks"></a>Poznámky

Rozhraní zobrazí nabídku určenou touto členskou proměnnou, když uživatel klikne na tlačítko nabídky.

##  <a name="m_nmenuresult"></a>CMFCMenuButton::m_nMenuResult

Celé číslo, které označuje, kterou položku uživatel vybere z místní nabídky.

```
int m_nMenuResult;
```

### <a name="remarks"></a>Poznámky

Hodnota této členské proměnné je nula, pokud uživatel nabídku zruší bez provedení výběru, nebo pokud dojde k chybě.

##  <a name="m_bdefaultclick"></a>CMFCMenuButton::m_bDefaultClick

Umožňuje výchozí zpracování textu nebo obrázků na tlačítku.

```
BOOL  m_bDefaultClick;
```

### <a name="remarks"></a>Poznámky

Nastavením m_bDefaultClick na hodnotu false dojde k zobrazení nabídky po kliknutí na libovolné místo na tlačítku.

##  <a name="m_nmenuresult"></a>CMFCMenuButton::m_nMenuResult

Celé číslo, které označuje, kterou položku uživatel vybere z místní nabídky.

```
int m_nMenuResult;
```

### <a name="remarks"></a>Poznámky

##  <a name="pretranslatemessage"></a>CMFCMenuButton::P reTranslateMessage

Volá se rozhraním, aby se mohly překládat zprávy oken předtím, než se odesílají.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
pro Odkazuje na strukturu [MSG](/windows/win32/api/winuser/ns-winuser-msg) , která obsahuje zprávu ke zpracování.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla zpráva přeložena a neměla by být odeslána; 0, pokud nebyla zpráva přeložena a měla by být odeslána.

### <a name="remarks"></a>Poznámky

##  <a name="sizetocontent"></a>CMFCMenuButton::SizeToContent

Změní velikost tlačítka podle velikosti textu a velikosti obrázku.

```
virtual CSize SizeToContent(BOOL bCalcOnly = FALSE);
```

### <a name="parameters"></a>Parametry

*bCalcOnly*<br/>
pro Logický parametr, který určuje, zda tato metoda mění velikost tlačítka.

### <a name="return-value"></a>Návratová hodnota

Objekt [CSize](../../atl-mfc-shared/reference/csize-class.md) , který určuje novou velikost tlačítka.

### <a name="remarks"></a>Poznámky

Pokud tuto funkci zavoláte a *bCalcOnly* je true `SizeToContent` , vypočítá se jenom nová velikost tlačítka.

Nová velikost tlačítka je vypočítána tak, aby odpovídala textu, obrázku a šipce tlačítka. Rozhraní také přidá v předdefinovaných okrajích 10 pixelů pro vodorovnou hranu a 5 pixelů svislého okraje.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCButton – třída](../../mfc/reference/cmfcbutton-class.md)
