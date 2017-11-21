---
title: "Třída COleConvertDialog | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleConvertDialog
- AFXODLGS/COleConvertDialog
- AFXODLGS/COleConvertDialog::COleConvertDialog
- AFXODLGS/COleConvertDialog::DoConvert
- AFXODLGS/COleConvertDialog::DoModal
- AFXODLGS/COleConvertDialog::GetClassID
- AFXODLGS/COleConvertDialog::GetDrawAspect
- AFXODLGS/COleConvertDialog::GetIconicMetafile
- AFXODLGS/COleConvertDialog::GetSelectionType
- AFXODLGS/COleConvertDialog::m_cv
dev_langs: C++
helpviewer_keywords:
- COleConvertDialog [MFC], COleConvertDialog
- COleConvertDialog [MFC], DoConvert
- COleConvertDialog [MFC], DoModal
- COleConvertDialog [MFC], GetClassID
- COleConvertDialog [MFC], GetDrawAspect
- COleConvertDialog [MFC], GetIconicMetafile
- COleConvertDialog [MFC], GetSelectionType
- COleConvertDialog [MFC], m_cv
ms.assetid: a7c57714-31e8-4b78-834d-8ddd1b856a1c
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 72de3b05dad581b2b0f4f3eec19e15d211bba601
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="coleconvertdialog-class"></a>COleConvertDialog – třída
Další informace najdete v tématu [OLEUICONVERT](http://msdn.microsoft.com/library/windows/desktop/ms686657) struktura ve Windows SDK.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleConvertDialog : public COleDialog  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[COleConvertDialog::COleConvertDialog](#coleconvertdialog)|Vytvoří `COleConvertDialog` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleConvertDialog::DoConvert](#doconvert)|Provede zadané v dialogovém okně Převod.|  
|[COleConvertDialog::DoModal](#domodal)|Zobrazí dialogové okno OLE změnu položky.|  
|[COleConvertDialog::GetClassID](#getclassid)|Získá **CLSID** přidružené k vybrané položce.|  
|[COleConvertDialog::GetDrawAspect](#getdrawaspect)|Určuje, jestli se k vykreslení položky jako ikona.|  
|[COleConvertDialog::GetIconicMetafile](#geticonicmetafile)|Získá popisovač pro metafile přidružené ikony formu této položky.|  
|[COleConvertDialog::GetSelectionType](#getselectiontype)|Získá typ výběru vybrali.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[COleConvertDialog::m_cv](#m_cv)|Struktura, která řídí chování dialogového okna.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Kód aplikace generované v Průvodci kontejneru používá tuto třídu.  
  
 Další informace o dialogových oknech OLE specifické, najdete v článku [dialogová okna v prostředí OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleConvertDialog`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxodlgs.h  
  
##  <a name="coleconvertdialog"></a>COleConvertDialog::COleConvertDialog  
 Vytvoří pouze `COleConvertDialog` objektu.  
  
```  
explicit COleConvertDialog (
    COleClientItem* pItem,
    DWORD dwFlags = CF_SELECTCONVERTTO,
    CLSID* pClassID = NULL,
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pItem`  
 Odkazuje na položku, kterou chcete převést nebo aktivovat.  
  
 `dwFlags`  
 Vytvoření příznak, který obsahuje libovolný počet následující hodnoty spojovat pomocí bitové hodnotě – operátor or:  
  
- **CF_SELECTCONVERTTO** Určuje, že přepínač převést na vybere původně při volání dialogové okno. Toto nastavení je výchozí.  
  
- **CF_SELECTACTIVATEAS** Určuje, že přepínač aktivovat jako vybere původně při volání dialogové okno.  
  
- **CF_SETCONVERTDEFAULT** Určuje, že třída jejichž **CLSID** je zadána **clsidConvertDefault** členem `m_cv` struktura bude sloužit jako výchozí Výběr v poli seznam tříd, pokud je vybrána přepínač převést na.  
  
- **CF_SETACTIVATEDEFAULT** Určuje, že třída jejichž **CLSID** je zadána **clsidActivateDefault** členem `m_cv` struktura bude sloužit jako výchozí Výběr v seznamu Třída při aktivaci jako přepínač vybrán.  
  
- **CF_SHOWHELPBUTTON** Určuje, že na tlačítko Nápověda se zobrazí, když je volána dialogové okno.  
  
 `pClassID`  
 Body CLSID položku, kterou chcete převést nebo aktivovat. Pokud **NULL**, **CLSID** přidružené `pItem` se použije.  
  
 `pParentWnd`  
 Odkazuje na objekt okno nadřazené nebo vlastníka (typu `CWnd`), ke které patří objektu dialogového okna. Pokud je **NULL**, nadřazeného okna dialogového okna nastavena na hlavní okno aplikace.  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li zobrazit dialogové okno, zavolejte [DoModal](#domodal) funkce.  
  
 Další informace najdete v tématu [klíč CLSID](http://msdn.microsoft.com/library/windows/desktop/ms691424) a [OLEUICONVERT](http://msdn.microsoft.com/library/windows/desktop/ms686657) struktury.  
  
##  <a name="doconvert"></a>COleConvertDialog::DoConvert  
 Volání této funkce po vrácení úspěšně z [DoModal](#domodal), buď převést nebo aktivovat objekt typu [COleClientItem](../../mfc/reference/coleclientitem-class.md).  
  
```  
BOOL DoConvert(COleClientItem* pItem);
```  
  
### <a name="parameters"></a>Parametry  
 `pItem`  
 Odkazuje na položku, kterou chcete převést nebo aktivovat. Nemůže být **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Převést nebo aktivovat podle informace uživatelem v dialogovém okně Převést vybrané položky.  
  
##  <a name="domodal"></a>COleConvertDialog::DoModal  
 Volání této funkce můžete zobrazit dialogové okno Převést OLE.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Stav dokončení pro dialogové okno. Jedna z následujících hodnot:  
  
- **IDOK** Pokud úspěšně zobrazí dialogové okno.  
  
- **IDCANCEL** Pokud uživatel zrušil dialogové okno.  
  
- **IDABORT** Pokud došlo k chybě. Pokud **IDABORT** se volání vrátí, [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) – členská funkce získat další informace o typu Chyba, že došlo k chybě. Seznam možné chyby, najdete v článku [OleUIConvert](http://msdn.microsoft.com/library/windows/desktop/ms680694) funkce ve Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete k chybě při inicializaci různých dialogové okno Ovládací prvky nastavením členy [m_cv](#m_cv) struktura, bude třeba provést před voláním `DoModal`, ale po objektu dialogového okna je vytvořený.  
  
 Pokud `DoModal` vrátí **IDOK**, můžete volat jiné členské funkce načíst nastavení nebo informace, které se vstup uživatelem na dialogové okno.  
  
##  <a name="getclassid"></a>COleConvertDialog::GetClassID  
 Volání této funkce můžete získat **CLSID** přidružené k položce vyberte v dialogovém okně Převést uživatele.  
  
```  
REFCLSID GetClassID() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 **CLSID** přidružené k položce, který byl vybrán v dialogovém okně Převést.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce až po volání [DoModal](#domodal) vrátí **IDOK**.  
  
 Další informace najdete v tématu [klíč CLSID](http://msdn.microsoft.com/library/windows/desktop/ms691424) ve Windows SDK.  
  
##  <a name="getdrawaspect"></a>COleConvertDialog::GetDrawAspect  
 Volání této funkce určete, zda se uživatel rozhodl zobrazit vybranou položku jako ikonu.  
  
```  
DVASPECT GetDrawAspect() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Metoda potřebné k vykreslení objektu.  
  
- `DVASPECT_CONTENT`Vrátí, pokud není zaškrtnuto zaškrtávací políčko Zobrazit jako ikonu.  
  
- `DVASPECT_ICON`Vrátí, pokud byl zaškrtnutí zaškrtávacího políčka Zobrazit jako ikonu.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce až po volání [DoModal](#domodal) vrátí **IDOK**.  
  
 Další informace o kreslení aspekt najdete v tématu [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura dat ve Windows SDK.  
  
##  <a name="geticonicmetafile"></a>COleConvertDialog::GetIconicMetafile  
 Volání této funkce se získat popisovač pro metafile, který obsahuje ikony aspekt vybrané položky.  
  
```  
HGLOBAL GetIconicMetafile() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač metafile obsahující ikony aspekt vybrané položky, pokud byl zaškrtněte políčko Zobrazit jako ikonu zaškrtnutí, když se tak, že zvolíte zavřel dialogové okno **OK**jinak **NULL**.  
  
##  <a name="getselectiontype"></a>COleConvertDialog::GetSelectionType  
 Volání této funkce se zjistit typ převodu vybrané v dialogovém okně Převést.  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Typ provedeného výběru.  
  
### <a name="remarks"></a>Poznámky  
 Návratový typ hodnoty jsou určené **výběr** typ výčtu deklarované v `COleConvertDialog` – třída.  
  
```  
enum Selection {
    noConversion,
    convertItem,
    activateAs
    };  
```  
  
 Postupujte podle stručný popis těchto hodnot:  
  
- **COleConvertDialog::noConversion** vrátil Pokud buď byla zrušena dialogové okno, nebo uživatel vybraný žádný převod. Pokud `COleConvertDialog::DoModal` vrátil **IDOK**, je možné, že vybraný uživatel jinou ikonu, než byla předtím vybrali.  
  
- **COleConvertDialog::convertItem** vrácena, pokud byla zaškrtnutá přepínač převést na, uživatel vybrat jinou položku převést, a `DoModal` vrátil **IDOK**.  
  
- **COleConvertDialog::activateAs** vrácena, pokud byl zaškrtnutí přepínač aktivovat jako uživatel vybral jinou položku chcete aktivovat, a `DoModal` vrátil **IDOK**.  
  
##  <a name="m_cv"></a>COleConvertDialog::m_cv  
 Struktura typu **OLEUICONVERT** používat k ovládání chování dialogové okno Převést.  
  
```  
OLEUICONVERT m_cv;  
```  
  
### <a name="remarks"></a>Poznámky  
 Členy této struktury lze změnit buď přímo nebo prostřednictvím členských funkcí.  
  
 Další informace najdete v tématu [OLEUICONVERT](http://msdn.microsoft.com/library/windows/desktop/ms686657) struktura ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [COleDialog – třída](../../mfc/reference/coledialog-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [COleDialog – třída](../../mfc/reference/coledialog-class.md)
