---
title: Coledataobject – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleDataObject
- AFXOLE/COleDataObject
- AFXOLE/COleDataObject::COleDataObject
- AFXOLE/COleDataObject::Attach
- AFXOLE/COleDataObject::AttachClipboard
- AFXOLE/COleDataObject::BeginEnumFormats
- AFXOLE/COleDataObject::Detach
- AFXOLE/COleDataObject::GetData
- AFXOLE/COleDataObject::GetFileData
- AFXOLE/COleDataObject::GetGlobalData
- AFXOLE/COleDataObject::GetNextFormat
- AFXOLE/COleDataObject::IsDataAvailable
- AFXOLE/COleDataObject::Release
dev_langs:
- C++
helpviewer_keywords:
- COleDataObject [MFC], COleDataObject
- COleDataObject [MFC], Attach
- COleDataObject [MFC], AttachClipboard
- COleDataObject [MFC], BeginEnumFormats
- COleDataObject [MFC], Detach
- COleDataObject [MFC], GetData
- COleDataObject [MFC], GetFileData
- COleDataObject [MFC], GetGlobalData
- COleDataObject [MFC], GetNextFormat
- COleDataObject [MFC], IsDataAvailable
- COleDataObject [MFC], Release
ms.assetid: d1cc84be-2e1c-4bb3-a8a0-565eb08aaa34
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 67a4f03db6a7c4cf37e59e05464865016d836097
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43215005"
---
# <a name="coledataobject-class"></a>Coledataobject – třída
Používáno v přenosech dat pro načtení dat v různých formátech ze schránky pomocí přetažení, nebo z vložené položky OLE.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleDataObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[COleDataObject::COleDataObject](#coledataobject)|Vytvoří `COleDataObject` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleDataObject::Attach](#attach)|Připojí zadaný datový objekt OLE `COleDataObject`.|  
|[COleDataObject::AttachClipboard](#attachclipboard)|Připojí datový objekt, který je do schránky.|  
|[COleDataObject::BeginEnumFormats](#beginenumformats)|Připraví pro jeden nebo více následujících `GetNextFormat` volání.|  
|[COleDataObject::Detach](#detach)|Odpojí přidružené `IDataObject` objektu.|  
|[COleDataObject::GetData](#getdata)|Kopíruje data z připojených datový objekt OLE v zadaném formátu.|  
|[COleDataObject::GetFileData](#getfiledata)|Kopíruje data z připojeného objektu OLE dat do `CFile` ukazatel v zadaném formátu.|  
|[COleDataObject::GetGlobalData](#getglobaldata)|Kopíruje data z připojeného objektu OLE data do `HGLOBAL` v zadaném formátu.|  
|[COleDataObject::GetNextFormat](#getnextformat)|Vrátí další formát dat, která je k dispozici.|  
|[COleDataObject::IsDataAvailable](#isdataavailable)|Kontroluje, zda je k dispozici v zadaném formátu data.|  
|[COleDataObject::Release](#release)|Odpojí a uvolní přidruženého `IDataObject` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 `COleDataObject` nemá základní třídu.  
  
 Tyto druhy přenosů dat zahrnují zdroj a cíl. Zdroj dat je implementováno jako objekt [coledatasource –](../../mfc/reference/coledatasource-class.md) třídy. Vždy, když cílová aplikace má data vyřadit v ní nebo se zobrazí výzva k provedení operace vložení ze schránky, objekt `COleDataObject` třídy se musí vytvořit.  
  
 Tato třída umožňuje určit, zda data existuje v zadaném formátu. Můžete také vytvořit výčet dostupných datových formátů nebo zkontrolujte, zda je k dispozici daném formátu a načítají v preferovaném formátu. Načítání objektu lze provést několika různými způsoby, včetně použití [cfile –](../../mfc/reference/cfile-class.md), což je HGLOBAL nebo `STGMEDIUM` struktury.  
  
 Další informace najdete v tématu [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) struktura v sadě Windows SDK.  
  
 Další informace o používání datových objektů ve vaší aplikaci, najdete v článku [datové objekty a zdroje dat (OLE)](../../mfc/data-objects-and-data-sources-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `COleDataObject`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxole.h  
  
##  <a name="attach"></a>  COleDataObject::Attach  
 Voláním této funkce pro přidružení `COleDataObject` objekt s datový objekt OLE.  
  
```  
void Attach(
    LPDATAOBJECT lpDataObject,  
    BOOL bAutoRelease = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *lpDataObject*  
 Odkazuje na datový objekt OLE.  
  
 *bAutoRelease*  
 Hodnota TRUE, pokud datový objekt OLE by měla být uvolněna při `COleDataObject` objekt je zničen; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject) v sadě Windows SDK.  
  
##  <a name="attachclipboard"></a>  COleDataObject::AttachClipboard  
 Voláním této funkce se připojit datový objekt, který je aktuálně ze schránky do `COleDataObject` objektu.  
  
```  
BOOL AttachClipboard();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Volání této funkce zamkne schránky, dokud se neuvolní tímto datovým objektem. Datový objekt vydanou destruktor `COleDataObject`. Další informace najdete v tématu [Modul OpenClipboard](/windows/desktop/api/winuser/nf-winuser-openclipboard) a [Modul CloseClipboard](/windows/desktop/api/winuser/nf-winuser-closeclipboard) v dokumentaci k systému Win32.  
  
##  <a name="beginenumformats"></a>  COleDataObject::BeginEnumFormats  
 Voláním této funkce Příprava následných volání `GetNextFormat` pro načtení z položky seznam datových formátů.  
  
```  
void BeginEnumFormats();
```  
  
### <a name="remarks"></a>Poznámky  
 Po volání `BeginEnumFormats`, je uložen pozici první formát podporovaný tímto datovým objektem. Následná volání `GetNextFormat` projde seznam dostupných formátů datového objektu.  
  
 Chcete-li zkontrolovat dostupnost dat v daném formátu, použijte [COleDataObject::IsDataAvailable](#isdataavailable).  
  
 Další informace najdete v tématu [IDataObject::EnumFormatEtc](/windows/desktop/api/objidl/nf-objidl-idataobject-enumformatetc) v sadě Windows SDK.  
  
##  <a name="coledataobject"></a>  COleDataObject::COleDataObject  
 Vytvoří `COleDataObject` objektu.  
  
```  
COleDataObject();
```  
  
### <a name="remarks"></a>Poznámky  
 Volání [COleDataObject::Attach](#attach) nebo [COleDataObject::AttachClipboard](#attachclipboard) nutné provést před voláním metody jiné `COleDataObject` funkce.  
  
> [!NOTE]
>  Protože jeden z parametrů rutinám přetažení myší je ukazatel `COleDataObject`, není nutné k volání tohoto konstruktoru pro podporu přetažení.  
  
##  <a name="detach"></a>  COleDataObject::Detach  
 Voláním této funkce se odpojit `COleDataObject` objekt z jeho přidružených datový objekt OLE bez datového objektu.  
  
```  
LPDATAOBJECT Detach();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na datový objekt OLE, která byla odpojena.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getdata"></a>  COleDataObject::GetData  
 Voláním této funkce k načtení dat z položky v zadaném formátu.  
  
```  
BOOL GetData(
    CLIPFORMAT cfFormat,  
    LPSTGMEDIUM lpStgMedium,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *cfFormat*  
 Formát, ve kterém má být vrácena data. Tento parametr může být jeden z předdefinovaných formátů schránky nebo hodnoty vrácené nativní Windows [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) funkce.  
  
 *lpStgMedium*  
 Odkazuje [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) struktura, která bude přijímat data.  
  
 *lpFormatEtc*  
 Odkazuje [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktura popisující formát, ve kterém má být vrácena data. Zadejte hodnotu pro tento parametr, pokud chcete zadat informace o dalších formátu nad rámec formátu schránky určeném *cfFormat*. Pokud je hodnota NULL, budou použity výchozí hodnoty pro ostatní pole v `FORMATETC` struktury.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [IDataObject::GetData](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata), [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium), a [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) v sadě Windows SDK.  
  
 Další informace najdete v tématu [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) v sadě Windows SDK.  
  
##  <a name="getfiledata"></a>  COleDataObject::GetFileData  
 Volání této funkce můžete vytvořit `CFile` nebo `CFile`-odvozenému objektu a k načtení dat v zadaném formátu do `CFile` ukazatele.  
  
```  
CFile* GetFileData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *cfFormat*  
 Formát, ve kterém má být vrácena data. Tento parametr může být jeden z předdefinovaných formátů schránky nebo hodnoty vrácené nativní Windows [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) funkce.  
  
 *lpFormatEtc*  
 Odkazuje [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktura popisující formát, ve kterém má být vrácena data. Zadejte hodnotu pro tento parametr, pokud chcete zadat informace o dalších formátu nad rámec formátu schránky určeném *cfFormat*. Pokud je hodnota NULL, budou použity výchozí hodnoty pro ostatní pole v `FORMATETC` struktury.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na novou `CFile` nebo `CFile`-odvozené objekt, který obsahuje data, je-li úspěšné; jinak hodnota NULL.  
  
### <a name="remarks"></a>Poznámky  
 V závislosti na střední jsou data uložená v, může být skutečný typ, na které odkazuje návratová hodnota `CFile`, `CSharedFile`, nebo `COleStreamFile`.  
  
> [!NOTE]
>  `CFile` Volající vlastní objekt, návratová hodnota této funkce. Je odpovědností volajícího, aby **odstranit** `CFile` objektu, a tím zavírání souboru.  
  
 Další informace najdete v tématu [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) v sadě Windows SDK.  
  
 Další informace najdete v tématu [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) v sadě Windows SDK.  
  
##  <a name="getglobaldata"></a>  COleDataObject::GetGlobalData  
 Voláním této funkce se přidělit blok globální paměti a k načtení dat v zadaném formátu do HGLOBAL.  
  
```  
HGLOBAL GetGlobalData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *cfFormat*  
 Formát, ve kterém má být vrácena data. Tento parametr může být jeden z předdefinovaných formátů schránky nebo hodnoty vrácené nativní Windows [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) funkce.  
  
 *lpFormatEtc*  
 Odkazuje [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktura popisující formát, ve kterém má být vrácena data. Zadejte hodnotu pro tento parametr, pokud chcete zadat informace o dalších formátu nad rámec formátu schránky určeném *cfFormat*. Pokud je hodnota NULL, budou použity výchozí hodnoty pro ostatní pole v `FORMATETC` struktury.  
  
### <a name="return-value"></a>Návratová hodnota  
 Obslužná rutina bloku globální paměti obsahující data v případě úspěchu; v opačném případě hodnota NULL.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) v sadě Windows SDK.  
  
 Další informace najdete v tématu [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) v sadě Windows SDK.  
  
##  <a name="getnextformat"></a>  COleDataObject::GetNextFormat  
 Voláním této funkce opakovaně získat všechny formáty, které jsou k dispozici pro načítání dat z položky.  
  
```  
BOOL GetNextFormat(LPFORMATETC lpFormatEtc);
```  
  
### <a name="parameters"></a>Parametry  
 *lpFormatEtc*  
 Odkazuje [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktura, která přijímá informace o formátu při volání funkce vrátí.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud jiný formát je k dispozici. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Po volání [COleDataObject::BeginEnumFormats](#beginenumformats), je uložen pozici první formát podporovaný tímto datovým objektem. Následná volání `GetNextFormat` projde seznam dostupných formátů datového objektu. Pomocí těchto funkcí seznam dostupných formátech.  
  
 Chcete-li zkontrolovat dostupnost daném formátu, zavolejte [COleDataObject::IsDataAvailable](#isdataavailable).  
  
 Další informace najdete v tématu [IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx) v sadě Windows SDK.  
  
##  <a name="isdataavailable"></a>  COleDataObject::IsDataAvailable  
 Voláním této funkce lze zjistit, konkrétní formát je k dispozici pro načítání dat z položky OLE.  
  
```  
BOOL IsDataAvailable(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *cfFormat*  
 Formát dat schránky pro použití ve struktuře odkazované *lpFormatEtc*. Tento parametr může být jeden z předdefinovaných formátů schránky nebo hodnoty vrácené nativní Windows [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) funkce.  
  
 *lpFormatEtc*  
 Odkazuje [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktura popisující požadovaného formátu. Zadejte hodnotu pro tento parametr pouze v případě, že chcete zadat informace o dalších formátu nad rámec formátu schránky určeném *cfFormat*. Pokud je hodnota NULL, budou použity výchozí hodnoty pro ostatní pole v `FORMATETC` struktury.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud jsou k dispozici v zadaném formátu; data jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je užitečná před voláním `GetData`, `GetFileData`, nebo `GetGlobalData`.  
  
 Další informace najdete v tématu [IDataObject::QueryGetData](/windows/desktop/api/objidl/nf-objidl-idataobject-querygetdata) a [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) v sadě Windows SDK.  
  
 Další informace najdete v tématu [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CRichEditView::QueryAcceptData](../../mfc/reference/cricheditview-class.md#queryacceptdata).  
  
##  <a name="release"></a>  COleDataObject::Release  
 Voláním této funkce uvolní vlastnictví [IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject) objektu, která byla dříve přidružená `COleDataObject` objektu.  
  
```  
void Release();
```  
  
### <a name="remarks"></a>Poznámky  
 `IDataObject` Byl přidružen `COleDataObject` voláním `Attach` nebo `AttachClipboard` explicitně nebo rozhraní. Pokud *bAutoRelease* parametr `Attach` má hodnotu FALSE, `IDataObject` objekt nebude uvolněn. V tomto případě je zodpovědná za uvolnění volající `IDataObject` voláním [IUnknown::Release](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release).  
  
## <a name="see-also"></a>Viz také  
 [Ukázky knihovny MFC HIERSVR](../../visual-cpp-samples.md)   
 [Ukázky knihovny MFC OCLIENT](../../visual-cpp-samples.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Coledatasource – třída](../../mfc/reference/coledatasource-class.md)   
 [Coleclientitem – třída](../../mfc/reference/coleclientitem-class.md)   
 [COleServerItem – třída](../../mfc/reference/coleserveritem-class.md)
