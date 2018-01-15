---
title: "Třída COlePasteSpecialDialog | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog::COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog::AddFormat
- AFXODLGS/COlePasteSpecialDialog::AddLinkEntry
- AFXODLGS/COlePasteSpecialDialog::AddStandardFormats
- AFXODLGS/COlePasteSpecialDialog::CreateItem
- AFXODLGS/COlePasteSpecialDialog::DoModal
- AFXODLGS/COlePasteSpecialDialog::GetDrawAspect
- AFXODLGS/COlePasteSpecialDialog::GetIconicMetafile
- AFXODLGS/COlePasteSpecialDialog::GetPasteIndex
- AFXODLGS/COlePasteSpecialDialog::GetSelectionType
- AFXODLGS/COlePasteSpecialDialog::m_ps
dev_langs: C++
helpviewer_keywords:
- COlePasteSpecialDialog [MFC], COlePasteSpecialDialog
- COlePasteSpecialDialog [MFC], AddFormat
- COlePasteSpecialDialog [MFC], AddLinkEntry
- COlePasteSpecialDialog [MFC], AddStandardFormats
- COlePasteSpecialDialog [MFC], CreateItem
- COlePasteSpecialDialog [MFC], DoModal
- COlePasteSpecialDialog [MFC], GetDrawAspect
- COlePasteSpecialDialog [MFC], GetIconicMetafile
- COlePasteSpecialDialog [MFC], GetPasteIndex
- COlePasteSpecialDialog [MFC], GetSelectionType
- COlePasteSpecialDialog [MFC], m_ps
ms.assetid: 0e82ef9a-9bbe-457e-8240-42c86a0534f7
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8680842f0aeeebf98eabc0f278089781290ad902
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="colepastespecialdialog-class"></a>COlePasteSpecialDialog – třída
Používá se pro dialogové okno OLE Vložit jinak.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COlePasteSpecialDialog : public COleDialog  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[COlePasteSpecialDialog::COlePasteSpecialDialog](#colepastespecialdialog)|Vytvoří `COlePasteSpecialDialog` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COlePasteSpecialDialog::AddFormat](#addformat)|Vlastní formáty přidá do seznamu formátů, které můžete vložit vaše aplikace.|  
|[COlePasteSpecialDialog::AddLinkEntry](#addlinkentry)|Přidá novou položku do seznamu podporovaných formátů schránky.|  
|[COlePasteSpecialDialog::AddStandardFormats](#addstandardformats)|Přidá **CF_BITMAP**, **CF_DIB**, `CF_METAFILEPICT`a volitelně `CF_LINKSOURCE` do seznamu formáty může vložit vaše aplikace.|  
|[COlePasteSpecialDialog::CreateItem](#createitem)|Vytvoří položku v kontejneru dokumentu pomocí zadaného formátu.|  
|[COlePasteSpecialDialog::DoModal](#domodal)|Zobrazí dialogové okno OLE Vložit jinak.|  
|[COlePasteSpecialDialog::GetDrawAspect](#getdrawaspect)|Určuje, jestli se k vykreslení položky jako ikony nebo ne.|  
|[COlePasteSpecialDialog::GetIconicMetafile](#geticonicmetafile)|Získá popisovač pro metafile přidružené ikony formu této položky.|  
|[COlePasteSpecialDialog::GetPasteIndex](#getpasteindex)|Získá index možnosti k dispozici vložení, který jste vybrali uživatelem.|  
|[COlePasteSpecialDialog::GetSelectionType](#getselectiontype)|Získá typ výběru vybrali.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[COlePasteSpecialDialog::m_ps](#m_ps)|Struktura typu **OLEUIPASTESPECIAL** ovládá funkce dialogového okna.|  
  
## <a name="remarks"></a>Poznámky  
 Vytvoření objektu třídy `COlePasteSpecialDialog` když chcete volat tohoto dialogového okna. Po `COlePasteSpecialDialog` objekt byl vytvořen, můžete použít [AddFormat](#addformat) a [AddStandardFormats](#addstandardformats) členské funkce pro přidání do dialogových oken formáty schránky. Můžete také [m_ps](#m_ps) struktura k chybě při inicializaci hodnoty nebo stavy, které ovládacích prvků v dialogovém okně. `m_ps` Struktura je typu **OLEUIPASTESPECIAL**.  
  
 Další informace najdete v tématu [OLEUIPASTESPECIAL](http://msdn.microsoft.com/library/windows/desktop/ms692434) struktura ve Windows SDK.  
  
 Další informace týkající se konkrétní OLE dialogových oken, najdete v článku [dialogová okna v prostředí OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COlePasteSpecialDialog`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxodlgs.h  
  
##  <a name="addformat"></a>COlePasteSpecialDialog::AddFormat  
 Volání této funkce můžete přidat nové formáty do seznamu formátů, které vaše aplikace může podporovat v rámci operace Vložit jinak.  
  
```  
void AddFormat(
    const FORMATETC& formatEtc,  
    LPTSTR lpszFormat,  
    LPTSTR lpszResult,  
    DWORD flags);

 
void AddFormat(
    UINT cf,  
    DWORD tymed,  
    UINT nFormatID,  
    BOOL bEnableIcon,  
    BOOL bLink);
```  
  
### <a name="parameters"></a>Parametry  
 *FMT*  
 Odkaz na datový typ, který chcete přidat.  
  
 `lpszFormat`  
 Řetězec, který popisuje formát pro uživatele.  
  
 *lpszResult*  
 Řetězec, který popisuje výsledek, pokud je tento formát zvolena v dialogovém okně.  
  
 `flags`  
 Různé propojování a vkládání možnosti, které jsou k dispozici pro tento formát. Tento příznak je bitová kombinace jednoho nebo více různých hodnot v **OLEUIPASTEFLAG** výčtového typu.  
  
 `cf`  
 Formát schránky, které chcete přidat.  
  
 *objekt tymed*  
 Typy médií, které jsou k dispozici v tomto formátu. To je bitová kombinace jednoho nebo více hodnot v **objekt TYMED** výčtového typu.  
  
 `nFormatID`  
 ID řetězec, který identifikuje tento formát. Formát tohoto řetězce je dva samostatné řetězce oddělenými znakem '\n'. První řetězec je stejný, které by byly předány v *lpstrFormat* parametr a druhý je stejný jako *lpstrResult* parametr.  
  
 *bEnableIcon*  
 Příznak, který určuje, zda je povoleno zaškrtněte políčko Zobrazit jako ikonu, když tento formát je vybrán v seznamu.  
  
 *Blikání*  
 Příznak, který určuje, zda je povoleno přepínač Vložit propojení, když tento formát je vybrán v seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Tuto funkci lze volat pro přidejte buď standardní formáty například **CF_TEXT** nebo **CF_TIFF** nebo vlastních formátů, které vaše aplikace je zaregistrovaná pomocí systému. Další informace o vkládání dat objektů do vaší aplikace, najdete v článku [datové objekty a zdroje dat: manipulace s](../../mfc/data-objects-and-data-sources-manipulation.md).  
  
 Další informace najdete v tématu [objekt TYMED](http://msdn.microsoft.com/library/windows/desktop/ms691227) typ výčtu a [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura ve Windows SDK.  
  
 Další informace najdete v tématu [OLEUIPASTEFLAG](http://msdn.microsoft.com/library/windows/desktop/ms682172) výčtového typu ve Windows SDK.  
  
##  <a name="addlinkentry"></a>COlePasteSpecialDialog::AddLinkEntry  
 Přidá novou položku do seznamu podporovaných formátů schránky.  
  
```  
OLEUIPASTEFLAG AddLinkEntry(UINT cf);
```  
  
### <a name="parameters"></a>Parametry  
 `cf`  
 Formát schránky, které chcete přidat.  
  
### <a name="return-value"></a>Návratová hodnota  
 [OLEUIPASTEFLAG](http://msdn.microsoft.com/library/windows/desktop/ms682172) struktura obsahující informace o nových odkazů.  
  
##  <a name="addstandardformats"></a>COlePasteSpecialDialog::AddStandardFormats  
 Volání této funkce můžete přidat následující formáty schránky do seznamu formátů, které vaše aplikace může podporovat v rámci Vložit jinak operace:  
  
```  
void AddStandardFormats(BOOL bEnableLink = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *bEnableLink*  
 Příznak, který určuje, jestli se má přidat `CF_LINKSOURCE` do seznamu formáty může vložit vaše aplikace.  
  
### <a name="remarks"></a>Poznámky  
  
- **CF_BITMAP**  
  
- **CF_DIB**  
  
- `CF_METAFILEPICT`  
  
- **"Vložený objekt"**  
  
-   (volitelně) **"Link zdroje"**  
  
 Tyto formáty jsou používány pro podporu vložení a propojení.  
  
##  <a name="colepastespecialdialog"></a>COlePasteSpecialDialog::COlePasteSpecialDialog  
 Vytvoří `COlePasteSpecialDialog` objektu.  
  
```  
COlePasteSpecialDialog(
    DWORD dwFlags = PSF_SELECTPASTE,  
    COleDataObject* pDataObject = NULL,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `dwFlags`  
 Vytvoření příznak obsahuje libovolný počet kombinované pomocí operátoru bitové operace OR následující příznaky:  
  
- `PSF_SELECTPASTE`Určuje, že přepínač vložení bude ověřen původně při volání dialogové okno. Nelze použít v kombinaci s `PSF_SELECTPASTELINK`. Toto nastavení je výchozí.  
  
- `PSF_SELECTPASTELINK`Určuje, že když je volána dialogové okno zaškrtnuté Vložit propojení bude přepínač původně. Nelze použít v kombinaci s `PSF_SELECTPASTE`.  
  
- `PSF_CHECKDISPLAYASICON`Určuje, že políčko Zobrazit jako ikonu se zkontrolují původně po se označuje jako dialogové okno.  
  
- `PSF_SHOWHELP`Určuje, že na tlačítko Nápověda se zobrazí, když je volána dialogové okno.  
  
 `pDataObject`  
 Odkazuje na [COleDataObject](../../mfc/reference/coledataobject-class.md) pro vložení. Pokud je tato hodnota **NULL**, získá `COleDataObject` ze schránky.  
  
 `pParentWnd`  
 Odkazuje na objekt okno nadřazené nebo vlastníka (typu `CWnd`), ke které patří objektu dialogového okna. Pokud je **NULL**, nadřazeného okna dialogového okna nastavena na hlavní okno aplikace.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce pouze vytvoří `COlePasteSpecialDialog` objektu. Chcete-li zobrazit dialogové okno, zavolejte [DoModal](#domodal) funkce.  
  
 Další informace najdete v tématu [OLEUIPASTEFLAG](http://msdn.microsoft.com/library/windows/desktop/ms682172) výčtového typu ve Windows SDK.  
  
##  <a name="createitem"></a>COlePasteSpecialDialog::CreateItem  
 Vytvoří novou položku, kterou jste vybrali v dialogovém okně Vložit jinak.  
  
```  
BOOL CreateItem(COleClientItem* pNewItem);
```  
  
### <a name="parameters"></a>Parametry  
 *pNewItem*  
 Odkazuje na `COleClientItem` instance. Nemůže být **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byla položka úspěšně; vytvořil jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce by měla být volána pouze po [DoModal](#domodal) vrátí **IDOK**.  
  
##  <a name="domodal"></a>COlePasteSpecialDialog::DoModal  
 Zobrazí dialogové okno OLE Vložit jinak.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Stav dokončení pro dialogové okno. Jedna z následujících hodnot:  
  
- **IDOK** Pokud úspěšně zobrazí dialogové okno.  
  
- **IDCANCEL** Pokud uživatel zrušil dialogové okno.  
  
- **IDABORT** Pokud došlo k chybě. Pokud **IDABORT** se volání vrátí, `COleDialog::GetLastError` – členská funkce získat další informace o typu Chyba, že došlo k chybě. Seznam možné chyby, najdete v článku [OleUIPasteSpecial](http://msdn.microsoft.com/library/windows/desktop/ms694512) funkce ve Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete k chybě při inicializaci různých dialogové okno Ovládací prvky nastavením členy [m_ps](#m_ps) struktura, bude třeba provést před voláním `DoModal`, ale po objektu dialogového okna je vytvořený.  
  
 Pokud `DoModal` vrátí **IDOK**, můžete volat jiné členské funkce načíst nastavení nebo uživatelský vstup informace do dialogových oken.  
  
##  <a name="getdrawaspect"></a>COlePasteSpecialDialog::GetDrawAspect  
 Určuje, pokud se uživatel rozhodl zobrazit jako ikonu vybranou položku.  
  
```  
DVASPECT GetDrawAspect() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Metoda potřebné k vykreslení objektu.  
  
- `DVASPECT_CONTENT`Vrátí, pokud nebyla zobrazit jako ikonu zaškrtávací políčko zaškrtnuto, když se zavře dialogové okno.  
  
- `DVASPECT_ICON`Vrátí, pokud při dialogové okno se zavře, zaškrtněte políčko Zobrazit jako ikonu byla zaškrtnutá.  
  
### <a name="remarks"></a>Poznámky  
 Pouze volání této funkce po [DoModal](#domodal) vrátí **IDOK**.  
  
 Další informace o kreslení aspekt najdete v tématu [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura ve Windows SDK.  
  
##  <a name="geticonicmetafile"></a>COlePasteSpecialDialog::GetIconicMetafile  
 Získá metafile přidružené k položce vybrané uživatelem.  
  
```  
HGLOBAL GetIconicMetafile() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač metafile obsahující ikony aspekt vybrané položky, pokud při dialogové okno se zavře výběrem zaškrtnuto políčko Zobrazit jako ikonu **OK**jinak **NULL**.  
  
##  <a name="getpasteindex"></a>COlePasteSpecialDialog::GetPasteIndex  
 Získá hodnotu indexu související s položkou vybraného uživatele.  
  
```  
int GetPasteIndex() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Index do pole **OLEUIPASTEENTRY** struktury, které se vybrané uživatelem. Formát, který odpovídá vybraného indexu se mají použít při provádění operace vložení.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [OLEUIPASTEENTRY](http://msdn.microsoft.com/library/windows/desktop/ms690165) struktura ve Windows SDK.  
  
##  <a name="getselectiontype"></a>COlePasteSpecialDialog::GetSelectionType  
 Určuje typ jednoho uživatele provedeného výběru.  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí typ provedeného výběru.  
  
### <a name="remarks"></a>Poznámky  
 Návratový typ hodnoty jsou určené **výběr** typ výčtu deklarované v `COlePasteSpecialDialog` – třída.  
  
```  
enum Selection {
    pasteLink,
    pasteNormal,
    pasteOther,
    pasteStatic
    };  
```  
  
 Postupujte podle stručný desccriptions z těchto hodnot:  
  
- **COlePasteSpecialDialog::pasteLink** byla zaškrtnutá přepínač The Vložit propojení a vybraný formát je standardní formát OLE.  
  
- **COlePasteSpecialDialog::pasteNormal** byla zaškrtnutá The vložení přepínač a vybraný formát je standardní formát OLE.  
  
- **COlePasteSpecialDialog::pasteOther** vybraném formátu není standardní formát OLE.  
  
- **COlePasteSpecialDialog::pasteStatic** vybraný formát byl metasoubory.  
  
##  <a name="m_ps"></a>COlePasteSpecialDialog::m_ps  
 Struktura typu **OLEUIPASTESPECIAL** používat k ovládání chování dialogové okno Vložit jinak.  
  
```  
OLEUIPASTESPECIAL m_ps;  
```  
  
### <a name="remarks"></a>Poznámky  
 Členové této struktury se dá změnit přímo nebo prostřednictvím členských funkcí.  
  
 Další informace najdete v tématu [OLEUIPASTESPECIAL](http://msdn.microsoft.com/library/windows/desktop/ms692434) struktura ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC OCLIENT](../../visual-cpp-samples.md)   
 [COleDialog – třída](../../mfc/reference/coledialog-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [COleDialog – třída](../../mfc/reference/coledialog-class.md)
