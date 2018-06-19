---
title: Třída CMFCRibbonApplicationButton | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton::CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton::SetImage
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonApplicationButton [MFC], CMFCRibbonApplicationButton
- CMFCRibbonApplicationButton [MFC], SetImage
ms.assetid: beb81757-fabd-4641-9130-876ba8505b78
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3b2b2e8adccd77862b445d7e91df0b808967a31d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369161"
---
# <a name="cmfcribbonapplicationbutton-class"></a>CMFCRibbonApplicationButton – třída
Implementuje speciální tlačítko nachází v levém horním rohu okna aplikace. Po kliknutí na tlačítko otevření nabídky, která obvykle obsahuje běžné **soubor** příkazy jako **otevřete**, **Uložit**, a **ukončení**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonApplicationButton : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonApplicationButton::CMFCRibbonApplicationButton](#cmfcribbonapplicationbutton)|Vytvoří a inicializuje `CMFCRibbonApplicationButton` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|`CMFCRibbonApplicationButton::CreateObject`|Rozhraní používá k vytvoření dynamických instance tohoto typu třídy.|  
|`CMFCRibbonApplicationButton::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený tento typ třídy.|  
|[CMFCRibbonApplicationButton::SetImage](#setimage)|Přiřadí bitovou kopii na pásu karet tlačítko aplikace.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí různých metod v nástroji `CMFCRibbonApplicationButton` třídy. Příklad ukazuje, jak přiřadit obrázek pro tlačítko aplikace a jak nastavit její popis. Tento fragment kódu je součástí [Ukázka kreslení klienta](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DrawClient#4](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_1.h)]  
[!code-cpp[NVC_MFC_DrawClient#5](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxRibbonBar.h  
  
##  <a name="cmfcribbonapplicationbutton"></a>  CMFCRibbonApplicationButton::CMFCRibbonApplicationButton  
 Vytvoří a inicializuje [CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md) objektu.  
  
```  
CMFCRibbonApplicationButton();  
CMFCRibbonApplicationButton(UINT uiBmpResID);  
  CMFCRibbonApplicationButton(HBITMAP hBmp);
```  
  
### <a name="parameters"></a>Parametry  
 `uiBmpResID`  
 ID prostředku bitové kopie pro zobrazení na tlačítko aplikace.  
  
 `hBmp`  
 Popisovač pro rastrový obrázek pro zobrazení na tlačítko aplikace.  
  
### <a name="remarks"></a>Poznámky  
 Na pásu karet tlačítko aplikace je speciální tlačítko, které se nachází v levém horním rohu okna aplikace. Když uživatel klikne na toto tlačítko, aplikace otevření nabídky, která obvykle obsahuje běžné **soubor** příkazy, jako **otevřete**, **Uložit**, a **ukončovací**.  
  
##  <a name="setimage"></a>  CMFCRibbonApplicationButton::SetImage  
 Přiřadí obrázek pro tlačítko aplikace.  
  
```  
void SetImage(UINT uiBmpResID);  
void SetImage(HBITMAP hBmp);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `uiBmpResID`  
 ID prostředku bitové kopie pro zobrazení na tlačítko aplikace.  
  
 [v] `hBmp`  
 Popisovač pro rastrový obrázek pro zobrazení na tlačítko aplikace.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k přiřazení novou bitovou kopii na pásu karet tlačítko aplikace po vytvoření na tlačítko. Tlačítko aplikace se nachází v levém horním rohu okna aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton – třída](../../mfc/reference/cmfcribbonbutton-class.md)
