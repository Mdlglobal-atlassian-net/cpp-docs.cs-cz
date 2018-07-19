---
title: Cmfcribbonlabel – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel::CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel::SetACCData
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonLabel [MFC], CMFCRibbonLabel
- CMFCRibbonLabel [MFC], SetACCData
ms.assetid: 0346c891-83bf-4f20-b8a1-c84cf2aadced
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac06722b675af5e8ac8d4136cc2938ac772befc9
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848580"
---
# <a name="cmfcribbonlabel-class"></a>Cmfcribbonlabel – třída
Implementuje neklikatelné textový popisek pro pás karet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonLabel : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonLabel::CMFCRibbonLabel](#cmfcribbonlabel)|Vytvoří a inicializuje `CMFCRibbonLabel` objektu zadaného textovým řetězcem.|  
|`CMFCRibbonLabel::~CMFCRibbonLabel`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|`CMFCRibbonLabel::CreateObject`|Rozhraní používá k vytvoření dynamické instance tohoto typu třídy.|  
|`CMFCRibbonLabel::GetThisClass`|Používá k získání ukazatele na rámec [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený k typu třídy.|  
|[CMFCRibbonLabel::SetACCData](#setaccdata)|Určuje usnadnění dat pro aktuální popisek prvek pásu karet. (Přepíše [CMFCRibbonButton::SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata).)|  
  
### <a name="remarks"></a>Poznámky  
 Po vytvoření popisku pásu karet, přidejte ho do panelu voláním [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).  
  
 Nelze přidat popisek pásu karet na panelu nástrojů Rychlý přístup.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [Cmfcribbonbaseelement –](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [Cmfcribbonbutton –](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [Cmfcribbonlabel –](../../mfc/reference/cmfcribbonlabel-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxRibbonLabel.h  
  
##  <a name="cmfcribbonlabel"></a>  CMFCRibbonLabel::CMFCRibbonLabel  
 Vytvoří a inicializuje [cmfcribbonlabel –](../../mfc/reference/cmfcribbonlabel-class.md) objekt, který zobrazí zadaný text řetězce.  
  
```  
CMFCRibbonLabel(
    LPCTSTR lpszText,  
    BOOL bIsMultiLine = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *lpszText*  
 Text, který se zobrazí v popisku.  
  
 [in] *bIsMultiLine*  
 TRUE, pokud chcete určit, že popisek je Víceřádkový popisek; v opačném případě hodnota FALSE.  
  
##  <a name="setaccdata"></a>  CMFCRibbonLabel::SetACCData  
 Určuje usnadnění dat pro aktuální popisek prvek pásu karet.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pParent*  
 Představuje nadřazené okno aktuální popisku pásu karet.  
  
 [out] *dat*  
 Objekt typu `CAccessibilityData` , který je naplněný daty usnadnění aktuální popisku pásu karet.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud *data* parametr byl úspěšně naplněný daty usnadnění aktuální popisku pásu karet; v opačném případě hodnota FALSE.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton – třída](../../mfc/reference/cmfcribbonbutton-class.md)
