---
title: Coledatasource – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleDataSource
- AFXOLE/COleDataSource
- AFXOLE/COleDataSource::COleDataSource
- AFXOLE/COleDataSource::CacheData
- AFXOLE/COleDataSource::CacheGlobalData
- AFXOLE/COleDataSource::DelayRenderData
- AFXOLE/COleDataSource::DelayRenderFileData
- AFXOLE/COleDataSource::DelaySetData
- AFXOLE/COleDataSource::DoDragDrop
- AFXOLE/COleDataSource::Empty
- AFXOLE/COleDataSource::FlushClipboard
- AFXOLE/COleDataSource::GetClipboardOwner
- AFXOLE/COleDataSource::OnRenderData
- AFXOLE/COleDataSource::OnRenderFileData
- AFXOLE/COleDataSource::OnRenderGlobalData
- AFXOLE/COleDataSource::OnSetData
- AFXOLE/COleDataSource::SetClipboard
dev_langs:
- C++
helpviewer_keywords:
- COleDataSource [MFC], COleDataSource
- COleDataSource [MFC], CacheData
- COleDataSource [MFC], CacheGlobalData
- COleDataSource [MFC], DelayRenderData
- COleDataSource [MFC], DelayRenderFileData
- COleDataSource [MFC], DelaySetData
- COleDataSource [MFC], DoDragDrop
- COleDataSource [MFC], Empty
- COleDataSource [MFC], FlushClipboard
- COleDataSource [MFC], GetClipboardOwner
- COleDataSource [MFC], OnRenderData
- COleDataSource [MFC], OnRenderFileData
- COleDataSource [MFC], OnRenderGlobalData
- COleDataSource [MFC], OnSetData
- COleDataSource [MFC], SetClipboard
ms.assetid: 02c8ee7d-8e10-4463-8613-bb2a0305ca69
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4df2584bd9b74640266d8ddf87087e2820deaac8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33376704"
---
# <a name="coledatasource-class"></a>Coledatasource – třída
Jednání jako mezipaměť, do které aplikace umístí data, která nabízí během data přenášet operace, např. schránku nebo operací přetažení myší.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleDataSource : public CCmdTarget  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[COleDataSource::COleDataSource](#coledatasource)|Vytvoří `COleDataSource` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleDataSource::CacheData](#cachedata)|Nabízí data v zadaném formátu, který používá **STGMEDIUM** struktury.|  
|[COleDataSource::CacheGlobalData](#cacheglobaldata)|Nabízí data v zadaném formátu, který používá `HGLOBAL`.|  
|[COleDataSource::DelayRenderData](#delayrenderdata)|Nabízí data v zadaném formátu pomocí zpožděné vykreslování.|  
|[COleDataSource::DelayRenderFileData](#delayrenderfiledata)|Nabízí data ve formátu určeného v `CFile` ukazatel.|  
|[COleDataSource::DelaySetData](#delaysetdata)|Volá se pro každý formát, který je podporován v `OnSetData`.|  
|[COleDataSource::DoDragDrop](#dodragdrop)|Operace přetažení myší se zdrojem dat provádí.|  
|[COleDataSource::Empty](#empty)|Vyprázdní `COleDataSource` objekt data.|  
|[COleDataSource::FlushClipboard](#flushclipboard)|Vykreslí všechna data do schránky.|  
|[COleDataSource::GetClipboardOwner](#getclipboardowner)|Ověřuje, že data umístit do schránky je stále existuje.|  
|[COleDataSource::OnRenderData](#onrenderdata)|Načte data v rámci zpožděné vykreslování.|  
|[COleDataSource::OnRenderFileData](#onrenderfiledata)|Načítání dat do `CFile` jako součást zpožděné vykreslování.|  
|[COleDataSource::OnRenderGlobalData](#onrenderglobaldata)|Načte data do `HGLOBAL` jako součást zpožděné vykreslování.|  
|[COleDataSource::OnSetData](#onsetdata)|Voláno k nahrazení data v `COleDataSource` objektu.|  
|[COleDataSource::SetClipboard](#setclipboard)|Místech `COleDataSource` objektu do schránky.|  
  
## <a name="remarks"></a>Poznámky  
 Vytvořením zdroje dat OLE přímo. Můžete také [COleClientItem](../../mfc/reference/coleclientitem-class.md) a [COleServerItem](../../mfc/reference/coleserveritem-class.md) třídy Vytvoření zdroje dat OLE v reakci na jejich `CopyToClipboard` a `DoDragDrop` členské funkce. V tématu [COleServerItem::CopyToClipboard](../../mfc/reference/coleserveritem-class.md#copytoclipboard) stručný popis. Přepsání `OnGetClipboardData` – členská funkce třída klienta položky nebo server položku pro přidání dalších formátech schránky do dat ve zdroji dat OLE pro vytvořit `CopyToClipboard` nebo `DoDragDrop` – členská funkce.  
  
 Vždy, když chcete připravit data přenosu, doporučujeme vytvoření objektu této třídy a vyplňte v něm s daty pomocí metody nejvhodnější pro vaše data. Způsob, jakým je vložen do zdroje dat je přímo ovlivňován okamžitě zadaná data (okamžitou vykreslování) nebo na vyžádání (odložené vykreslování). Pro každý formát schránky, ve kterém jsou poskytuje data předáním formát schránky, který se má použít (a volitelné [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura), volání [DelayRenderData](#delayrenderdata).  
  
 Další informace o zdrojích dat a přenos dat, najdete v článku [datové objekty a zdroje dat (OLE)](../../mfc/data-objects-and-data-sources-ole.md). Kromě toho článek [schránky témata](../../mfc/clipboard.md) popisuje mechanismu schránky OLE.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDataSource`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxole.h  
  
##  <a name="cachedata"></a>  COleDataSource::CacheData  
 Volání této funkce můžete určit formát, ve kterém dat je nabídnuta během data operace přenosu.  
  
```  
void CacheData(
    CLIPFORMAT cfFormat,  
    LPSTGMEDIUM lpStgMedium,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `cfFormat`  
 Formát schránky, ve kterém má být nabízí data. Tento parametr může být jeden z předdefinovaných formátů schránky nebo hodnoty vrácené nativní Windows [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) funkce.  
  
 `lpStgMedium`  
 Odkazuje na [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) struktura obsahující data ve formátu určeném.  
  
 `lpFormatEtc`  
 Odkazuje na [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura popisující formát, ve kterém má být nabízí data. Zadejte hodnotu pro tento parametr, pokud chcete zadat informace o dalších formátu nad rámec formát schránky určeného `cfFormat`. Pokud je **NULL**, použijí se výchozí hodnoty pro v ostatních polích **FORMATETC** struktura.  
  
### <a name="remarks"></a>Poznámky  
 Je třeba zadat data, protože tato funkce poskytuje ji pomocí okamžitou vykreslování. Data se uloží do mezipaměti, dokud nebude potřeba.  
  
 Zadat data pomocí [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) struktury. Můžete také `CacheGlobalData` – členská funkce pokud poskytuje množství dat, je dostatečně malé, které se mají přenést, efektivně pomocí `HGLOBAL`.  
  
 Po zavolání `CacheData` **ptd** členem `lpFormatEtc` a obsah `lpStgMedium` jsou vlastněny datový objekt, ne podle volající.  
  
 Chcete-li použít zpožděné vykreslování, zavolejte [DelayRenderData](#delayrenderdata) nebo [DelayRenderFileData](#delayrenderfiledata) – členská funkce. Další informace o zpožděné vykreslování jako zpracované MFC, najdete v článku [datové objekty a zdroje dat: manipulace s](../../mfc/data-objects-and-data-sources-manipulation.md).  
  
 Další informace najdete v tématu [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) a [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktury v sadě Windows SDK.  
  
 Další informace najdete v tématu [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) ve Windows SDK.  
  
##  <a name="cacheglobaldata"></a>  COleDataSource::CacheGlobalData  
 Volání této funkce můžete určit formát, ve kterém dat je nabídnuta během data operace přenosu.  
  
```  
void CacheGlobalData(
    CLIPFORMAT cfFormat,  
    HGLOBAL hGlobal,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `cfFormat`  
 Formát schránky, ve kterém má být nabízí data. Tento parametr může být jeden z předdefinovaných formátů schránky nebo hodnoty vrácené nativní Windows [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) funkce.  
  
 *hGlobal*  
 Popisovač globální paměť bloku obsahující data ve formátu určeném.  
  
 `lpFormatEtc`  
 Odkazuje na [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura popisující formát, ve kterém má být nabízí data. Zadejte hodnotu pro tento parametr, pokud chcete zadat informace o dalších formátu nad rámec formát schránky určeného `cfFormat`. Pokud je **NULL**, použijí se výchozí hodnoty pro v ostatních polích **FORMATETC** struktura.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce poskytuje data pomocí okamžitou vykreslování, takže data musíte zadat při volání funkce; data se uloží do mezipaměti, dokud nebude potřeba. Použití `CacheData` – členská funkce, pokud jsou zadávání velké množství dat nebo pokud vyžadujete strukturovaných paměťového média.  
  
 Chcete-li použít zpožděné vykreslování, zavolejte [DelayRenderData](#delayrenderdata) nebo [DelayRenderFileData](#delayrenderfiledata) – členská funkce. Další informace o zpožděné vykreslování jako zpracované MFC, najdete v článku [datové objekty a zdroje dat: manipulace s](../../mfc/data-objects-and-data-sources-manipulation.md).  
  
 Další informace najdete v tématu [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura ve Windows SDK.  
  
 Další informace najdete v tématu [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) ve Windows SDK.  
  
##  <a name="coledatasource"></a>  COleDataSource::COleDataSource  
 Vytvoří `COleDataSource` objektu.  
  
```  
COleDataSource();
```  
  
##  <a name="delayrenderdata"></a>  COleDataSource::DelayRenderData  
 Volání této funkce můžete určit formát, ve kterém dat je nabídnuta během data operace přenosu.  
  
```  
void DelayRenderData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `cfFormat`  
 Formát schránky, ve kterém má být nabízí data. Tento parametr může být jeden z předdefinovaných formátů schránky nebo hodnoty vrácené nativní Windows [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) funkce.  
  
 `lpFormatEtc`  
 Odkazuje na [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura popisující formát, ve kterém má být nabízí data. Zadejte hodnotu pro tento parametr, pokud chcete zadat informace o dalších formátu nad rámec formát schránky určeného `cfFormat`. Pokud je **NULL**, použijí se výchozí hodnoty pro v ostatních polích **FORMATETC** struktura.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce poskytuje data pomocí zpožděné vykreslování, takže data se nedodává okamžitě. [OnRenderData](#onrenderdata) nebo [OnRenderGlobalData](#onrenderglobaldata) – členská funkce je volána k vyžádání data.  
  
 Tuto funkci použít, pokud nechcete zadat data prostřednictvím `CFile` objektu. Pokud chcete zadat data prostřednictvím `CFile` objektu, volání [DelayRenderFileData](#delayrenderfiledata) – členská funkce. Další informace o zpožděné vykreslování jako zpracované MFC, najdete v článku [datové objekty a zdroje dat: manipulace s](../../mfc/data-objects-and-data-sources-manipulation.md).  
  
 Chcete-li použít okamžitou vykreslování, zavolejte [CacheData](#cachedata) nebo [CacheGlobalData](#cacheglobaldata) – členská funkce.  
  
 Další informace najdete v tématu [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura ve Windows SDK.  
  
 Další informace najdete v tématu [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) ve Windows SDK.  
  
##  <a name="delayrenderfiledata"></a>  COleDataSource::DelayRenderFileData  
 Volání této funkce můžete určit formát, ve kterém dat je nabídnuta během data operace přenosu.  
  
```  
void DelayRenderFileData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `cfFormat`  
 Formát schránky, ve kterém má být nabízí data. Tento parametr může být jeden z předdefinovaných formátů schránky nebo hodnoty vrácené nativní Windows [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) funkce.  
  
 `lpFormatEtc`  
 Odkazuje na [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura popisující formát, ve kterém má být nabízí data. Zadejte hodnotu pro tento parametr, pokud chcete zadat informace o dalších formátu nad rámec formát schránky určeného `cfFormat`. Pokud je **NULL**, použijí se výchozí hodnoty pro v ostatních polích **FORMATETC** struktura.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce poskytuje data pomocí zpožděné vykreslování, takže data se nedodává okamžitě. [OnRenderFileData](#onrenderfiledata) – členská funkce je volána k vyžádání data.  
  
 Tuto funkci použít, pokud se bude používat `CFile` objekt, který chcete zadat data. Pokud nechcete použít `CFile` objektu, volání [DelayRenderData](#delayrenderdata) – členská funkce. Další informace o zpožděné vykreslování jako zpracované MFC, najdete v článku [datové objekty a zdroje dat: manipulace s](../../mfc/data-objects-and-data-sources-manipulation.md).  
  
 Chcete-li použít okamžitou vykreslování, zavolejte [CacheData](#cachedata) nebo [CacheGlobalData](#cacheglobaldata) – členská funkce.  
  
 Další informace najdete v tématu [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura ve Windows SDK.  
  
 Další informace najdete v tématu [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) ve Windows SDK.  
  
##  <a name="delaysetdata"></a>  COleDataSource::DelaySetData  
 Volání této funkce můžete podporovat změnu obsah datového zdroje.  
  
```  
void DelaySetData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `cfFormat`  
 Formát schránky, ve kterém má být umístěn data. Tento parametr může být jeden z předdefinovaných formátů schránky nebo hodnoty vrácené nativní Windows [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) funkce.  
  
 `lpFormatEtc`  
 Odkazuje na [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura popisující formát, ve kterém má být nahrazen data. Zadejte hodnotu pro tento parametr, pokud chcete zadat informace o dalších formátu nad rámec formát schránky určeného `cfFormat`. Pokud je **NULL**, použijí se výchozí hodnoty pro v ostatních polích **FORMATETC** struktura.  
  
### <a name="remarks"></a>Poznámky  
 [OnSetData](#onsetdata) bude volat rozhraní v takovém případě. Používá se jen při rozhraní vrátí zdroj dat z [COleServerItem::GetDataSource](../../mfc/reference/coleserveritem-class.md#getdatasource). Pokud `DelaySetData` není volán, vaše `OnSetData` funkce nebude nikdy volat. `DelaySetData` by měla být volána pro každý schránky nebo **FORMATETC** formátu, které podporujete.  
  
 Další informace najdete v tématu [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura ve Windows SDK.  
  
 Další informace najdete v tématu [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) ve Windows SDK.  
  
##  <a name="dodragdrop"></a>  COleDataSource::DoDragDrop  
 Volání `DoDragDrop` – členská funkce k provedení operace přetažení myší pro tento zdroj dat, obvykle v [CWnd::OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown) obslužné rutiny.  
  
```  
DROPEFFECT DoDragDrop(
    DWORD dwEffects = DROPEFFECT_COPY|DROPEFFECT_MOVE|DROPEFFECT_LINK,  
    LPCRECT lpRectStartDrag = NULL,  
    COleDropSource* pDropSource = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `dwEffects`  
 Přetažení myší operace, které jsou povoleny na tomto datovém zdroji. Může být jeden nebo více následujících akcí:  
  
- `DROPEFFECT_COPY` Operace kopírování můžete provést.  
  
- `DROPEFFECT_MOVE` Můžete provést operaci přesunutí.  
  
- `DROPEFFECT_LINK` Může vytvořit odkaz z vynechaných dat na původní data.  
  
- `DROPEFFECT_SCROLL` Označuje, že mohlo dojít posuňte operaci přetažení.  
  
 `lpRectStartDrag`  
 Ukazatel na obdélníku, která definuje, kde přetáhněte skutečně spustí. Další informace naleznete v následující části poznámky.  
  
 *pDropSource*  
 Odkazuje na zdroje přetažení. Pokud **NULL** pak výchozí implementaci třídy [COleDropSource](../../mfc/reference/coledropsource-class.md) se použije.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vyřaďte vliv generovány operací přetažení myší; v opačném případě `DROPEFFECT_NONE` Pokud operaci nikdy začne, protože uživatel vydané před opuštěním zadaný obdélník tlačítko myši.  
  
### <a name="remarks"></a>Poznámky  
 Operaci přetažení myší nespustí okamžitě. Čeká, dokud myší opustí rámeček určeného `lpRectStartDrag` nebo dokud předané zadaný počet milisekund. Pokud `lpRectStartDrag` je **NULL**, velikost rámeček je jeden pixel.  
  
 Doba zpoždění je určena nastavení klíče registru. Doba zpoždění lze změnit pomocí volání [CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) nebo [CWinApp::WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint). Pokud nezadáte čas zpoždění, se používá výchozí hodnota je 200 MS. Doba zpoždění přetažení se ukládají následujícím způsobem:  
  
-   Doba zpoždění systému Windows NT přetáhněte je uložená v HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay.  
  
-   Doba zpoždění přetáhněte 3.x Windows je uložená v WIN. Soubor INI, části [Windows}.  
  
-   Doba zpoždění Windows 95/98 přetáhněte je uložená v mezipaměti verzi WIN. INI.  
  
 Pro další informace o tom, přetáhněte zpoždění informace jsou uloženy v registru buď nebo. Soubor INI, najdete v části [WriteProfileString](http://msdn.microsoft.com/library/windows/desktop/ms725504) ve Windows SDK.  
  
 Další informace najdete v článku [přetažení: implementace zdroje přetažení](../../mfc/drag-and-drop-implementing-a-drop-source.md).  
  
##  <a name="empty"></a>  COleDataSource::Empty  
 Volání této funkce na prázdnou `COleDataSource` objekt data.  
  
```  
void Empty();
```  
  
### <a name="remarks"></a>Poznámky  
 Obě do mezipaměti a formáty vykreslení zpoždění jsou vyprázdněny, takže se můžete znovu použít.  
  
 Další informace najdete v tématu [ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491) ve Windows SDK.  
  
##  <a name="flushclipboard"></a>  COleDataSource::FlushClipboard  
 Vykreslí data, která je do schránky a pak umožňuje vložení dat ze schránky po vypnutí aplikace.  
  
```  
static void PASCAL FlushClipboard();
```  
  
### <a name="remarks"></a>Poznámky  
 Použití [Modul SetClipboard](#setclipboard) dávat data do schránky.  
  
##  <a name="getclipboardowner"></a>  COleDataSource::GetClipboardOwner  
 Určuje, zda data do schránky došlo ke změně od [Modul SetClipboard](#setclipboard) poslední volala a pokud ano, identifikuje aktuálního vlastníka.  
  
```  
static COleDataSource* PASCAL GetClipboardOwner();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Zdroj dat aktuálně na do schránky nebo **NULL** Pokud není nic do schránky nebo pokud schránky není vlastníkem je volající aplikace.  
  
##  <a name="onrenderdata"></a>  COleDataSource::OnRenderData  
 Voláno rámcem k načtení dat v zadaném formátu.  
  
```  
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,  
    LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>Parametry  
 `lpFormatEtc`  
 Odkazuje na [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura určující formát, ve které je požadované informace.  
  
 `lpStgMedium`  
 Odkazuje na [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) struktury, ve kterém má být vrácen data.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Zadaný formát je jeden dříve umístili ve `COleDataSource` pomocí [DelayRenderData](#delayrenderdata) nebo [DelayRenderFileData](#delayrenderfiledata) – členská funkce pro zpožděné vykreslování. Výchozí implementace této funkce bude volat [OnRenderFileData](#onrenderfiledata) nebo [OnRenderGlobalData](#onrenderglobaldata) Pokud zadaná úložné médium je soubor nebo paměti, v uvedeném pořadí. Pokud jsou zadány ani jeden z těchto formátů, bude výchozí implementace vraťte 0 a nic nestane. Další informace o zpožděné vykreslování jako zpracované MFC, najdete v článku [datové objekty a zdroje dat: manipulace s](../../mfc/data-objects-and-data-sources-manipulation.md).  
  
 Pokud `lpStgMedium` ->  *objekt tymed* je **TYMED_NULL**, **STGMEDIUM** by měl být přidělené a vyplněna podle specifikace *lpFormatEtc -> objekt tymed*. Pokud není **TYMED_NULL**, **STGMEDIUM** je nutné zadat místní s daty.  
  
 Toto je rozšířené přepisovatelné. Funkci k poskytování vaše data v požadovaný formát a střední přepište. V závislosti na vaše data můžete místo toho jeden z jiné verze této funkce přepsání. Pokud vaše data jsou malé a pevnou velikost, mají přednost před `OnRenderGlobalData`. Pokud vaše data jsou v souboru nebo s proměnnou velikostí, mají přednost před `OnRenderFileData`.  
  
 Další informace najdete v tématu [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) a [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktur, [objekt TYMED](http://msdn.microsoft.com/library/windows/desktop/ms691227) typ výčtu a [IDataObject::GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431) v systému Windows SDK.  
  
##  <a name="onrenderfiledata"></a>  COleDataSource::OnRenderFileData  
 Voláno rámcem k načtení dat v zadaném formátu, pokud zadaný úložné médium je soubor.  
  
```  
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,  
    CFile* pFile);
```  
  
### <a name="parameters"></a>Parametry  
 `lpFormatEtc`  
 Odkazuje na [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura určující formát, ve které je požadované informace.  
  
 `pFile`  
 Odkazuje na [cfile –](../../mfc/reference/cfile-class.md) objektu, ve kterém má být vykreslen data.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Zadaný formát je jeden dříve umístili ve `COleDataSource` pomocí [DelayRenderData](#delayrenderdata) – členská funkce pro zpožděné vykreslování. Výchozí implementace této funkce jednoduše vrací **FALSE**.  
  
 Toto je rozšířené přepisovatelné. Funkci k poskytování vaše data v požadovaný formát a střední přepište. V závislosti na vaše data můžete místo toho jeden z jiné verze této funkce přepsání. Pokud chcete zpracovat více úložná média, mají přednost před [OnRenderData](#onrenderdata). Pokud vaše data jsou v souboru nebo s proměnnou velikostí, mají přednost před `OnRenderFileData`. Další informace o zpožděné vykreslování jako zpracované MFC, najdete v článku [datové objekty a zdroje dat: manipulace s](../../mfc/data-objects-and-data-sources-manipulation.md).  
  
 Další informace najdete v tématu [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura a [IDataObject::GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431) ve Windows SDK.  
  
##  <a name="onrenderglobaldata"></a>  COleDataSource::OnRenderGlobalData  
 Voláno rámcem k načtení dat v zadaném formátu, když střední zadané úložiště je globální paměť.  
  
```  
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,  
    HGLOBAL* phGlobal);
```  
  
### <a name="parameters"></a>Parametry  
 `lpFormatEtc`  
 Odkazuje na [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura určující formát, ve které je požadované informace.  
  
 `phGlobal`  
 Odkazuje na popisovač pro globální paměť, ve kterém má být vrácen data. Pokud nebyl ještě jednu byly přiděleny, tento parametr může být **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Zadaný formát je jeden dříve umístili ve `COleDataSource` pomocí [DelayRenderData](#delayrenderdata) – členská funkce pro zpožděné vykreslování. Výchozí implementace této funkce jednoduše vrací **FALSE**.  
  
 Pokud `phGlobal` je **NULL**, pak nový `HGLOBAL` by měl být přidělené a vrácených v `phGlobal`. V opačném `HGLOBAL` specifikováno na základě `phGlobal` by mělo být zadáno s daty. Množství dat umístěny `HGLOBAL` nesmí být delší než aktuální velikost bloku paměti. Navíc bloku nelze znovu přidělit, větší velikost.  
  
 Toto je rozšířené přepisovatelné. Funkci k poskytování vaše data v požadovaný formát a střední přepište. V závislosti na vaše data můžete místo toho jeden z jiné verze této funkce přepsání. Pokud chcete zpracovat více úložná média, mají přednost před [OnRenderData](#onrenderdata). Pokud vaše data jsou v souboru nebo s proměnnou velikostí, mají přednost před [OnRenderFileData](#onrenderfiledata). Další informace o zpožděné vykreslování jako zpracované MFC, najdete v článku [datové objekty a zdroje dat: manipulace s](../../mfc/data-objects-and-data-sources-manipulation.md).  
  
 Další informace najdete v tématu [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura a [IDataObject::GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431) ve Windows SDK.  
  
##  <a name="onsetdata"></a>  COleDataSource::OnSetData  
 Voláno rámcem nastavit nebo nahradit data v `COleDataSource` objekt v zadaném formátu.  
  
```  
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,  
    LPSTGMEDIUM lpStgMedium,  
    BOOL bRelease);
```  
  
### <a name="parameters"></a>Parametry  
 `lpFormatEtc`  
 Odkazuje na [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura určující formát, ve kterém data nahradit.  
  
 `lpStgMedium`  
 Odkazuje na [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) struktura obsahující data, která nahradí aktuální obsah `COleDataSource` objektu.  
  
 `bRelease`  
 Určuje, kdo je vlastníkem úložiště střední po dokončení volání funkce. Volající rozhodne, který je zodpovědný za uvolnění prostředky přidělené jménem paměťového média. Volající dosahuje tím, že nastavení `bRelease`. Pokud `bRelease` je nenulové hodnoty, zdroj dat trvá vlastnictví, uvolnění médium, až se dokončí, jeho použití. Když `bRelease` je 0, volající uchovává vlastnictví a zdroj dat můžete použít úložiště střední pouze po dobu trvání volání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Zdroj dat nevyžaduje vlastnictví dat, dokud ho má byly úspěšně načteny. To znamená, že se nevyžaduje vlastnictví Pokud `OnSetData` vrátí hodnotu 0. Pokud zdroj dat používá vlastnictví, uvolní úložné médium voláním [ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491) funkce.  
  
 Výchozí implementace neprovede žádnou akci. Přepsání této funkci můžete nahradit data v zadaném formátu. Toto je rozšířené přepisovatelné.  
  
 Další informace najdete v tématu [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) a [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktury a [ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491) a [IDataObject::GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431) funkce ve Windows SDK.  
  
##  <a name="setclipboard"></a>  COleDataSource::SetClipboard  
 Převádí data obsažená v `COleDataSource` objektu do schránky po volání jedné z následujících funkcí: [CacheData](#cachedata), [CacheGlobalData](#cacheglobaldata), [DelayRenderData](#delayrenderdata), nebo [DelayRenderFileData](#delayrenderfiledata).  
  
```  
void SetClipboard();
```  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC HIERSVR](../../visual-cpp-samples.md)   
 [Ukázka MFC OCLIENT](../../visual-cpp-samples.md)   
 [CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [COleDataObject – třída](../../mfc/reference/coledataobject-class.md)
