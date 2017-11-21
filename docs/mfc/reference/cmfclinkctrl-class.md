---
title: "Třída CMFCLinkCtrl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCLinkCtrl
- AFXLINKCTRL/CMFCLinkCtrl
- AFXLINKCTRL/CMFCLinkCtrl::SetURL
- AFXLINKCTRL/CMFCLinkCtrl::SetURLPrefix
- AFXLINKCTRL/CMFCLinkCtrl::SizeToContent
- AFXLINKCTRL/CMFCLinkCtrl::OnDrawFocusRect
dev_langs: C++
helpviewer_keywords:
- CMFCLinkCtrl [MFC], SetURL
- CMFCLinkCtrl [MFC], SetURLPrefix
- CMFCLinkCtrl [MFC], SizeToContent
- CMFCLinkCtrl [MFC], OnDrawFocusRect
ms.assetid: 80f3874d-7cc8-410e-9ff1-62a225f5034b
caps.latest.revision: "27"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1105e69599b1741d79c20e4f0ceb362cfc8c15eb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cmfclinkctrl-class"></a>CMFCLinkCtrl – třída
`CMFCLinkCtrl` Třída zobrazí tlačítko jako hypertextový odkaz a vyvolá na odkaz cíl při kliknutí na tlačítko.  
  
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
|[CMFCLinkCtrl::SizeToContent](#sizetocontent)|Změní velikost tlačítko tak, aby obsahovala text tlačítka nebo rastrového obrázku.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCLinkCtrl::OnDrawFocusRect](#ondrawfocusrect)|Voláno rámcem před vykreslením rámečku fokusu tlačítka.|  
  
## <a name="remarks"></a>Poznámky  
 Při kliknutí na tlačítko, který je odvozený od `CMFCLinkCtrl` třídu rozhraní předá adresu URL tlačítko jako parametr, který se `ShellExecute` metoda. Pak se `ShellExecute` metoda otevře cílové adresy URL.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nastavit velikost `CMFCLinkCtrl` objekt a jak nastavit adresu url a popis v `CMFCLinkCtrl` objektu. Tato ukázka je součástí [nové ovládací prvky ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#9](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#10](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
 [CMFCLinkCtrl](../../mfc/reference/cmfclinkctrl-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxlinkctrl.h  
  
##  <a name="ondrawfocusrect"></a>CMFCLinkCtrl::OnDrawFocusRect  
 Voláno rámcem před vykreslením rámečku fokusu tlačítka.  
  
```  
virtual void OnDrawFocusRect(
    CDC* pDC,  
    const CRect& rectClient);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Ukazatel na kontextu zařízení.  
  
 [v]`rectClient`  
 Obdélníku, která bounds ovládací prvek odkazu.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu, pokud chcete použít k vykreslení rámečku fokusu na tlačítko Vlastní kód.  
  
##  <a name="seturl"></a>CMFCLinkCtrl::SetURL  
 Zadaná adresa URL se zobrazí jako text tlačítka.  
  
```  
void SetURL(LPCTSTR lpszURL);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszURL`  
 Text tlačítka pro zobrazení.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="seturlprefix"></a>CMFCLinkCtrl::SetURLPrefix  
 Nastaví implicitní protokol (například "http:") adresy URL.  
  
```  
void SetURLPrefix(LPCTSTR lpszPrefix);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszPrefix`  
 Předponu adresy URL protokolu.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte, chcete-li nastavit předponu adresy URL. Předpona se nezobrazí na vzhled tlačítka, ale slouží ke procházet cílovou adresu URL.  
  
##  <a name="sizetocontent"></a>CMFCLinkCtrl::SizeToContent  
 Změní velikost tlačítko tak, aby obsahovala text tlačítka nebo rastrového obrázku.  
  
```  
virtual CSize SizeToContent(
    BOOL bVCenter=FALSE,  
    BOOL bHCenter=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bVCenter`  
 `TRUE`na střed tlačítko text a rastrový obrázek svisle mezi horní a dolní část řízení propojení; v opačném `FALSE`. Výchozí hodnota je `FALSE`.  
  
 [v]`bHCenter`  
 `TRUE`na střed tlačítko text a rastrový obrázek vodorovně mezi levé a pravé straně ovládacího prvku odkaz; v opačném `FALSE`. Výchozí hodnota je `FALSE`.  
  
### <a name="return-value"></a>Návratová hodnota  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md) objekt, který obsahuje nové velikosti ovládacího prvku odkazu.  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CLinkCtrl – třída](../../mfc/reference/clinkctrl-class.md)   
 [CMFCButton – třída](../../mfc/reference/cmfcbutton-class.md)
