---
title: "CDialogBar – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDialogBar
- AFXEXT/CDialogBar
- AFXEXT/CDialogBar::CDialogBar
- AFXEXT/CDialogBar::Create
dev_langs: C++
helpviewer_keywords:
- CDialogBar [MFC], CDialogBar
- CDialogBar [MFC], Create
ms.assetid: da2f7a30-970c-44e3-87f0-6094bd002cab
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4ee7507165c64f10def930f97c5f0ca2a62423dd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cdialogbar-class"></a>CDialogBar – třída
Poskytuje funkci Windows nemodální dialogového okna v ovládacím panelu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDialogBar : public CControlBar  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CDialogBar::CDialogBar](#cdialogbar)|Vytvoří `CDialogBar` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDialogBar::Create](#create)|Vytvoří dialogového pruhu Windows a připojí jej k `CDialogBar` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Panel dialogového okna se podobá dialogové okno, protože obsahuje standardní ovládací prvky systému Windows, které může uživatel kartě mezi. Jiné podobnosti je, že vytvořit šablony dialogového okna představují panel dialogového okna.  
  
 Vytvoření a použití dialogového pruhu je podobná vytváření a používání `CFormView` objektu. Nejprve pomocí [editoru dialogového okna](../../windows/dialog-editor.md) definovat šablony dialogového okna se stylem **ws_child –** a žádný jiný styl. Šablona nesmí obsahovat styl **ws_visible –**. V kódu aplikace, volat konstruktor k vytvoření `CDialogBar` objekt a potom volání **vytvořit** vytvořit okno panel dialogového okna a jeho k připojení `CDialogBar` objektu.  
  
 Další informace o `CDialogBar`, najdete v článku [dialogové pruhy](../../mfc/dialog-bars.md) a [Technická poznámka 31](../../mfc/tn031-control-bars.md), ovládací pruhy.  
  
> [!NOTE]
>  V aktuální verzi `CDialogBar` objektu nemůže být hostitelem ovládací prvky Windows Forms. Další informace o ovládacích prvcích Windows Forms v jazyce Visual C++ najdete v tématu [pomocí uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Ccontrolbar –](../../mfc/reference/ccontrolbar-class.md)  
  
 `CDialogBar`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxext.h  
  
##  <a name="cdialogbar"></a>CDialogBar::CDialogBar  
 Vytvoří `CDialogBar` objektu.  
  
```  
CDialogBar();
```  
  
##  <a name="create"></a>CDialogBar::Create  
 Načte prostředek – dialogové okno šablonu určenou položkou `lpszTemplateName` nebo `nIDTemplate`, vytvoří okno panel dialogového okna, nastaví její styl a přidruží ji s `CDialogBar` objektu.  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    LPCTSTR lpszTemplateName,  
    UINT nStyle,  
    UINT nID);

 
virtual BOOL Create(
    CWnd* pParentWnd,  
    UINT nIDTemplate,  
    UINT nStyle,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentWnd`  
 Ukazatel na nadřazený `CWnd` objektu.  
  
 `lpszTemplateName`  
 Ukazatel na název `CDialogBar` šablony prostředků – dialogové objektu.  
  
 `nStyle`  
 Styl panelu nástrojů. Styly dalších nástrojů, které jsou podporované jsou:  
  
- `CBRS_TOP`Ovládací prvek panelu je v horní části okna rámce.  
  
- `CBRS_BOTTOM`Ovládací prvek panelu je v dolní části okna rámce.  
  
- `CBRS_NOALIGN`Ovládací prvek panelu není změnit jejich umístění při změně velikosti nadřazeného objektu.  
  
- `CBRS_TOOLTIPS`Ovládací prvek panelu zobrazí popisy.  
  
- **Cbrs_size_dynamic –** ovládacích pruhů je dynamický.  
  
- **Cbrs_size_fixed –** ovládacích pruhů vyřešen.  
  
- **CBRS_FLOATING** je plovoucí ovládacích pruhů.  
  
- `CBRS_FLYBY`Stavový řádek zobrazí informace o tlačítko.  
  
- **CBRS_HIDE_INPLACE** není zobrazovat uživateli, ovládacích pruhů.  
  
 `nID`  
 ID ovládacího prvku panel dialogového okna.  
  
 `nIDTemplate`  
 ID prostředku `CDialogBar` dialogového šablony objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud zadáte `CBRS_TOP` nebo `CBRS_BOTTOM` zarovnání styl, šířka panel dialogového okna je, že rámce okna a jeho výšku je u prostředku zadaného parametrem `nIDTemplate`. Pokud zadáte `CBRS_LEFT` nebo `CBRS_RIGHT` zarovnání styl, výška panel dialogového okna je, že rámce okna a jeho šířka je, že z prostředku zadaného parametrem `nIDTemplate`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCMessageMaps#13](../../mfc/reference/codesnippet/cpp/cdialogbar-class_1.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC CTRLBARS](../../visual-cpp-samples.md)   
 [Ccontrolbar – třída](../../mfc/reference/ccontrolbar-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy CFormView – třída](../../mfc/reference/cformview-class.md)   
 [Ccontrolbar – třída](../../mfc/reference/ccontrolbar-class.md)
