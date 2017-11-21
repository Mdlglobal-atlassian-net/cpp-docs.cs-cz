---
title: "Třída CMFCMenuButton | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "32"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 43772dff0e09b7160c1ec28a6c62d341c124892e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cmfcmenubutton-class"></a>CMFCMenuButton – třída
Tlačítko, které se zobrazí místní nabídka a sestavy v nabídce výběry uživatele.  
  
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
|[CMFCMenuButton::PreTranslateMessage](#pretranslatemessage)|Voláno rámcem přeložit okno zprávy před jejich odesláním. (Přepisuje `CMFCButton::PreTranslateMessage`.)|  
|[CMFCMenuButton::SizeToContent](#sizetocontent)|Změní velikost tlačítka podle jeho textových a obrázkových velikost.|  
  
### <a name="data-members"></a>Datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCMenuButton::m_bOSMenu](#m_bosmenu)|Určuje, jestli se zobrazit v rozbalovací nabídce Výchozí systému nebo použít [CContextMenuManager::TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu).|  
|[CMFCMenuButton::m_bRightArrow](#m_brightarrow)|Určuje, zda v místní nabídce se zobrazí pod nebo napravo od tlačítko.|  
|[CMFCMenuButton::m_bStayPressed](#m_bstaypressed)|Určuje, zda tlačítko nabídky změní stav po uživatel uvolní tlačítko.|  
|[CMFCMenuButton::m_hMenu](#m_hmenu)|Popisovač pro připojené nabídky systému Windows.|  
|[CMFCMenuButton::m_nMenuResult](#m_nmenuresult)|Identifikátor, který určuje, které položky vybrané uživatele z místní nabídky.|  
  
## <a name="remarks"></a>Poznámky  
 `CMFCMenuButton` Je třída odvozená z [CMFCButton – třída](../../mfc/reference/cmfcbutton-class.md) zase, který je, odvozen z [CButton třída](../../mfc/reference/cbutton-class.md). Proto můžete použít `CMFCMenuButton` ve vašem kódu stejným způsobem, jako byste použili `CButton`.  
  
 Při vytváření `CMFCMenuButton`, je nutné předat v popisovač do přidružených místní nabídky. Potom zavolejte funkci `CMFCMenuButton::SizeToContent`. `CMFCMenuButton::SizeToContent`kontroluje, zda je velikost tlačítko dostatečná zahrnout šipka odkazující na umístění, kde se zobrazí místní okno – konkrétně, pod nebo napravo od tlačítko.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nastavit popisovač v nabídce na tlačítko připojit, tlačítko podle jeho velikost textových a obrázkových změnit velikost a místní nabídky, který se zobrazí při rozhraní. Tento fragment kódu je součástí [nové ovládací prvky ukázka](../../visual-cpp-samples.md).  
  
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
 **Záhlaví:** afxmenubutton.h  
  
##  <a name="cmfcmenubutton"></a>CMFCMenuButton::CMFCMenuButton  
 Vytvoří nový [CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md) objektu.  
  
```  
CMFCMenuButton();
```  
  
##  <a name="m_bosmenu"></a>CMFCMenuButton::m_bOSMenu  
 Logická hodnota členské proměnné, která určuje, které místní nabídky zobrazí rozhraní.  
  
```  
BOOL m_bOSMenu;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud `m_bOSMenu` je `TRUE`, volá framework zděděnou `TrackPopupMenu` metoda pro tento objekt. Jinak, volá framework [CContextMenuManager::TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu).  
  
##  <a name="m_brightarrow"></a>CMFCMenuButton::m_bRightArrow  
 Logická hodnota členské proměnné, který určuje umístění v místní nabídce.  
  
```  
BOOL m_bRightArrow;  
```  
  
### <a name="remarks"></a>Poznámky  
 Po stisknutí tlačítka nabídky, aplikace se zobrazí místní nabídky. Rozhraní framework se zobrazí v rozbalovací nabídce v části tlačítko nebo pravé tlačítko. Tlačítko také obsahuje malé šipku, která určuje, kde se zobrazí v místní nabídce. Pokud `m_bRightArrow` je `TRUE`, rozhraní zobrazí v rozbalovací nabídce pravé tlačítko. V opačném případě zobrazí místní nabídky v části na tlačítko.  
  
##  <a name="m_bstaypressed"></a>CMFCMenuButton::m_bStayPressed  
 Logická hodnota členské proměnné, která určuje, zda se zobrazí tlačítko nabídky stisknutí, když uživatel provede výběr z místní nabídky.  
  
```  
BOOL m_bStayPressed;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud `m_bStayPressed` člen `FALSE`, nabídky ne stane stisknuté při použití klikne na tlačítko. V takovém případě rozhraní zobrazí pouze místní nabídky.  
  
 Pokud `m_bStayPressed` člen `TRUE`, se změní na stisknutí tlačítka nabídky, když uživatel klikne na tlačítko. Zůstane při stisknutí tlačítka až poté, co uživatel nezavře místní nabídky, provedení výběru nebo zrušení.  
  
##  <a name="m_hmenu"></a>CMFCMenuButton::m_hMenu  
 Popisovač připojené nabídky.  
  
```  
HMENU m_hMenu;  
```  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní zobrazuje v nabídce označených pomocí této proměnné člena, když uživatel klikne na tlačítko nabídky.  
  
##  <a name="m_nmenuresult"></a>CMFCMenuButton::m_nMenuResult  
 Celé číslo, které určuje, která položka uživatel vybere z místní nabídky.  
  
```  
int m_nMenuResult;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tato proměnná člena hodnotu nula. Pokud uživatel zruší nabídce bez provedení výběru nebo pokud dojde k chybě.  
  
##  <a name="pretranslatemessage"></a>CMFCMenuButton::PreTranslateMessage  
 Voláno rámcem přeložit okno zprávy před jejich odesláním.  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pMsg`  
 Odkazuje na [MSG](../../mfc/reference/msg-structure1.md) struktura, která obsahuje zprávu zpracovat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud zpráva byla přeložit a nesmí být odeslán; 0, pokud zpráva nebyla přeložit a by měla být odeslána.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="sizetocontent"></a>CMFCMenuButton::SizeToContent  
 Změní velikost tlačítka podle jeho velikost textu a velikost bitové kopie.  
  
```  
virtual CSize SizeToContent(BOOL bCalcOnly = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bCalcOnly`  
 Parametr typu Boolean, která určuje, zda tato metoda změní na tlačítko.  
  
### <a name="return-value"></a>Návratová hodnota  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md) objekt, který určuje novou velikost pro tlačítko.  
  
### <a name="remarks"></a>Poznámky  
 Pokud volání této funkce a `bCalcOnly` je `TRUE`, `SizeToContent` vypočítá novou velikost tlačítko.  
  
 Velikost nového tlačítka se počítá podle text tlačítka, image a šipku. Rozhraní framework přidává předdefinované okraje 10 pixelů pro vodorovné okraj a 5 pixelů pro vertikální okraj.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCButton – třída](../../mfc/reference/cmfcbutton-class.md)
