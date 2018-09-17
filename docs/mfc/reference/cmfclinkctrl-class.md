---
title: Cmfclinkctrl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCLinkCtrl
- AFXLINKCTRL/CMFCLinkCtrl
- AFXLINKCTRL/CMFCLinkCtrl::SetURL
- AFXLINKCTRL/CMFCLinkCtrl::SetURLPrefix
- AFXLINKCTRL/CMFCLinkCtrl::SizeToContent
- AFXLINKCTRL/CMFCLinkCtrl::OnDrawFocusRect
dev_langs:
- C++
helpviewer_keywords:
- CMFCLinkCtrl [MFC], SetURL
- CMFCLinkCtrl [MFC], SetURLPrefix
- CMFCLinkCtrl [MFC], SizeToContent
- CMFCLinkCtrl [MFC], OnDrawFocusRect
ms.assetid: 80f3874d-7cc8-410e-9ff1-62a225f5034b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a6bed16f338c5ee3333529613189fe03ad7e3ec3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709550"
---
# <a name="cmfclinkctrl-class"></a>Cmfclinkctrl – třída
`CMFCLinkCtrl` Třídy zobrazí tlačítko jako hypertextový odkaz a po kliknutí na tlačítko vyvolá cíl odkazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCLinkCtrl : public CMFCButton  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCLinkCtrl::SetURL](#seturl)|Zadaná adresa URL se zobrazí jako text tlačítka.|  
|[CMFCLinkCtrl::SetURLPrefix](#seturlprefix)|Nastaví implicitní protokol (například "http:") adresy URL.|  
|[CMFCLinkCtrl::SizeToContent](#sizetocontent)|Změní velikost tlačítka tak, aby obsahovala text tlačítka nebo rastrový obrázek.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCLinkCtrl::OnDrawFocusRect](#ondrawfocusrect)|Volá se rozhraním před vykreslením obdélník tlačítka.|  
  
## <a name="remarks"></a>Poznámky  
 Po kliknutí na tlačítko, který je odvozen z `CMFCLinkCtrl` třídy, rozhraní předá adresu URL na tlačítko jako parametr, který se `ShellExecute` metody. Pak bude `ShellExecute` metoda otevře cílové adresy URL.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nastavit velikost `CMFCLinkCtrl` objekt a jak nastavit adresu url a popis ve `CMFCLinkCtrl` objektu. V tomto příkladu je součástí [nové ovládací prvky ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#9](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#10](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [Cmfcbutton –](../../mfc/reference/cmfcbutton-class.md)  
  
 [Cmfclinkctrl –](../../mfc/reference/cmfclinkctrl-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxlinkctrl.h  
  
##  <a name="ondrawfocusrect"></a>  CMFCLinkCtrl::OnDrawFocusRect  
 Volá se rozhraním před vykreslením obdélník tlačítka.  
  
```  
virtual void OnDrawFocusRect(
    CDC* pDC,  
    const CRect& rectClient);
```  
  
### <a name="parameters"></a>Parametry  
*primární řadič domény*<br/>
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
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [Clinkctrl – třída](../../mfc/reference/clinkctrl-class.md)   
 [CMFCButton – třída](../../mfc/reference/cmfcbutton-class.md)
