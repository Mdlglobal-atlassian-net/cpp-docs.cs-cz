---
title: Třída COleDataObject | Microsoft Docs
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
ms.openlocfilehash: e9cd159597440dfb55bbe8abe147623096cdf449
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33374507"
---
# <a name="coledataobject-class"></a>COleDataObject – třída
Používá se v přenosech souborů pro načítání dat v různých formátech ze schránky, prostřednictvím přetažení, nebo z vložené položky OLE.  
  
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
|[COleDataObject::Attach](#attach)|Připojí zadaný objekt OLE dat na `COleDataObject`.|  
|[COleDataObject::AttachClipboard](#attachclipboard)|Připojí datový objekt, který je do schránky.|  
|[COleDataObject::BeginEnumFormats](#beginenumformats)|Připraví pro jednu nebo více dalších `GetNextFormat` volání.|  
|[COleDataObject::Detach](#detach)|Umožňuje odpojit přidruženého `IDataObject` objektu.|  
|[COleDataObject::GetData](#getdata)|Kopíruje data z připojených datový objekt OLE v zadaném formátu.|  
|[COleDataObject::GetFileData](#getfiledata)|Zkopíruje data z objektu připojené OLE dat do `CFile` ukazatele v zadaném formátu.|  
|[COleDataObject::GetGlobalData](#getglobaldata)|Zkopíruje data z připojených datový objekt OLE do `HGLOBAL` v zadaném formátu.|  
|[COleDataObject::GetNextFormat](#getnextformat)|Vrací další formát dat, která je k dispozici.|  
|[COleDataObject::IsDataAvailable](#isdataavailable)|Kontroluje, zda jsou k dispozici v zadaném formátu data.|  
|[COleDataObject::Release](#release)|Umožňuje odpojit a uvolní přidruženého `IDataObject` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 `COleDataObject` nemá základní třídu.  
  
 Tyto typy přenosů dat patří zdroj a cíl. Zdroj dat je implementovaný jako objekt [coledatasource –](../../mfc/reference/coledatasource-class.md) třídy. Vždy, když cílová aplikace obsahuje data vyřadit v ní nebo se zobrazí výzva k provedení operace vložte ze schránky, objekt `COleDataObject` musí vytvořit třídu.  
  
 Tato třída umožňuje určit, zda data existuje v zadaném formátu. Můžete také vytvořit výčet formáty dostupných dat nebo zkontrolujte, zda daný formát je k dispozici a následně načíst data ve formátu upřednostňované. Načtení objektu lze provést několika různými způsoby, včetně použití [cfile –](../../mfc/reference/cfile-class.md), `HGLOBAL`, nebo **STGMEDIUM** struktury.  
  
 Další informace najdete v tématu [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) struktura ve Windows SDK.  
  
 Další informace o použití datových objektů v aplikaci, najdete v článku [datové objekty a zdroje dat (OLE)](../../mfc/data-objects-and-data-sources-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `COleDataObject`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxole.h  
  
##  <a name="attach"></a>  COleDataObject::Attach  
 Volání této funkce pro přidružení `COleDataObject` objektu s objektem dat OLE.  
  
```  
void Attach(
    LPDATAOBJECT lpDataObject,  
    BOOL bAutoRelease = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *lpDataObject*  
 Odkazuje na objekt dat OLE.  
  
 `bAutoRelease`  
 **Hodnota TRUE,** Pokud OLE datový objekt musí být uvolněna při `COleDataObject` objekt je zničení; jinak hodnota **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421) ve Windows SDK.  
  
##  <a name="attachclipboard"></a>  COleDataObject::AttachClipboard  
 Volání této funkce připojit datový objekt, který je aktuálně ze schránky do `COleDataObject` objektu.  
  
```  
BOOL AttachClipboard();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Volání této funkce zamkne schránky, dokud tento objekt dat vydání. V destruktoru pro vydání datový objekt `COleDataObject`. Další informace najdete v tématu [Modul OpenClipboard](http://msdn.microsoft.com/library/windows/desktop/ms649048) a [Modul CloseClipboard](http://msdn.microsoft.com/library/windows/desktop/ms649035) v dokumentaci Win32.  
  
##  <a name="beginenumformats"></a>  COleDataObject::BeginEnumFormats  
 Volání této funkce připravte následující volání `GetNextFormat` pro načtení seznamu formáty dat z položky.  
  
```  
void BeginEnumFormats();
```  
  
### <a name="remarks"></a>Poznámky  
 Po volání `BeginEnumFormats`, je uložen pozice první formát nepodporuje tento datový objekt. Následná volání `GetNextFormat` se vytvořit výčet seznamu dostupných formátů v datový objekt.  
  
 Chcete-li zkontrolovat dostupnost data v daném formátu, použijte [COleDataObject::IsDataAvailable](#isdataavailable).  
  
 Další informace najdete v tématu [IDataObject::EnumFormatEtc](http://msdn.microsoft.com/library/windows/desktop/ms683979) ve Windows SDK.  
  
##  <a name="coledataobject"></a>  COleDataObject::COleDataObject  
 Vytvoří `COleDataObject` objektu.  
  
```  
COleDataObject();
```  
  
### <a name="remarks"></a>Poznámky  
 Volání [COleDataObject::Attach](#attach) nebo [COleDataObject::AttachClipboard](#attachclipboard) musí být provedeny před voláním jiné `COleDataObject` funkce.  
  
> [!NOTE]
>  Protože jeden z parametrů na obslužné rutiny a přetažení ukazatele na `COleDataObject`, není nutné volat tento konstruktor pro podporu přetažení.  
  
##  <a name="detach"></a>  COleDataObject::Detach  
 Volání této funkce se odpojit `COleDataObject` objekt z jeho přidružených datový objekt OLE bez uvolnění. datový objekt.  
  
```  
LPDATAOBJECT Detach();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na datový objekt OLE, která byla odpojena.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getdata"></a>  COleDataObject::GetData  
 Volání této funkce k načtení dat z položky v zadaném formátu.  
  
```  
BOOL GetData(
    CLIPFORMAT cfFormat,  
    LPSTGMEDIUM lpStgMedium,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `cfFormat`  
 Formát, ve kterém má být vrácen data. Tento parametr může být jeden z předdefinovaných formátů schránky nebo hodnoty vrácené nativní Windows [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) funkce.  
  
 `lpStgMedium`  
 Odkazuje na [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) struktura, která bude přijímat data.  
  
 `lpFormatEtc`  
 Odkazuje na [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura popisující formát, ve kterém má být vrácen data. Zadejte hodnotu pro tento parametr, pokud chcete zadat informace o dalších formátu nad rámec formát schránky určeného `cfFormat`. Pokud je **NULL**, použijí se výchozí hodnoty pro v ostatních polích **FORMATETC** struktura.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [IDataObject::GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431), [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812), a [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) ve Windows SDK.  
  
 Další informace najdete v tématu [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) ve Windows SDK.  
  
##  <a name="getfiledata"></a>  COleDataObject::GetFileData  
 Volání této funkce můžete vytvořit `CFile` nebo `CFile`-odvozené objektu a k načítání dat v zadaném formátu do `CFile` ukazatel.  
  
```  
CFile* GetFileData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `cfFormat`  
 Formát, ve kterém má být vrácen data. Tento parametr může být jeden z předdefinovaných formátů schránky nebo hodnoty vrácené nativní Windows [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) funkce.  
  
 `lpFormatEtc`  
 Odkazuje na [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura popisující formát, ve kterém má být vrácen data. Zadejte hodnotu pro tento parametr, pokud chcete zadat informace o dalších formátu nad rámec formát schránky určeného `cfFormat`. Pokud je **NULL**, použijí se výchozí hodnoty pro v ostatních polích **FORMATETC** struktura.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nové `CFile` nebo `CFile`-odvozené objekt obsahující data, pokud úspěšná, jinak hodnota **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 V závislosti na médiu, jsou data uložená v, může být skutečný typ ukazuje návratovou hodnotu `CFile`, `CSharedFile`, nebo `COleStreamFile`.  
  
> [!NOTE]
>  `CFile` Vlastníkem objektu přistupují návratovou hodnotu této funkce je volající. Je zodpovědností volajícího, aby **odstranit** `CFile` objekt, a tím zavírání souboru.  
  
 Další informace najdete v tématu [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) ve Windows SDK.  
  
 Další informace najdete v tématu [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) ve Windows SDK.  
  
##  <a name="getglobaldata"></a>  COleDataObject::GetGlobalData  
 Volání této funkce přidělit globální paměť bloku a k načítání dat v zadaném formátu do `HGLOBAL`.  
  
```  
HGLOBAL GetGlobalData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `cfFormat`  
 Formát, ve kterém má být vrácen data. Tento parametr může být jeden z předdefinovaných formátů schránky nebo hodnoty vrácené nativní Windows [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) funkce.  
  
 `lpFormatEtc`  
 Odkazuje na [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura popisující formát, ve kterém má být vrácen data. Zadejte hodnotu pro tento parametr, pokud chcete zadat informace o dalších formátu nad rámec formát schránky určeného `cfFormat`. Pokud je **NULL**, použijí se výchozí hodnoty pro v ostatních polích **FORMATETC** struktura.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač globální paměť bloku obsahující data v případě úspěšného; v opačném případě **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) ve Windows SDK.  
  
 Další informace najdete v tématu [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) ve Windows SDK.  
  
##  <a name="getnextformat"></a>  COleDataObject::GetNextFormat  
 Volání této funkce opakovaně k získání všechny formáty, které jsou k dispozici pro načítání dat z položky.  
  
```  
BOOL GetNextFormat(LPFORMATETC lpFormatEtc);
```  
  
### <a name="parameters"></a>Parametry  
 `lpFormatEtc`  
 Odkazuje na [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura, která přijímá informace o formátu při volání funkce vrátí.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud jiný formát je k dispozici. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Po volání [COleDataObject::BeginEnumFormats](#beginenumformats), je uložen pozice první formát nepodporuje tento datový objekt. Následná volání `GetNextFormat` se vytvořit výčet seznamu dostupných formátů v datový objekt. Tyto funkce použijte k zobrazení seznamu dostupných formátů.  
  
 Chcete-li zkontrolovat dostupnost dané formátu, volejte [COleDataObject::IsDataAvailable](#isdataavailable).  
  
 Další informace najdete v tématu [IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx) ve Windows SDK.  
  
##  <a name="isdataavailable"></a>  COleDataObject::IsDataAvailable  
 Volání této funkce lze zjistit konkrétní formát je k dispozici pro načítání dat z položky OLE.  
  
```  
BOOL IsDataAvailable(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `cfFormat`  
 Formát dat schránky pro použití ve struktuře na kterou odkazuje `lpFormatEtc`. Tento parametr může být jeden z předdefinovaných formátů schránky nebo hodnoty vrácené nativní Windows [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) funkce.  
  
 `lpFormatEtc`  
 Odkazuje na [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura popisující formát potřeby. Zadejte hodnotu tohoto parametru, pouze v případě, že chcete zadat informace o dalších formátu nad rámec formát schránky určeného `cfFormat`. Pokud je **NULL**, použijí se výchozí hodnoty pro v ostatních polích **FORMATETC** struktura.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud jsou k dispozici v zadaném formátu; data jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je užitečná před voláním `GetData`, `GetFileData`, nebo `GetGlobalData`.  
  
 Další informace najdete v tématu [IDataObject::QueryGetData](http://msdn.microsoft.com/library/windows/desktop/ms680637) a [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) ve Windows SDK.  
  
 Další informace najdete v tématu [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CRichEditView::QueryAcceptData](../../mfc/reference/cricheditview-class.md#queryacceptdata).  
  
##  <a name="release"></a>  COleDataObject::Release  
 Volání této funkce k uvolnění vlastnictví [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421) objekt, který byl dříve přidružen `COleDataObject` objektu.  
  
```  
void Release();
```  
  
### <a name="remarks"></a>Poznámky  
 `IDataObject` Byl přidružen `COleDataObject` voláním **Attach** nebo `AttachClipboard` explicitně nebo rozhraní. Pokud `bAutoRelease` parametr **Attach** je **FALSE**, `IDataObject` nebude uvolnění objektu. V takovém případě volající zodpovídá za vydání `IDataObject` voláním [IUnknown::Release](http://msdn.microsoft.com/library/windows/desktop/ms682317).  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC HIERSVR](../../visual-cpp-samples.md)   
 [Ukázka MFC OCLIENT](../../visual-cpp-samples.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Coledatasource – třída](../../mfc/reference/coledatasource-class.md)   
 [COleClientItem – třída](../../mfc/reference/coleclientitem-class.md)   
 [COleServerItem – třída](../../mfc/reference/coleserveritem-class.md)
