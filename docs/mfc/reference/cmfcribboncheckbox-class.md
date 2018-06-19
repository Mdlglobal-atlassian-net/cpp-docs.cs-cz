---
title: Třída CMFCRibbonCheckBox | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetCompactSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetIntermediateSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetRegularSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::IsDrawTooltipImage
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDraw
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDrawMenuImage
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDrawOnList
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::SetACCData
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonCheckBox [MFC], CMFCRibbonCheckBox
- CMFCRibbonCheckBox [MFC], GetCompactSize
- CMFCRibbonCheckBox [MFC], GetIntermediateSize
- CMFCRibbonCheckBox [MFC], GetRegularSize
- CMFCRibbonCheckBox [MFC], IsDrawTooltipImage
- CMFCRibbonCheckBox [MFC], OnDraw
- CMFCRibbonCheckBox [MFC], OnDrawMenuImage
- CMFCRibbonCheckBox [MFC], OnDrawOnList
- CMFCRibbonCheckBox [MFC], SetACCData
ms.assetid: 3a6c3891-c8d1-4af0-b954-7b9ab048782a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 109c3b2f6337adece6c371f1fafa98291468485e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369704"
---
# <a name="cmfcribboncheckbox-class"></a>CMFCRibbonCheckBox – třída
`CMFCRibbonCheckBox` Třída implementuje zaškrtávací políčko, které můžete přidat k nabídce panelu, panel nástrojů Rychlý přístup nebo automaticky otevíraného okna pásu karet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonCheckBox : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonCheckBox::CMFCRibbonCheckBox](#cmfcribboncheckbox)|Konstruktor|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonCheckBox::GetCompactSize](#getcompactsize)|(Přepisuje [CMFCRibbonButton::GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize).)|  
|[CMFCRibbonCheckBox::GetIntermediateSize](#getintermediatesize)|(Přepisuje [CMFCRibbonButton::GetIntermediateSize](../../mfc/reference/cmfcribbonbutton-class.md#getintermediatesize).)|  
|[CMFCRibbonCheckBox::GetRegularSize](#getregularsize)|(Přepisuje [CMFCRibbonButton::GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize).)|  
|[CMFCRibbonCheckBox::IsDrawTooltipImage](#isdrawtooltipimage)|(Přepisuje `CMFCRibbonButton::IsDrawTooltipImage`.)|  
|[CMFCRibbonCheckBox::OnDraw](#ondraw)|(Přepisuje [CMFCRibbonButton::OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw).)|  
|[CMFCRibbonCheckBox::OnDrawMenuImage](#ondrawmenuimage)|(Přepisuje [CMFCRibbonBaseElement::OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage).)|  
|[CMFCRibbonCheckBox::OnDrawOnList](#ondrawonlist)|(Přepisuje `CMFCRibbonButton::OnDrawOnList`.)|  
|[CMFCRibbonCheckBox::SetACCData](#setaccdata)|(Přepisuje [CMFCRibbonButton::SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata).)|  
  
## <a name="remarks"></a>Poznámky  
 Použít `CMFCRibbonCheckBox` ve vaší aplikaci, přidejte následující konstruktor kódu:  
  
```  
CMFCRibbonCheckBox (UINT nID, LPCTSTR lpszText)  
```  
kde `nID` je ID příkazu, který zaškrtávací políčko a `lpszText` je textový popisek zaškrtávacího políčka.  
  
 Zaškrtávací políčko můžete přidat na panel pásu karet pomocí [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonCheckBox](../../mfc/reference/cmfcribboncheckbox-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxribboncheckbox.h  
  
##  <a name="cmfcribboncheckbox"></a>  CMFCRibbonCheckBox::CMFCRibbonCheckBox  
 Konstruktor objektu políčko pásu karet  
  
```  
CMFCRibbonCheckBox(
    UINT nID,  
    LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nID`  
 Určuje ID příkazu.  
  
 [v] `lpszText`  
 Určuje text popisku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vytvoří objekt políčko pásu karet.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit objekt `CMFCRibbonCheckBox` třídy.  
  
 [!code-cpp[NVC_MFC_RibbonApp#17](../../mfc/reference/codesnippet/cpp/cmfcribboncheckbox-class_1.cpp)]  
  
##  <a name="getcompactsize"></a>  CMFCRibbonCheckBox::GetCompactSize  
 Při přepisu získá compact velikost zaškrtávací políčko.  
  
```  
virtual CSize GetCompactSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDC`  
 Ukazatel `CDC` přidružené zaškrtávací políčko.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `CSize` objekt, který obsahuje compact velikost zaškrtávací políčko.  
  
### <a name="remarks"></a>Poznámky  
 Pokud přepsána nejsou, vrátí zprostředkující velikost zaškrtávací políčko.  
  
##  <a name="getintermediatesize"></a>  CMFCRibbonCheckBox::GetIntermediateSize  
 Získá zprostředkující velikost zaškrtávací políčko.  
  
```  
virtual CSize GetIntermediateSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDC`  
 Ukazatel `CDC` přidružené toto políčko.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CSize` objekt obsahující zprostředkující velikost zaškrtávací políčko.  
  
### <a name="remarks"></a>Poznámky  
 Pokud přepsána nejsou, vypočítá velikost zprostředkující jako výchozí velikost políčko ( `AFX_CHECK_BOX_DEFAULT_SIZE`) plus velikost textu, plus okraje.  
  
##  <a name="getregularsize"></a>  CMFCRibbonCheckBox::GetRegularSize  
 Získá regulární velikost zaškrtávací políčko.  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDC`  
 Ukazatel `CDC` objekt přidružený k toto políčko.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `CSize` objekt, který obsahuje regulární velikost zaškrtávací políčko.  
  
### <a name="remarks"></a>Poznámky  
 Pokud přepsána nejsou, vrátí zprostředkující velikost zaškrtávací políčko.  
  
##  <a name="isdrawtooltipimage"></a>  CMFCRibbonCheckBox::IsDrawTooltipImage  
 Určuje, zda je přiřazen popisek Obrázek zaškrtávací políčko.  
  
```  
virtual BOOL IsDrawTooltipImage() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `TRUE` Pokud není přiřazen popisek Obrázek políčka, nebo `FALSE` není-li.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ondraw"></a>  CMFCRibbonCheckBox::OnDraw  
 Voláno rámcem k vykreslení zaškrtávacího políčka pomocí kontextu zadaného zařízení.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDC`  
 Ukazatel `CDC` ve kterém se má nakreslit zaškrtávací políčko.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ondrawmenuimage"></a>  CMFCRibbonCheckBox::OnDrawMenuImage  
 Voláno rámcem kreslení obrázku nabídky zaškrtávacího políčka.  
  
```  
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `CDC*`  
 Ukazatel `CDC` přidružené zaškrtávací políčko.  
  
 [v] `CRect`  
 A `CRect` určující obdélníku, ve kterém k vykreslení bitovou kopii nabídky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `TRUE` Pokud vykreslení bitovou kopii, nebo `FALSE` není-li.  
  
### <a name="remarks"></a>Poznámky  
 Pokud přepsána nejsou, vrátí `FALSE`.  
  
##  <a name="ondrawonlist"></a>  CMFCRibbonCheckBox::OnDrawOnList  
 Voláno rámcem v seznamu příkazů nakreslit zaškrtávací políčko.  
  
```  
virtual void OnDrawOnList(
    CDC* pDC,  
    CString strText,  
    int nTextOffset,  
    CRect rect,  
    BOOL bIsSelected,  
    BOOL bHighlighted);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDC`  
 Ukazatel na zařízení kontextu, ve kterém k vykreslení zaškrtávací políčko.  
  
 [v] `strText`  
 Zobrazovaný text.  
  
 [v] `nTextOffset`  
 Vzdálenost v pixelech, z levé strany zobrazovaný text v rozevíracím seznamu.  
  
 [v] `rect`  
 Obdélník zobrazení zaškrtávacího políčka.  
  
 [v] `bIsSelected`  
 `TRUE` Pokud je políčko zaškrtnuto, nebo `FALSE` není-li.  
  
 [v] `bHighlighted`  
 `TRUE` Pokud políčko zvýrazní, nebo `FALSE` není-li.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setaccdata"></a>  CMFCRibbonCheckBox::SetACCData  
 Nastaví data usnadnění zaškrtávacího políčka.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Parametry  
 `pParent`  
 Nadřazené okno Zaškrtávací políčko.  
  
 `data`  
 Usnadnění data zaškrtávacího políčka.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení tato metoda nastaví data usnadnění zaškrtávacího políčka a vždy vrátí `TRUE`. Potlačí tuto metodu za účelem usnadnění, nastavte a vrátí hodnotu, která označuje úspěch nebo selhání.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonPanel – třída](../../mfc/reference/cmfcribbonpanel-class.md)
