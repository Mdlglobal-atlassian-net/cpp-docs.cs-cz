---
title: Cmfccaptionbutton – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetHit
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetIconID
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetRect
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetSize
- AFXCAPTIONBUTTON/CMFCCaptionButton::IsMiniFrameButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::Move
- AFXCAPTIONBUTTON/CMFCCaptionButton::OnDraw
- AFXCAPTIONBUTTON/CMFCCaptionButton::SetMiniFrameButton
dev_langs:
- C++
helpviewer_keywords:
- CMFCCaptionButton [MFC], CMFCCaptionButton
- CMFCCaptionButton [MFC], GetHit
- CMFCCaptionButton [MFC], GetIconID
- CMFCCaptionButton [MFC], GetRect
- CMFCCaptionButton [MFC], GetSize
- CMFCCaptionButton [MFC], IsMiniFrameButton
- CMFCCaptionButton [MFC], Move
- CMFCCaptionButton [MFC], OnDraw
- CMFCCaptionButton [MFC], SetMiniFrameButton
ms.assetid: c5774b38-c0dd-414a-9ede-3b2f78f233ec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c3e9c9e5122e4bef7007a767fb3225483984e11d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711682"
---
# <a name="cmfccaptionbutton-class"></a>Cmfccaptionbutton – třída
`CMFCCaptionButton` Třída implementuje tlačítka, který se zobrazí v záhlaví pro ukotvené podokno nebo okno s minirámcem. Obvykle rozhraní vytvoří titulek tlačítka automaticky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCCaptionButton : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="constructors"></a>Konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCCaptionButton::CMFCCaptionButton](#cmfccaptionbutton)|Vytvoří objekt cmfccaptionbutton –.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCCaptionButton::GetHit](#gethit)|Vrátí příkaz, reprezentovaný tlačítka.|  
|[CMFCCaptionButton::GetIconID](#geticonid)|Vrátí ID bitové kopie přidružený k tlačítku.|  
|[CMFCCaptionButton::GetRect](#getrect)|Vrací obdélník obsazena na tlačítko.|  
|[CMFCCaptionButton::GetSize](#getsize)|Vrátí šířku a výšku tlačítka.|  
|[CMFCCaptionButton::IsMiniFrameButton](#isminiframebutton)|Označuje, zda height název řádku je nastavena na minimální velikost.|  
|[CMFCCaptionButton::Move](#move)|Nastaví umístění příkazu pro vykreslení tlačítko a zobrazit stav okna.|  
|[CMFCCaptionButton::OnDraw](#ondraw)|Nakreslí titulek tlačítka.|  
|[CMFCCaptionButton::SetMiniFrameButton](#setminiframebutton)|Nastaví minimální velikost záhlaví okna.|  
  
## <a name="remarks"></a>Poznámky  
 Můžete odvozovat třídu z [cpaneframewnd – třída](../../mfc/reference/cpaneframewnd-class.md) a používat chráněné metody `AddButton`, přidejte popisek tlačítka mini rámce okna.  
  
 CPaneFrameWnd.h definuje ID příkazu pro dva druhy titulek tlačítka:  
  
- AFX_CAPTION_BTN_PIN, které se zobrazí tlačítko Připnutí po ukotvené podokno podporuje režim automatického skrytí.  
  
- AFX_CAPTION_BTN_CLOSE, který se zobrazí **Zavřít** tlačítko podokna můžete uzavřeny nebo skrytý.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit `CMFCCaptionButton` objektu a nastavíte minimální velikost záhlaví.  
  
 [!code-cpp[NVC_MFC_RibbonApp#43](../../mfc/reference/codesnippet/cpp/cmfccaptionbutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [Cmfccaptionbutton –](../../mfc/reference/cmfccaptionbutton-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcaptionbutton.h  
  
##  <a name="cmfccaptionbutton"></a>  CMFCCaptionButton::CMFCCaptionButton  
 Vytvoří `CMFCCaptionButton` objektu.  
  
```  
CMFCCaptionButton();

 
CMFCCaptionButton(
    UINT nHit,  
    BOOL bLeftAlign = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
*nHit*<br/>
[in] Příkaz přidružený k tlačítku.  
  
*bLeftAlign*<br/>
[in] Určuje, zda tlačítko je umístěno na levé straně.  
  
 V následující tabulce jsou uvedeny možné hodnoty pro *nHit* parametru.  
  
|Hodnota|Příkaz|  
|-----------|-------------|  
|AFX_HTCLOSE|Tlačítko Zavřít.|  
|HTMINBUTTON|Tlačítko minimalizujte.|  
|HTMAXBUTTON|Tlačítko maximalizace.|  
|AFX_HTLEFTBUTTON|Tlačítko šipka vlevo.|  
|AFX_HTRIGHTBUTTON|Tlačítko se šipkou vpravo.|  
|AFX_HTMENU|Šipku dolů nabídky.|  
|HTNOWHERE|Výchozí hodnota. představuje žádný příkaz.|  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení nejsou přidružené příkaz Titulek tlačítka.  
  
 Titulek tlačítka jsou zarovnána doprava nebo doleva.  
  
##  <a name="gethit"></a>  CMFCCaptionButton::GetHit  
 Vrátí příkaz, reprezentovaný tlačítka.  
  
```  
UINT GetHit() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Příkaz, reprezentovaný tlačítka.  
  
 Následující tabulka obsahuje seznam možných vrácených hodnot.  
  
|Hodnota|Příkaz|  
|-----------|-------------|  
|AFX_HTCLOSE|Tlačítko Zavřít.|  
|HTMINBUTTON|Tlačítko minimalizujte.|  
|HTMAXBUTTON|Tlačítko maximalizace.|  
|AFX_HTLEFTBUTTON|Tlačítko šipka vlevo.|  
|AFX_HTRIGHTBUTTON|Tlačítko se šipkou vpravo.|  
|AFX_HTMENU|Šipku dolů nabídky.|  
|HTNOWHERE|Výchozí hodnota. představuje žádný příkaz.|  
  
##  <a name="geticonid"></a>  CMFCCaptionButton::GetIconID  
 Vrátí ID bitové kopie přidružený k tlačítku.  
  
```  
virtual CMenuImages::IMAGES_IDS GetIconID(
    BOOL bHorz,  
    BOOL bMaximized = FALSE) const;  
```  
  
### <a name="parameters"></a>Parametry  
*bHorz*<br/>
[in] Hodnota TRUE pro image šipka doleva nebo doprava ID; FALSE pro navýšení nebo snížení kapacity obrázku šipky ID.  
  
*bMaximized*<br/>
[in] Hodnota TRUE pro ID bitové kopie maximalizovat; FALSE pro ID minimalizovat bitové kopie.  
  
### <a name="return-value"></a>Návratová hodnota  
 ID bitové kopie.  
  
### <a name="remarks"></a>Poznámky  
 Parametry zadejte ID obrázku pro minimalizovat nebo maximalizovat titulek tlačítka.  
  
##  <a name="getrect"></a>  CMFCCaptionButton::GetRect  
 Vrací obdélník obsazena na tlačítko.  
  
```  
virtual CRect GetRect() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Obdélník, který představuje umístění tlačítka.  
  
### <a name="remarks"></a>Poznámky  
 Pokud tlačítko nevidíte, je velikost vrátí 0.  
  
##  <a name="getsize"></a>  CMFCCaptionButton::GetSize  
 Vrátí šířku a výšku tlačítka.  
  
```  
static CSize GetSize();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vnější dimenze na tlačítko.  
  
### <a name="remarks"></a>Poznámky  
 Velikostí vrácenou obsahuje tlačítko okraj a okraj.  
  
##  <a name="isminiframebutton"></a>  CMFCCaptionButton::IsMiniFrameButton  
 Označuje, zda height název řádku je nastavena na minimální velikost.  
  
```  
BOOL IsMiniFrameButton() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud je popisek nastavený na minimální velikost. v opačném případě FALSE.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="move"></a>  CMFCCaptionButton::Move  
 Nastaví umístění příkazu pro vykreslení tlačítko a zobrazit stav okna.  
  
```  
void Move(
    const CPoint& ptTo,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
*ptTo*<br/>
[in] Nové umístění.  
  
*bHide*<br/>
[in] Určuje, zda je zobrazeno tlačítko.  
  
##  <a name="ondraw"></a>  CMFCCaptionButton::OnDraw  
 Nakreslí titulek tlačítka.  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    BOOL bActive,  
    BOOL bHorz = TRUE,  
    BOOL bMaximized = TRUE,  
    BOOL bDisabled = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
*primární řadič domény*<br/>
[in] Ukazatel na kontext zařízení pro tlačítko.  
  
*bActive*<br/>
[in] Určuje, zda vykreslení obrázku tlačítka aktivní.  
  
*bHorz*<br/>
[in] Vyhrazené pro použití v odvozené třídě.  
  
*bMaximized*<br/>
[in] Určuje, zda chcete-li nakreslit obrázek maximalizované tlačítka.  
  
*bDisabled*<br/>
[in] Určuje, zda vykreslení obrázku povolené tlačítko.  
  
### <a name="remarks"></a>Poznámky  
 *BMaximized* parametr se používá, když je tlačítko Maximalizovat nebo tlačítko Minimalizovat.  
  
##  <a name="setminiframebutton"></a>  CMFCCaptionButton::SetMiniFrameButton  
 Nastaví minimální velikost záhlaví okna.  
  
```  
void SetMiniFramebutton(BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
*bSet*<br/>
[in] Hodnota TRUE pro Výška pruhu mini názvu; FALSE pro Výška pruhu výchozí název.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [Cpaneframewnd – třída](../../mfc/reference/cpaneframewnd-class.md)   
 [CDockablePane – třída](../../mfc/reference/cdockablepane-class.md)
