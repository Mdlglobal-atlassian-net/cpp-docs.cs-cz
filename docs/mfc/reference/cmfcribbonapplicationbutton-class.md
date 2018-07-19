---
title: Cmfcribbonapplicationbutton – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: eddce134c3cda27e57a6a20d709bc4eab08d6e80
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37849012"
---
# <a name="cmfcribbonapplicationbutton-class"></a>Cmfcribbonapplicationbutton – třída
Implementuje speciální tlačítko umístěné v levém horním rohu okna aplikace. Po kliknutí na tlačítko otevře nabídku, která obvykle obsahuje běžné **souboru** příkazy jako **otevřít**, **Uložit**, a **ukončovací**.  
  
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
|`CMFCRibbonApplicationButton::CreateObject`|Rozhraní používá k vytvoření dynamické instance tohoto typu třídy.|  
|`CMFCRibbonApplicationButton::GetThisClass`|Používá k získání ukazatele na rámec [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený k typu třídy.|  
|[CMFCRibbonApplicationButton::SetImage](#setimage)|Přiřadí obrázku tlačítka pásu karet aplikace.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít různé metody v `CMFCRibbonApplicationButton` třídy. Příklad ukazuje, jak přiřadit obrázek pro tlačítko aplikace a jak nastavit jeho popis. Tento fragment kódu je součástí [nakreslit Client sample](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DrawClient#4](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_1.h)]  
[!code-cpp[NVC_MFC_DrawClient#5](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [Cmfcribbonbaseelement –](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [Cmfcribbonbutton –](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [Cmfcribbonapplicationbutton –](../../mfc/reference/cmfcribbonapplicationbutton-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxRibbonBar.h  
  
##  <a name="cmfcribbonapplicationbutton"></a>  CMFCRibbonApplicationButton::CMFCRibbonApplicationButton  
 Vytvoří a inicializuje [cmfcribbonapplicationbutton –](../../mfc/reference/cmfcribbonapplicationbutton-class.md) objektu.  
  
```  
CMFCRibbonApplicationButton();  
CMFCRibbonApplicationButton(UINT uiBmpResID);  
  CMFCRibbonApplicationButton(HBITMAP hBmp);
```  
  
### <a name="parameters"></a>Parametry  
 *uiBmpResID*  
 ID prostředku bitové kopie se zobrazí na tlačítku aplikace.  
  
 *hBmp*  
 Popisovač rastrový obrázek se zobrazí na tlačítku aplikace.  
  
### <a name="remarks"></a>Poznámky  
 Tlačítko aplikace pásu karet je speciální tlačítko, které se nachází v levém horním rohu okna aplikace. Když uživatel klikne na toto tlačítko, aplikace se otevře nabídka, která obvykle obsahuje běžné **souboru** příkazy, jako například **otevřít**, **Uložit**, a **ukončení**.  
  
##  <a name="setimage"></a>  CMFCRibbonApplicationButton::SetImage  
 Přiřadí obrázek pro tlačítko aplikace.  
  
```  
void SetImage(UINT uiBmpResID);  
void SetImage(HBITMAP hBmp);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *uiBmpResID*  
 ID prostředku bitové kopie se zobrazí na tlačítku aplikace.  
  
 [in] *hBmp*  
 Popisovač rastrový obrázek se zobrazí na tlačítku aplikace.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této metody můžete po vytvoření tlačítka přiřadit novou bitovou kopii na pásu karet tlačítko aplikace. Tlačítko aplikace se nachází v levém horním rohu okna aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton – třída](../../mfc/reference/cmfcribbonbutton-class.md)
