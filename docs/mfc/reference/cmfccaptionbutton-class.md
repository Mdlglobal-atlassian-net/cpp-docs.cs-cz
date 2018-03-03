---
title: "Třída CMFCCaptionButton | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 857054bd60e206cc3a563aa5f00b872f67c58d3f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfccaptionbutton-class"></a>CMFCCaptionButton – třída
`CMFCCaptionButton` Třída implementuje tlačítko, které se zobrazí na panelu popisek pro ukotvené podokno nebo zkrácená rámce okna. Obvykle rozhraní popisek tlačítka automaticky vytvoří.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCCaptionButton : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="constructors"></a>Konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCCaptionButton::CMFCCaptionButton](#cmfccaptionbutton)|Vytvoří objekt CMFCCaptionButton.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCCaptionButton::GetHit](#gethit)|Vrátí příkaz reprezentována tlačítko.|  
|[CMFCCaptionButton::GetIconID](#geticonid)|Vrátí ID bitové kopie přidružený tlačítko.|  
|[CMFCCaptionButton::GetRect](#getrect)|Vrátí rámeček obsazena tlačítko.|  
|[CMFCCaptionButton::GetSize](#getsize)|Vrátí šířka a výška tlačítko.|  
|[CMFCCaptionButton::IsMiniFrameButton](#isminiframebutton)|Označuje, zda je název výška panelu nastavit minimální velikost.|  
|[CMFCCaptionButton::Move](#move)|Nastaví tlačítko Kreslení umístění a okno zobrazení stavu.|  
|[CMFCCaptionButton::OnDraw](#ondraw)|Nakreslí tlačítko titulek.|  
|[CMFCCaptionButton::SetMiniFrameButton](#setminiframebutton)|Nastaví minimální velikost záhlaví.|  
  
## <a name="remarks"></a>Poznámky  
 Můžete odvození třídy z [CPaneFrameWnd třída](../../mfc/reference/cpaneframewnd-class.md) a použít metodu chráněné `AddButton`, přidejte popisek tlačítka mini rámce okna.  
  
 CPaneFrameWnd.h definuje ID příkazu pro dva typy popisek tlačítka:  
  
- `AFX_CAPTION_BTN_PIN`, který zobrazí tlačítko PIN kód, když podokně ukotvení podporuje režim automaticky skrýt.  
  
- `AFX_CAPTION_BTN_CLOSE`, které zobrazí **Zavřít** když v podokně můžete uzavřený nebo skrytý.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit `CMFCCaptionButton` objektu a nastavit minimální velikost záhlaví.  
  
 [!code-cpp[NVC_MFC_RibbonApp#43](../../mfc/reference/codesnippet/cpp/cmfccaptionbutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCCaptionButton](../../mfc/reference/cmfccaptionbutton-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcaptionbutton.h  
  
##  <a name="cmfccaptionbutton"></a>CMFCCaptionButton::CMFCCaptionButton  
 Vytvoří `CMFCCaptionButton` objektu.  
  
```  
CMFCCaptionButton();

 
CMFCCaptionButton(
    UINT nHit,  
    BOOL bLeftAlign = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nHit`  
 Příkaz přidružený tlačítko.  
  
 [v]`bLeftAlign`  
 Určuje, zda je tlačítko zarovnán doleva.  
  
 Následující tabulka uvádí možné hodnoty pro `nHit` parametr.  
  
|Hodnota|Příkaz|  
|-----------|-------------|  
|`AFX_HTCLOSE`|Tlačítko Zavřít.|  
|`HTMINBUTTON`|Tlačítka minimalizujte.|  
|`HTMAXBUTTON`|Tlačítko maximalizujte.|  
|`AFX_HTLEFTBUTTON`|Tlačítko šipku vlevo.|  
|`AFX_HTRIGHTBUTTON`|Tlačítko se šipkou vpravo.|  
|`AFX_HTMENU`|Šipku dolů nabídky.|  
|`HTNOWHERE`|Výchozí hodnota. představuje žádný příkaz.|  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení nejsou popisek tlačítka přidružené příkaz.  
  
 Popisek tlačítka je zarovnán buď na doleva či doprava.  
  
##  <a name="gethit"></a>CMFCCaptionButton::GetHit  
 Vrátí příkaz reprezentována tlačítko.  
  
```  
UINT GetHit() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Příkaz reprezentována tlačítko.  
  
 Následující tabulka uvádí možné vrácené hodnoty.  
  
|Hodnota|Příkaz|  
|-----------|-------------|  
|`AFX_HTCLOSE`|Tlačítko Zavřít.|  
|`HTMINBUTTON`|Tlačítka minimalizujte.|  
|`HTMAXBUTTON`|Tlačítko maximalizujte.|  
|`AFX_HTLEFTBUTTON`|Tlačítko šipku vlevo.|  
|`AFX_HTRIGHTBUTTON`|Tlačítko se šipkou vpravo.|  
|`AFX_HTMENU`|Šipku dolů nabídky.|  
|`HTNOWHERE`|Výchozí hodnota. představuje žádný příkaz.|  
  
##  <a name="geticonid"></a>CMFCCaptionButton::GetIconID  
 Vrátí ID bitové kopie přidružený tlačítko.  
  
```  
virtual CMenuImages::IMAGES_IDS GetIconID(
    BOOL bHorz,  
    BOOL bMaximized = FALSE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bHorz`  
 `TRUE`Šipka doleva nebo doprava bitové kopie ID; `FALSE` pro nahoru nebo šipku dolů bitové kopie ID.  
  
 [v]`bMaximized`  
 `TRUE`pro bitovou kopii s ID maximalizovat; `FALSE` minimalizovat bitové kopie ID.  
  
### <a name="return-value"></a>Návratová hodnota  
 ID obrázku.  
  
### <a name="remarks"></a>Poznámky  
 Parametry zadejte ID bitové kopie pro minimalizaci nebo maximalizovat popisek tlačítka.  
  
##  <a name="getrect"></a>CMFCCaptionButton::GetRect  
 Vrátí rámeček obsazena tlačítko.  
  
```  
virtual CRect GetRect() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Obdélníku, která představuje umístění tlačítka.  
  
### <a name="remarks"></a>Poznámky  
 Pokud tlačítko nevidíte, velikost vrátil je 0.  
  
##  <a name="getsize"></a>CMFCCaptionButton::GetSize  
 Vrátí šířka a výška tlačítko.  
  
```  
static CSize GetSize();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vnější dimenze tlačítka.  
  
### <a name="remarks"></a>Poznámky  
 Velikost vrátil zahrnuje okrajem tlačítko a ohraničení.  
  
##  <a name="isminiframebutton"></a>CMFCCaptionButton::IsMiniFrameButton  
 Označuje, zda je název výška panelu nastavit minimální velikost.  
  
```  
BOOL IsMiniFrameButton() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud nastavení titulek mini velikost; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="move"></a>CMFCCaptionButton::Move  
 Nastaví tlačítko Kreslení umístění a okno zobrazení stavu.  
  
```  
void Move(
    const CPoint& ptTo,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`ptTo`  
 Nové umístění.  
  
 [v]`bHide`  
 Určuje, zda se zobrazí tlačítko.  
  
##  <a name="ondraw"></a>CMFCCaptionButton::OnDraw  
 Nakreslí tlačítko titulek.  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    BOOL bActive,  
    BOOL bHorz = TRUE,  
    BOOL bMaximized = TRUE,  
    BOOL bDisabled = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Ukazatel na kontext zařízení pro tlačítko.  
  
 [v]`bActive`  
 Určuje, zda se k vykreslení bitovou kopii aktivní tlačítko.  
  
 [v]`bHorz`  
 Vyhrazené pro použití v odvozené třídě.  
  
 [v]`bMaximized`  
 Určuje, zda se k vykreslení obrázek tlačítka maximalizovaném okně.  
  
 [v]`bDisabled`  
 Určuje, zda se k vykreslení image povoleno tlačítko.  
  
### <a name="remarks"></a>Poznámky  
 `bMaximized` Parametr se používá při tlačítko Maximalizovat nebo minimalizovat tlačítko.  
  
##  <a name="setminiframebutton"></a>CMFCCaptionButton::SetMiniFrameButton  
 Nastaví minimální velikost záhlaví.  
  
```  
void SetMiniFramebutton(BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bSet`  
 `TRUE`pro výška panelu mini title; `FALSE` pro výchozí název panelu výšku.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CPaneFrameWnd – třída](../../mfc/reference/cpaneframewnd-class.md)   
 [CDockablePane – třída](../../mfc/reference/cdockablepane-class.md)
