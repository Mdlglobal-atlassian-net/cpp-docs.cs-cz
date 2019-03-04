---
title: Cmfcmenubutton – třída
ms.date: 11/04/2016
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
helpviewer_keywords:
- CMFCMenuButton [MFC], CMFCMenuButton
- CMFCMenuButton [MFC], PreTranslateMessage
- CMFCMenuButton [MFC], SizeToContent
- CMFCMenuButton [MFC], m_bOSMenu
- CMFCMenuButton [MFC], m_bRightArrow
- CMFCMenuButton [MFC], m_bStayPressed
- CMFCMenuButton [MFC], m_hMenu
- CMFCMenuButton [MFC], m_nMenuResult
ms.assetid: 53d3d459-1e5a-47c5-8b7f-2e61f6af5187
ms.openlocfilehash: bacd8726fd4c833f956f763cca81a88d41d1f167
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57298201"
---
# <a name="cmfcmenubutton-class"></a>Cmfcmenubutton – třída

Tlačítko, které zobrazí místní nabídku, informuje o možnosti nabídky uživatele.

## <a name="syntax"></a>Syntaxe

```
class CMFCMenuButton : public CMFCButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCMenuButton::CMFCMenuButton](#cmfcmenubutton)|Vytvoří `CMFCMenuButton` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCMenuButton::PreTranslateMessage](#pretranslatemessage)|Volá se rozhraním před odesláním přeložit zprávy okna. (Přepíše `CMFCButton::PreTranslateMessage`.)|
|[CMFCMenuButton::SizeToContent](#sizetocontent)|Změní velikost tlačítka podle velikosti jeho textu a obrázků.|

### <a name="data-members"></a>Datové členy

|Název|Popis|
|----------|-----------------|
|[CMFCMenuButton::m_bOSMenu](#m_bosmenu)|Určuje, zda chcete zobrazit výchozí rozbalovací nabídky systému nebo použít [CContextMenuManager::TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu).|
|[CMFCMenuButton::m_bRightArrow](#m_brightarrow)|Určuje, zda v rozbalovací nabídce se zobrazí pod nebo napravo od panelu.|
|[CMFCMenuButton::m_bStayPressed](#m_bstaypressed)|Určuje, zda tlačítko nabídky po uživatel uvolní tlačítko změní svůj stav.|
|[CMFCMenuButton::m_hMenu](#m_hmenu)|Popisovač pro připojené nabídku Windows.|
|[CMFCMenuButton::m_nMenuResult](#m_nmenuresult)|Identifikátor, který určuje položky, které uživatel vybral v místní nabídce.|

## <a name="remarks"></a>Poznámky

`CMFCMenuButton` Je třída odvozena z [cmfcbutton – třída](../../mfc/reference/cmfcbutton-class.md) který je zase odvozen z [CButton – třída](../../mfc/reference/cbutton-class.md). Proto můžete použít `CMFCMenuButton` ve vašem kódu, stejně jako byste použili `CButton`.

Když vytvoříte `CMFCMenuButton`, je nutné předat v popisovač do přidružené rozbalovací nabídky. V dalším kroku zavolejte funkci `CMFCMenuButton::SizeToContent`. `CMFCMenuButton::SizeToContent` kontroluje, zda je velikost tlačítka dostatečná zahrnují šipky, která odkazuje na umístění, kde se zobrazí v automaticky otevíraném okně – konkrétně pod nebo napravo od panelu.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak nastavit popisovač nabídky připojeno k tlačítku, změňte velikost tlačítka podle velikosti jeho textu a obrázků a nastavit v rozbalovací nabídce, která se zobrazí v rámci rozhraní. Tento fragment kódu je součástí [nové ovládací prvky ukázka](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#38](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#39](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxmenubutton.h

##  <a name="cmfcmenubutton"></a>  CMFCMenuButton::CMFCMenuButton

Sestaví nový [cmfcmenubutton –](../../mfc/reference/cmfcmenubutton-class.md) objektu.

```
CMFCMenuButton();
```

##  <a name="m_bosmenu"></a>  CMFCMenuButton::m_bOSMenu

Logická členskou proměnnou, která označuje, které rozbalovací nabídky zobrazí rozhraní.

```
BOOL m_bOSMenu;
```

### <a name="remarks"></a>Poznámky

Pokud `m_bOSMenu` má hodnotu TRUE, volá framework zděděnou `TrackPopupMenu` metody pro tento objekt. V opačném případě volá framework [CContextMenuManager::TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu).

##  <a name="m_brightarrow"></a>  CMFCMenuButton::m_bRightArrow

Logická členské proměnné, která určuje umístění v místní nabídce.

```
BOOL m_bRightArrow;
```

### <a name="remarks"></a>Poznámky

Když uživatel stiskne tlačítko nabídky, aplikace zobrazí rozbalovací nabídky. Rozhraní se zobrazí v rozbalovací nabídce pod tlačítkem nebo napravo od panelu. Tlačítko také má malou šipku, která určuje, kde se objeví v rozbalovací nabídce. Pokud `m_bRightArrow` má hodnotu TRUE, zobrazí rozhraní v rozbalovací nabídce na pravé straně tlačítka. V opačném případě zobrazí rozbalovací nabídce pod tlačítkem.

##  <a name="m_bstaypressed"></a>  CMFCMenuButton::m_bStayPressed

Logická členské proměnné, která určuje, zda se zobrazí tlačítko stiskne, když uživatel provede výběru v místní nabídce.

```
BOOL m_bStayPressed;
```

### <a name="remarks"></a>Poznámky

Pokud `m_bStayPressed` člen je FALSE, na tlačítko nabídky stane nestisknutý při, že uživatel klikne na tlačítko. V tomto případě rozhraní zobrazí pouze v místní nabídce.

Pokud `m_bStayPressed` člen je hodnota TRUE, bude stisknutí tlačítka nabídky, když uživatel klikne na tlačítko. Zůstane při stisknutí až poté, co uživatel zavře v rozbalovací nabídce buď výběrem nebo zrušením.

##  <a name="m_hmenu"></a>  CMFCMenuButton::m_hMenu

Popisovač nabídky připojené.

```
HMENU m_hMenu;
```

### <a name="remarks"></a>Poznámky

V nabídce indikován této členské proměnné, když uživatel klikne na tlačítko nabídky zobrazí rozhraní.

##  <a name="m_nmenuresult"></a>  CMFCMenuButton::m_nMenuResult

Celé číslo, které označuje, která položka uživatel vybere z místní nabídky.

```
int m_nMenuResult;
```

### <a name="remarks"></a>Poznámky

Hodnota této proměnné člena je nula, pokud uživatel zruší nabídce bez výběru nebo pokud dojde k chybě.

##  <a name="pretranslatemessage"></a>  CMFCMenuButton::PreTranslateMessage

Volá se rozhraním před odesláním přeložit zprávy okna.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
[in] Odkazuje [MSG](/windows/desktop/api/winuser/ns-winuser-tagmsg) struktura, která obsahuje zprávu zpracovat.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud zpráva byl přeložen a by neměl být odeslána; 0, pokud zpráva nebyl přeložen a by měla být odeslána.

### <a name="remarks"></a>Poznámky

##  <a name="sizetocontent"></a>  CMFCMenuButton::SizeToContent

Změní velikost tlačítka podle jeho velikost písma a velikost bitové kopie.

```
virtual CSize SizeToContent(BOOL bCalcOnly = FALSE);
```

### <a name="parameters"></a>Parametry

*bCalcOnly*<br/>
[in] Parametr logické hodnoty označující, zda tato metoda mění velikost tlačítka.

### <a name="return-value"></a>Návratová hodnota

A [CSize](../../atl-mfc-shared/reference/csize-class.md) objekt, který určuje novou velikost tlačítka.

### <a name="remarks"></a>Poznámky

Při volání této funkce a *bCalcOnly* má hodnotu TRUE, `SizeToContent` bude počítat pouze novou velikost tlačítka.

Nová velikost tlačítka se počítá podle textu tlačítka, image a šipky. Rozhraní framework přidává předdefinované okrajů 10 pixelů pro vodorovné edge a 5 pixelů pro vertikální edge.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCButton – třída](../../mfc/reference/cmfcbutton-class.md)
