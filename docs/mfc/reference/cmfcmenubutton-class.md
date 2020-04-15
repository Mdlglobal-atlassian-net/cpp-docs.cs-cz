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
ms.openlocfilehash: 929fc1c8166f249fe3babc724b2c0bcd9cb99676
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369675"
---
# <a name="cmfcmenubutton-class"></a>CMFCMenuButton – třída

Tlačítko, které zobrazuje rozbalovací nabídku a hlásí výběr nabídky uživatele.

## <a name="syntax"></a>Syntaxe

```
class CMFCMenuButton : public CMFCButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCMenuButton::TLAČÍTKO CMFCMenu](#cmfcmenubutton)|Vytvoří `CMFCMenuButton` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCMenuButton::PreTranslateMessage](#pretranslatemessage)|Volat rámci přeložit okno zprávy před jejich odesláním. (Přepíše `CMFCButton::PreTranslateMessage`.)|
|[CMFCMenuButton::SizeToContent](#sizetocontent)|Změní velikost tlačítka podle jeho textu a velikosti obrázku.|

### <a name="data-members"></a>Členové dat

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCMenuButton::m_bOSMenu](#m_bosmenu)|Určuje, zda se má zobrazit výchozí automaticky otevíraná nabídka systému nebo zda se má použít [cContextMenuManager::TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu).|
|[CMFCMenuButton::m_bRightArrow](#m_brightarrow)|Určuje, zda se rozbalovací nabídka zobrazí pod tlačítkem nebo vpravo od něj.|
|[CMFCMenuButton::m_bStayPressed](#m_bstaypressed)|Určuje, zda tlačítko nabídky změní svůj stav poté, co uživatel tlačítko uvolní.|
|[CMFCMenuButton::m_hMenu](#m_hmenu)|Úchyt k připojené nabídce systému Windows.|
|[CMFCMenuButton::m_nMenuResult](#m_nmenuresult)|Identifikátor, který označuje, kterou položku uživatel vybral z rozbalovací nabídky.|
|[CMFCMenuButton::m_bDefaultClick](#m_bdefaultclick)| Povolit výchozí zpracování (na tlačítku text/obrázek).|

## <a name="remarks"></a>Poznámky

Třída `CMFCMenuButton` je odvozena z [třídy CMFCButton,](../../mfc/reference/cmfcbutton-class.md) která je zase odvozena z [třídy CButton](../../mfc/reference/cbutton-class.md). Proto můžete použít `CMFCMenuButton` v kódu stejným způsobem, `CButton`jako byste použili .

Při vytváření `CMFCMenuButton`je nutné předat popisovač přidružené rozbalovací nabídce. Dále zavolejte `CMFCMenuButton::SizeToContent`funkci . `CMFCMenuButton::SizeToContent`zkontroluje, zda je velikost tlačítka dostatečná pro zahrnutí šipky, která ukazuje na místo, kde se zobrazí vyskakovací okno - jmenovitě pod nebo vpravo od tlačítka.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak nastavit úchyt nabídky připojené k tlačítku, změnit velikost tlačítka podle jeho velikosti textu a obrázku a nastavit rozbalovací nabídku, která je zobrazena v rámci. Tento fragment kódu je součástí [ukázky Nové ovládací prvky](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#38](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#39](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CmFCButton](../../mfc/reference/cmfcbutton-class.md)

[Tlačítko CMFCMenu](../../mfc/reference/cmfcmenubutton-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxmenubutton.h

## <a name="cmfcmenubuttoncmfcmenubutton"></a><a name="cmfcmenubutton"></a>CMFCMenuButton::TLAČÍTKO CMFCMenu

Vytvoří nový objekt [CMFCMenuButton.](../../mfc/reference/cmfcmenubutton-class.md)

```
CMFCMenuButton();
```

## <a name="cmfcmenubuttonm_bosmenu"></a><a name="m_bosmenu"></a>CMFCMenuButton::m_bOSMenu

Logická členská proměnná, která označuje, které rozbalovací nabídky rozhraní zobrazí.

```
BOOL m_bOSMenu;
```

### <a name="remarks"></a>Poznámky

Pokud `m_bOSMenu` je TRUE, framework volá `TrackPopupMenu` zděděnou metodu pro tento objekt. V opačném případě framework volá [CContextMenuManager::TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu).

## <a name="cmfcmenubuttonm_brightarrow"></a><a name="m_brightarrow"></a>CMFCMenuButton::m_bRightArrow

Logická členská proměnná, která označuje umístění rozbalovací nabídky.

```
BOOL m_bRightArrow;
```

### <a name="remarks"></a>Poznámky

Když uživatel stiskne tlačítko nabídky, aplikace zobrazí rozbalovací nabídku. V rámci se zobrazí rozbalovací menu buď pod tlačítkem, nebo vpravo od tlačítka. Tlačítko má také malou šipku, která označuje, kde se zobrazí rozbalovací nabídka. Pokud `m_bRightArrow` je TRUE, rozhraní zobrazí rozbalovací nabídku napravo od tlačítka. V opačném případě se pod tlačítkem zobrazí rozbalovací nabídka.

## <a name="cmfcmenubuttonm_bstaypressed"></a><a name="m_bstaypressed"></a>CMFCMenuButton::m_bStayPressed

Logická členská proměnná, která označuje, zda se tlačítko nabídky zobrazí stisknuté, zatímco uživatel provede výběr z rozbalovací nabídky.

```
BOOL m_bStayPressed;
```

### <a name="remarks"></a>Poznámky

Pokud `m_bStayPressed` je člen FALSE, tlačítko nabídky se nestiskne, když použije tlačítko. V tomto případě se v rámci zobrazí pouze rozbalovací nabídka.

Pokud `m_bStayPressed` je člen TRUE, tlačítko nabídky se stiskne, když uživatel klepne na tlačítko. Zůstane stisknuto až poté, co uživatel zavře rozbalovací nabídku, a to buď provedením výběru nebo zrušením.

## <a name="cmfcmenubuttonm_hmenu"></a><a name="m_hmenu"></a>CMFCMenuButton::m_hMenu

Úchyt do připojené nabídky.

```
HMENU m_hMenu;
```

### <a name="remarks"></a>Poznámky

Rozhraní Framework zobrazí nabídku označenou touto členovou proměnnou, když uživatel klepne na tlačítko nabídky.

## <a name="cmfcmenubuttonm_nmenuresult"></a><a name="m_nmenuresult"></a>CMFCMenuButton::m_nMenuResult

Celé číslo, které označuje, kterou položku uživatel vybere z rozbalovací nabídky.

```
int m_nMenuResult;
```

### <a name="remarks"></a>Poznámky

Hodnota této členské proměnné je nulová, pokud uživatel zruší nabídku bez provedení výběru nebo pokud dojde k chybě.

## <a name="cmfcmenubuttonm_bdefaultclick"></a><a name="m_bdefaultclick"></a>CMFCMenuButton::m_bDefaultClick

Umožňuje výchozí zpracování textu nebo obrázků na tlačítku.

```
BOOL  m_bDefaultClick;
```

### <a name="remarks"></a>Poznámky

Nastavení m_bDefaultClick na false způsobí, že se tlačítko zobrazí po klepnutí na libovolné místo na tlačítku.

## <a name="cmfcmenubuttonm_nmenuresult"></a><a name="m_nmenuresult"></a>CMFCMenuButton::m_nMenuResult

Celé číslo, které označuje, kterou položku uživatel vybere z rozbalovací nabídky.

```
int m_nMenuResult;
```

### <a name="remarks"></a>Poznámky

## <a name="cmfcmenubuttonpretranslatemessage"></a><a name="pretranslatemessage"></a>CMFCMenuButton::PreTranslateMessage

Volat rámci přeložit okno zprávy před jejich odesláním.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
[v] Odkazuje na strukturu [MSG,](/windows/win32/api/winuser/ns-winuser-msg) která obsahuje zprávu ke zpracování.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla zpráva přeložena a neměla by být odeslána; 0, pokud zpráva nebyla přeložena a měla by být odeslána.

### <a name="remarks"></a>Poznámky

## <a name="cmfcmenubuttonsizetocontent"></a><a name="sizetocontent"></a>CMFCMenuButton::SizeToContent

Změní velikost tlačítka podle velikosti textu a velikosti obrázku.

```
virtual CSize SizeToContent(BOOL bCalcOnly = FALSE);
```

### <a name="parameters"></a>Parametry

*bCalcOnly*<br/>
[v] Logický parametr, který označuje, zda tato metoda změní velikost tlačítka .

### <a name="return-value"></a>Návratová hodnota

[CSize](../../atl-mfc-shared/reference/csize-class.md) objekt, který určuje novou velikost tlačítka.

### <a name="remarks"></a>Poznámky

Pokud zavoláte tuto funkci a *bCalcOnly* je TRUE, `SizeToContent` vypočítá pouze novou velikost tlačítka.

Nová velikost tlačítka se vypočítá tak, aby odpovídala textu, obrázku a šipkě tlačítka. Rozhraní také přidá předdefinované okraje 10 pixelů pro vodorovný okraj a 5 pixelů pro svislou hranu.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCButton – třída](../../mfc/reference/cmfcbutton-class.md)
