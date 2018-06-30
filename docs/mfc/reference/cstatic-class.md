---
title: Třída CStatic | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CStatic
- AFXWIN/CStatic
- AFXWIN/CStatic::CStatic
- AFXWIN/CStatic::Create
- AFXWIN/CStatic::DrawItem
- AFXWIN/CStatic::GetBitmap
- AFXWIN/CStatic::GetCursor
- AFXWIN/CStatic::GetEnhMetaFile
- AFXWIN/CStatic::GetIcon
- AFXWIN/CStatic::SetBitmap
- AFXWIN/CStatic::SetCursor
- AFXWIN/CStatic::SetEnhMetaFile
- AFXWIN/CStatic::SetIcon
dev_langs:
- C++
helpviewer_keywords:
- CStatic [MFC], CStatic
- CStatic [MFC], Create
- CStatic [MFC], DrawItem
- CStatic [MFC], GetBitmap
- CStatic [MFC], GetCursor
- CStatic [MFC], GetEnhMetaFile
- CStatic [MFC], GetIcon
- CStatic [MFC], SetBitmap
- CStatic [MFC], SetCursor
- CStatic [MFC], SetEnhMetaFile
- CStatic [MFC], SetIcon
ms.assetid: e7c94cd9-5ebd-428a-aa30-b3e51f8efb95
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4bc7a236b8a1dfc8877bc094641d26163f735a3e
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122764"
---
# <a name="cstatic-class"></a>CStatic – třída
Poskytuje funkci statické ovládacího prvku Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CStatic : public CWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CStatic::CStatic](#cstatic)|Vytvoří `CStatic` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CStatic::Create](#create)|Statické ovládací prvek Windows vytvoří a připojí jej k `CStatic` objektu.|  
|[CStatic::DrawItem](#drawitem)|Přepsání pro kreslení statické ovládací prvek vykreslované uživatelem.|  
|[CStatic::GetBitmap](#getbitmap)|Načte popisovač rastrového obrázku dříve nastavené s [SetBitmap](#setbitmap).|  
|[CStatic::GetCursor](#getcursor)|Načte popisovač bitovou kopii kurzoru dříve nastavené s [SetCursor](#setcursor).|  
|[CStatic::GetEnhMetaFile](#getenhmetafile)|Načte popisovač EMF dříve nastavené s [SetEnhMetaFile](#setenhmetafile).|  
|[CStatic::GetIcon](#geticon)|Načte popisovač ikonu dříve nastavené s [SetIcon](#seticon).|  
|[CStatic::SetBitmap](#setbitmap)|Určuje rastrový obrázek zobrazený v ovládacím prvku statické.|  
|[CStatic::SetCursor](#setcursor)|Určuje obrázek kurzoru zobrazený v ovládacím prvku statické.|  
|[CStatic::SetEnhMetaFile](#setenhmetafile)|Určuje EMF zobrazený v ovládacím prvku statické.|  
|[CStatic::SetIcon](#seticon)|Určuje ikonu, která se zobrazí v ovládacím prvku statické.|  
  
## <a name="remarks"></a>Poznámky  
 Statické ovládací prvek zobrazí textový řetězec, pole, obdélníku, ikona, kurzoru, rastrového obrázku nebo EMF. Slouží k označení, pole nebo oddělení další ovládací prvky. Statické ovládací prvek obvykle nemá žádný vstup a poskytuje žádný výstup; Pokud je vytvořen s ss_notify – styl, ho však oznámit nadřazené kliknutí myší.  
  
 Vytvoření ovládacího prvku statické ve dvou krocích. Nejprve volat konstruktor k vytvoření `CStatic` objekt a potom volání [vytvořit](#create) členské funkce k vytvoření statických ovládacího prvku a připojte ji k `CStatic` objektu.  
  
 Pokud vytvoříte `CStatic` objekt v rámci dialogového okna (prostřednictvím prostředku dialogového okna), `CStatic` objekt zničen automaticky při zavření dialogu.  
  
 Pokud vytvoříte `CStatic` objektu v okně a také můžete potřebovat jeho odstranění. A `CStatic` objekt vytvořený v zásobníku v rámci časového období automaticky zničena. Pokud vytvoříte `CStatic` objektu v haldě pomocí **nové** funkce, musí volat **odstranit** na objekt, který má zničte, jakmile jste hotovi s ním.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CStatic`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="create"></a>  CStatic::Create  
 Statické ovládací prvek Windows vytvoří a připojí jej k `CStatic` objektu.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszText,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID = 0xffff);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszText*  
 Určuje text, který má umístit v ovládacím prvku. Pokud hodnotu NULL, se nebude zobrazovat žádný text.  
  
 *dwStyle*  
 Určuje styl okna statické ovládací prvek. Použít libovolnou kombinaci [styly ovládacího prvku statické](../../mfc/reference/styles-used-by-mfc.md#static-styles) do ovládacího prvku.  
  
 *Rect –*  
 Určuje umístění a velikost statické ovládacího prvku. Může být buď `RECT` struktura nebo `CRect` objektu.  
  
 *pParentWnd*  
 Určuje, `CStatic` nadřazené okno, obvykle `CDialog` objektu. Nesmí být NULL.  
  
 *nID*  
 Určuje ID statické ovládací prvek ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Vytvořit `CStatic` objektu ve dvou krocích. Nejprve volat konstruktor `CStatic`a pak zavolají `Create`, který vytvoří statickou ovládacího prvku Windows a připojí jej k `CStatic` objektu.  
  
 Použít následující [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) do ovládacího prvku statické:  
  
- Ws_child – vždy  
  
- Ws_visible – obvykle  
  
- Ws_disabled – zřídka  
  
 Pokud se chystáte zobrazit rastrového obrázku, kurzoru, ikony nebo metafile v ovládacím prvku statické, budete muset použít jednu z následujících [statické styly](../../mfc/reference/styles-used-by-mfc.md#static-styles):  
  
- Ss_bitmap – tento styl použít pro rastrové obrázky.  
  
- Ss_icon – tento styl použít pro ikony a kurzory.  
  
- Ss_enhmetafile – tento styl použít pro rozšířené metasoubory.  
  
 Kurzory, rastrové obrázky nebo ikony můžete také použít styl následující:  
  
- Ss_centerimage – použití na střed bitovou kopii v ovládacím prvku statické.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CStatic#1](../../mfc/reference/codesnippet/cpp/cstatic-class_1.cpp)]  
  
##  <a name="cstatic"></a>  CStatic::CStatic  
 Vytvoří `CStatic` objektu.  
  
```  
CStatic();
```  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CStatic#2](../../mfc/reference/codesnippet/cpp/cstatic-class_2.cpp)]  
  
##  <a name="drawitem"></a>  CStatic::DrawItem  
 Voláno rámcem k vykreslení statické ovládací prvek vykreslované uživatelem.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 *lpDrawItemStruct*  
 Ukazatel [drawitemstruct –](../../mfc/reference/drawitemstruct-structure.md) struktura. Struktura obsahuje informace o položce, které se mají vykreslovat a typ kreslení vyžaduje.  
  
### <a name="remarks"></a>Poznámky  
 Přepsat tuto funkci implementovat kreslení pro vykreslovaných vlastníkem `CStatic` objektu (styl ss_ownerdraw – ovládací prvek má).  
  
##  <a name="getbitmap"></a>  CStatic::GetBitmap  
 Získá popisovač rastrového obrázku, dříve nastavené s [SetBitmap](#setbitmap), která je přidružená `CStatic`.  
  
```  
HBITMAP GetBitmap() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro aktuální rastrový obrázek nebo hodnota NULL, pokud byla nastavena žádná rastrového obrázku.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]  
  
##  <a name="getcursor"></a>  CStatic::GetCursor  
 Získá popisovač kurzor, dříve nastavené s [SetCursor](#setcursor), která je přidružená `CStatic`.  
  
```  
HCURSOR GetCursor();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro aktuální kurzor, nebo hodnota NULL, pokud byl nastaven žádný ukazatel.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]  
  
##  <a name="getenhmetafile"></a>  CStatic::GetEnhMetaFile  
 Získá popisovač EMF dříve nastavené s [SetEnhMetafile](#setenhmetafile), která je přidružená `CStatic`.  
  
```  
HENHMETAFILE GetEnhMetaFile() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro aktuální EMF nebo hodnota NULL, pokud byla nastavena žádná EMF.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]  
  
##  <a name="geticon"></a>  CStatic::GetIcon  
 Získá popisovač ikonu dříve nastavené s [SetIcon](#seticon), která je přidružená `CStatic`.  
  
```  
HICON GetIcon() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro aktuální ikony nebo hodnota NULL, pokud byla nastavena žádná ikona.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]  
  
##  <a name="setbitmap"></a>  CStatic::SetBitmap  
 Přidruží nové bitové mapy ovládacího prvku statické.  
  
```  
HBITMAP SetBitmap(HBITMAP hBitmap);
```  
  
### <a name="parameters"></a>Parametry  
 *hBitmap*  
 Popisovač rastrového obrázku, které se mají vykreslovat v ovládacím prvku statické.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač rastrového obrázku, který byl dříve přidružen statické ovládací prvek, nebo hodnota NULL, pokud žádné rastrového obrázku je spojené s statické ovládací prvek.  
  
### <a name="remarks"></a>Poznámky  
 Bitmapy se automaticky přidělit v ovládacím prvku statické. Ve výchozím nastavení bude se vykresluje v levém horním rohu a statické ovládací prvek bude nastavena velikost na velikost bitové mapy.  
  
 Můžete použít různé okno a styly statické ovládacího prvku, včetně těchto:  
  
-   Tento styl ss_bitmap – vždy použít pro rastrové obrázky.  
  
-   Ss_centerimage – použití na střed bitovou kopii v ovládacím prvku statické. Pokud bitovou kopii je větší než statické ovládací prvek, bude oříznut. Pokud je menší než statické ovládací prvek, bude prázdná místo kolem obrázku vyplněno barvou pixelů v levém horním rohu bitové mapy.  
  
-   Poskytuje třídy MFC `CBitmap`, který můžete použít, když máte více s rastrový obrázek než stačí zavolat Win32 funkci `LoadBitmap`. `CBitmap`, která obsahuje jednoho druhu objektu GDI se často používá ve spolupráci s `CStatic`, který je `CWnd` třídu, která se používá pro zobrazení grafického objektu jako statické ovládací prvek.  
  
 `CImage` je třída ATL a MFC, která vám umožní více snadno pracovat s bitovými mapami zařízení nezávislé (DIB). Další informace najdete v tématu [CImage – třída](../../atl-mfc-shared/reference/cimage-class.md).  
  
-   Typická využití je umožnit `CStatic::SetBitmap` GDI objekt, který je vrácen provozovatelem HBITMAP `CBitmap` nebo `CImage` objektu. Kód k tomu se podobá následující řádek.  
  
```  
MyStaticControl.SetBitmap(HBITMAP(MyBitmap));
```  
Následující příklad vytvoří dvě `CStatic` objekty v haldě. Potom načte s rastrový obrázek systém pomocí `CBitmap::LoadOEMBitmap` a dalších ze souboru pomocí `CImage::Load`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]  
  
##  <a name="setcursor"></a>  CStatic::SetCursor  
 Přidruží novou bitovou kopii kurzoru statické ovládací prvek.  
  
```  
HCURSOR SetCursor(HCURSOR hCursor);
```  
  
### <a name="parameters"></a>Parametry  
 *hCursor*  
 Obslužná rutina kurzoru, které se mají vykreslovat v ovládacím prvku statické.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač kurzor dřív přidružené ke statické ovládací prvek, nebo hodnota NULL, pokud žádný ukazatel je spojené s statické ovládací prvek.  
  
### <a name="remarks"></a>Poznámky  
 Kurzor se automaticky přidělit v ovládacím prvku statické. Ve výchozím nastavení bude se vykresluje v levém horním rohu a statické ovládací prvek bude nastavena velikost na velikost kurzor.  
  
 Můžete použít různé okno a styly statické ovládacího prvku, včetně následujících:  
  
- Tento styl ss_icon – vždy použít pro ikony a kurzory.  
  
- Ss_centerimage – použití na střed v ovládacím prvku statické. Pokud bitovou kopii je větší než statické ovládací prvek, bude oříznut. Pokud je menší než statické ovládací prvek, prázdné místo kolem obrázku bude vyplněn barvu pozadí ovládacího prvku statické.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]  
  
##  <a name="setenhmetafile"></a>  CStatic::SetEnhMetaFile  
 Přidruží novou bitovou kopii EMF statické ovládací prvek.  
  
```  
HENHMETAFILE SetEnhMetaFile(HENHMETAFILE hMetaFile);
```  
  
### <a name="parameters"></a>Parametry  
 *hMetaFile*  
 Popisovač EMF, které se mají vykreslovat v ovládacím prvku statické.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač EMF dřív přidružené ke statické ovládací prvek, nebo hodnota NULL, pokud žádné EMF byl přidružen statické ovládací prvek.  
  
### <a name="remarks"></a>Poznámky  
 Rozšířené metafile se automaticky přidělit v ovládacím prvku statické. Rozšířené metafile přizpůsobí velikost statické ovládací prvek.  
  
 Můžete použít různé okno a styly statické ovládacího prvku, včetně následujících:  
  
- Ss_enhmetafile – pomocí této styl vždy pro rozšířené metasoubory.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]  
  
##  <a name="seticon"></a>  CStatic::SetIcon  
 Přidruží novou bitovou kopii ikonu statické ovládací prvek.  
  
```  
HICON SetIcon(HICON hIcon);
```  
  
### <a name="parameters"></a>Parametry  
 *hIcon*  
 Obslužná rutina ikony, které se mají vykreslovat v ovládacím prvku statické.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač ikonu dřív přidružené ke statické ovládací prvek, nebo hodnota NULL, pokud žádná ikona byl přidružen statické ovládací prvek.  
  
### <a name="remarks"></a>Poznámky  
 Ikona se automaticky přidělit v ovládacím prvku statické. Ve výchozím nastavení bude se vykresluje v levém horním rohu a statické ovládací prvek bude nastavena velikost na velikost ikony.  
  
 Můžete použít různé okno a styly statické ovládacího prvku, včetně následujících:  
  
- Tento styl ss_icon – vždy použít pro ikony a kurzory.  
  
- Ss_centerimage – použití na střed v ovládacím prvku statické. Pokud bitovou kopii je větší než statické ovládací prvek, bude oříznut. Pokud je menší než statické ovládací prvek, prázdné místo kolem obrázku bude vyplněn barvu pozadí ovládacího prvku statické.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [CButton – třída](../../mfc/reference/cbutton-class.md)   
 [CComboBox – třída](../../mfc/reference/ccombobox-class.md)   
 [CEdit – třída](../../mfc/reference/cedit-class.md)   
 [Clistbox – třída](../../mfc/reference/clistbox-class.md)   
 [CScrollBar – třída](../../mfc/reference/cscrollbar-class.md)   
 [CDialog – třída](../../mfc/reference/cdialog-class.md)
