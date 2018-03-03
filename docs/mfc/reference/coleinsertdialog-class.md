---
title: "Třída COleInsertDialog | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleInsertDialog
- AFXODLGS/COleInsertDialog
- AFXODLGS/COleInsertDialog::COleInsertDialog
- AFXODLGS/COleInsertDialog::CreateItem
- AFXODLGS/COleInsertDialog::DoModal
- AFXODLGS/COleInsertDialog::GetClassID
- AFXODLGS/COleInsertDialog::GetDrawAspect
- AFXODLGS/COleInsertDialog::GetIconicMetafile
- AFXODLGS/COleInsertDialog::GetPathName
- AFXODLGS/COleInsertDialog::GetSelectionType
- AFXODLGS/COleInsertDialog::m_io
dev_langs:
- C++
helpviewer_keywords:
- COleInsertDialog [MFC], COleInsertDialog
- COleInsertDialog [MFC], CreateItem
- COleInsertDialog [MFC], DoModal
- COleInsertDialog [MFC], GetClassID
- COleInsertDialog [MFC], GetDrawAspect
- COleInsertDialog [MFC], GetIconicMetafile
- COleInsertDialog [MFC], GetPathName
- COleInsertDialog [MFC], GetSelectionType
- COleInsertDialog [MFC], m_io
ms.assetid: a9ec610b-abde-431e-bd01-c40159a66dbb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4638471ed199d08bb21bcf16465fe933af3a584c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="coleinsertdialog-class"></a>COleInsertDialog – třída
Používá se pro dialogové okno Vložit objekt OLE.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleInsertDialog : public COleDialog  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[COleInsertDialog::COleInsertDialog](#coleinsertdialog)|Vytvoří `COleInsertDialog` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleInsertDialog::CreateItem](#createitem)|Vytvoří položky vybrané v dialogovém okně.|  
|[COleInsertDialog::DoModal](#domodal)|Zobrazí dialogové okno Vložit objekt OLE.|  
|[COleInsertDialog::GetClassID](#getclassid)|Získá **CLSID** přidružené k vybrané položce.|  
|[COleInsertDialog::GetDrawAspect](#getdrawaspect)|Určuje, jestli se k vykreslení položky jako ikona.|  
|[COleInsertDialog::GetIconicMetafile](#geticonicmetafile)|Získá popisovač pro metafile přidružené ikony formu této položky.|  
|[COleInsertDialog::GetPathName](#getpathname)|Získá úplnou cestu k souboru vybrali v dialogovém okně.|  
|[COleInsertDialog::GetSelectionType](#getselectiontype)|Získá typ vybraného objektu.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[COleInsertDialog::m_io](#m_io)|Struktura typu **OLEUIINSERTOBJECT** , řídí chování dialogového okna.|  
  
## <a name="remarks"></a>Poznámky  
 Vytvoření objektu třídy `COleInsertDialog` když chcete volat tohoto dialogového okna. Po `COleInsertDialog` objekt byl vytvořen, můžete použít [m_io](#m_io) struktura k chybě při inicializaci hodnoty nebo stavy, které ovládacích prvků v dialogovém okně. `m_io` Struktura je typu **OLEUIINSERTOBJECT**. Další informace o používání této třídy dialogového okna, najdete v článku [DoModal](#domodal) – členská funkce.  
  
> [!NOTE]
>  Kód aplikace generované v Průvodci kontejneru používá tuto třídu.  
  
 Další informace najdete v tématu [OLEUIINSERTOBJECT](http://msdn.microsoft.com/library/windows/desktop/ms691316) struktura ve Windows SDK.  
  
 Další informace týkající se konkrétní OLE dialogových oken, najdete v článku [dialogová okna v prostředí OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleInsertDialog`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxodlgs.h  
  
##  <a name="coleinsertdialog"></a>COleInsertDialog::COleInsertDialog  
 Tato funkce se vytvoří pouze `COleInsertDialog` objektu.  
  
```  
COleInsertDialog (
    DWORD dwFlags = IOF_SELECTCREATENEW,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `dwFlags`  
 Vytvoření příznak, který obsahuje libovolný počet následující hodnoty a nelze jej zkombinovat pomocí operátoru bitové operace OR:  
  
- **IOF_SHOWHELP** Určuje, že na tlačítko Nápověda se zobrazí, když je volána dialogové okno.  
  
- **IOF_SELECTCREATENEW** Určuje, že vytvořit nový přepínač vybere původně při volání dialogové okno. Toto je výchozí a nelze použít s **IOF_SELECTCREATEFROMFILE**.  
  
- **IOF_SELECTCREATEFROMFILE** Určuje, že přepínač Vytvořit ze souboru vybere původně při volání dialogové okno. Nelze použít s **IOF_SELECTCREATENEW**.  
  
- **IOF_CHECKLINK** Určuje, že políčko Propojit se zkontrolují původně po se označuje jako dialogové okno.  
  
- **IOF_DISABLELINK** Určuje, že políčko Propojit budou vypnuté, když je volána dialogové okno.  
  
- **IOF_CHECKDISPLAYASICON** Určuje, který bude ověřen původně zaškrtněte políčko Zobrazit jako ikonu, se zobrazí aktuální ikona a na tlačítko Změnit ikonu bude povolena, když je volána dialogové okno.  
  
- **IOF_VERIFYSERVERSEXIST** Určuje, že by měl dialogové okno ověření třídy se přidá do seznamu tím, že zajistí, že zadané v databázi registrace servery existují předtím, než se zobrazí dialogové okno. Nastavením tohoto příznaku může výrazně zhoršit výkon.  
  
 `pParentWnd`  
 Odkazuje na objekt okno nadřazené nebo vlastníka (typu `CWnd`), ke které patří objektu dialogového okna. Pokud je **NULL**, okno nadřazeného objektu dialogové okno bude nastaveno na hlavní okno aplikace.  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li zobrazit dialogové okno, zavolejte [DoModal](#domodal) funkce.  
  
##  <a name="createitem"></a>COleInsertDialog::CreateItem  
 Volání této funkce pro vytvoření objektu typu [COleClientItem](../../mfc/reference/coleclientitem-class.md) pouze v případě [DoModal](#domodal) vrátí **IDOK**.  
  
```  
BOOL CreateItem(COleClientItem* pItem);
```  
  
### <a name="parameters"></a>Parametry  
 `pItem`  
 Odkazuje na položku, kterou chcete vytvořit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud položka byla vytvořena; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Je třeba přiřadit `COleClientItem` objektu, než bude možné volat tuto funkci.  
  
##  <a name="domodal"></a>COleInsertDialog::DoModal  
 Volání této funkce můžete zobrazit dialogové okno Vložit objekt OLE.  
  
```  
virtual INT_PTR   
    DoModal();

 
INT_PTR   
    DoModal(DWORD  dwFlags);
```  
  
### <a name="parameters"></a>Parametry  
 `dwFlags`  
 Jedna z následujících hodnot:  
  
 `COleInsertDialog::DocObjectsOnly`Vloží pouze DocObjects.  
  
 `COleInsertDialog::ControlsOnly`Vloží pouze ovládací prvky ActiveX.  
  
 Nula vloží DocObject ani ovládacího prvku ActiveX. Výsledkem hodnota stejnou implementaci jako první prototypu uvedené výše.  
  
### <a name="return-value"></a>Návratová hodnota  
 Stav dokončení pro dialogové okno. Jedna z následujících hodnot:  
  
-   IDOK Pokud úspěšně zobrazí dialogové okno.  
  
-   IDCANCEL, pokud uživatel zrušil dialogové okno.  
  
-   IDABORT, pokud došlo k chybě. Pokud je vrácen IDABORT, zavolejte [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) – členská funkce získat další informace o typu Chyba, že došlo k chybě. Seznam možné chyby, najdete v článku [OleUIInsertObject](http://msdn.microsoft.com/library/windows/desktop/ms694325) funkce ve Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete k chybě při inicializaci různých dialogové okno Ovládací prvky nastavením členy [m_io](#m_io) struktura, bude třeba provést před voláním `DoModal`, ale po objektu dialogového okna je vytvořený.  
  
 Pokud `DoModal` IDOK, vrátí funkce můžete volat jiného člena k načtení nastavení nebo informace o vstup do dialogových oken uživatelem.  
  
##  <a name="getclassid"></a>COleInsertDialog::GetClassID  
 Volání této funkce můžete získat **CLSID** spojené s pouze pokud vybraná položka [DoModal](#domodal) vrátí **IDOK** a výběr typ je **COleInsertDialog:: createNewItem**.  
  
```  
REFCLSID GetClassID() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **CLSID** spojené s vybranou položku.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [klíč CLSID](http://msdn.microsoft.com/library/windows/desktop/ms691424) ve Windows SDK.  
  
##  <a name="getdrawaspect"></a>COleInsertDialog::GetDrawAspect  
 Volání této funkce k určení, pokud se uživatel rozhodl zobrazit jako ikonu vybranou položku.  
  
```  
DVASPECT GetDrawAspect() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Metoda potřebné k vykreslení objektu.  
  
- `DVASPECT_CONTENT`Vrátí, pokud není zaškrtnuto zaškrtávací políčko Zobrazit jako ikonu.  
  
- `DVASPECT_ICON`Vrátí, pokud byl zaškrtnutí zaškrtávacího políčka Zobrazit jako ikonu.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce jenom Pokud [DoModal](#domodal) vrátí **IDOK**.  
  
 Další informace o kreslení aspekt najdete v tématu [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura dat ve Windows SDK.  
  
##  <a name="geticonicmetafile"></a>COleInsertDialog::GetIconicMetafile  
 Volání této funkce se získat popisovač pro metafile, který obsahuje ikony aspekt vybrané položky.  
  
```  
HGLOBAL GetIconicMetafile() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač metafile obsahující ikony aspekt vybrané položky, pokud byl zaškrtněte políčko Zobrazit jako ikonu zaškrtnutí, když se tak, že zvolíte zavřel dialogové okno **OK**jinak **NULL**.  
  
##  <a name="getpathname"></a>COleInsertDialog::GetPathName  
 Volání této funkce můžete získat úplnou cestu jenom Pokud vybraný soubor [DoModal](#domodal) vrátí **IDOK** a typ výběru není **COleInsertDialog::createNewItem**.  
  
```  
CString GetPathName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Úplná cesta k souboru vybraného v dialogovém okně. Pokud je typ výběru `createNewItem`, funkce vrátí hodnotu smysl `CString` v režimu vydání nebo způsobí, že kontrolní výrazy v režimu ladění.  
  
##  <a name="getselectiontype"></a>COleInsertDialog::GetSelectionType  
 Volání této funkce se získat typ výběr vybrali při odmítnuta dialogové okno Vložit objekt výběrem **OK**.  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Typ provedeného výběru.  
  
### <a name="remarks"></a>Poznámky  
 Návratový typ hodnoty jsou určené **výběr** typ výčtu deklarované v `COleInsertDialog` – třída.  
  
```  
enum Selection {
    createNewItem,
    insertFromFile,
    linkToFile
    };  
```  
  
 Postupujte podle stručný popis těchto hodnot:  
  
- **COleInsertDialog::createNewItem** byl vybrán přepínač The vytvořit nový.  
  
- **COleInsertDialog::insertFromFile** byl vybrán přepínač The vytvořit ze souboru a odkaz políčko nebyla zkontrolována.  
  
- **COleInsertDialog::linkToFile** byl vybrán přepínač The vytvořit ze souboru a odkaz políčko byla zaškrtnutá.  
  
##  <a name="m_io"></a>COleInsertDialog::m_io  
 Struktura typu **OLEUIINSERTOBJECT** používat k ovládání chování dialogové okno Vložit objekt.  
  
```  
OLEUIINSERTOBJECT m_io;  
```  
  
### <a name="remarks"></a>Poznámky  
 Členy této struktury lze změnit buď přímo nebo prostřednictvím členských funkcí.  
  
 Další informace najdete v tématu [OLEUIINSERTOBJECT](http://msdn.microsoft.com/library/windows/desktop/ms691316) struktura ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC OCLIENT](../../visual-cpp-samples.md)   
 [COleDialog – třída](../../mfc/reference/coledialog-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [COleDialog – třída](../../mfc/reference/coledialog-class.md)
