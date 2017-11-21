---
title: "Třída CMFCImageEditorDialog | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog::CMFCImageEditorDialog
dev_langs: C++
helpviewer_keywords: CMFCImageEditorDialog [MFC], CMFCImageEditorDialog
ms.assetid: 6a7d08f3-1ec2-4062-9b79-a0c2776b58d1
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0318c8290e58fc479d5c427b60d246d81b62585c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cmfcimageeditordialog-class"></a>CMFCImageEditorDialog – třída
`CMFCImageEditorDialog` Třída podporuje dialogové okno editor bitové kopie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCImageEditorDialog : public CDialogEx  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCImageEditorDialog::CMFCImageEditorDialog](#cmfcimageeditordialog)|Vytvoří `CMFCImageEditorDialog` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 `CMFCImageEditorDialog` Třída poskytuje dialogové okno, které obsahuje:  
  
-   Oblast obrázku, který používáte k úpravě jednotlivých pixelů bitovou kopii.  
  
-   Kreslení nástroje k úpravě pixelů v oblasti obrázku.  
  
-   Palety barev zadat barvu, která je používána nástrojů pro kreslení.  
  
-   Náhled oblasti, která zobrazuje účinku úpravy.  
  
 Následující obrázek znázorňuje dialogové okno editoru bitové kopie.  
  
 ![Dialogové okno CMFCImageEditorDialog](../../mfc/reference/media/imageedit.png "imageedit")  
  
 Jedním ze způsobů použití `CMFCImageEditorDialog` objektu je předejte ji `CBitmap` bitové kopie k provádění úprav. Nevytvářejte velký obrázek, protože bitovou kopii úpravy oblasti má omezenou velikost a velikost logických pixelů je upravit podle oblasti. Volání `DoModal` metoda zahájíte modální dialogové okno.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afximageeditordialog.h  
  
##  <a name="cmfcimageeditordialog"></a>CMFCImageEditorDialog::CMFCImageEditorDialog  
 Vytvoří `CMFCImageEditorDialog` objektu.  
  
```  
CMFCImageEditorDialog(
    CBitmap* pBitmap,  
    CWnd* pParent=NULL,  
    int nBitsPixel=-1);
```  
  
### <a name="parameters"></a>Parametry  
 `pBitmap`  
 Ukazatel na bitovou kopii.  
  
 `pParent`  
 Ukazatel do nadřazeného okna aktuální dialogového okna editoru bitové kopie.  
  
 `nBitsPixel`  
 Počet bitů používá k reprezentování barvu jednoho pixelů, která je také označována jako hloubka barev.  Pokud `nBitsPixel` parametr -1, hloubky barev je odvozený od bitovou kopii určeného `pBitmap` parametr. Výchozí hodnota je -1.  
  
### <a name="return-value"></a>Návratová hodnota  
 K úpravě bitovou kopii, předejte ukazatel bitovou kopii na `CMFCImageEditorDialog` konstruktor. Potom zavolejte `DoModal` metoda otevřete modální dialogové okno. Když `DoModal` metoda vrací výsledek, obsahuje bitovou mapu novou bitovou kopii.  
  
### <a name="remarks"></a>Poznámky  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit objekt `CMFCImageEditorDialog` třídy. Tato ukázka je součástí [nové ovládací prvky ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#8](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_1.cpp)]  
[!code-cpp[NVC_MFC_NewControls#40](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_2.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar – třída](../../mfc/reference/cmfctoolbar-class.md)
