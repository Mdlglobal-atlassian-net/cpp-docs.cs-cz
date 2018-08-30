---
title: Cgdiobject – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CGdiObject
- AFXWIN/CGdiObject
- AFXWIN/CGdiObject::CGdiObject
- AFXWIN/CGdiObject::Attach
- AFXWIN/CGdiObject::CreateStockObject
- AFXWIN/CGdiObject::DeleteObject
- AFXWIN/CGdiObject::DeleteTempMap
- AFXWIN/CGdiObject::Detach
- AFXWIN/CGdiObject::FromHandle
- AFXWIN/CGdiObject::GetObject
- AFXWIN/CGdiObject::GetObjectType
- AFXWIN/CGdiObject::GetSafeHandle
- AFXWIN/CGdiObject::UnrealizeObject
- AFXWIN/CGdiObject::m_hObject
dev_langs:
- C++
helpviewer_keywords:
- CGdiObject [MFC], CGdiObject
- CGdiObject [MFC], Attach
- CGdiObject [MFC], CreateStockObject
- CGdiObject [MFC], DeleteObject
- CGdiObject [MFC], DeleteTempMap
- CGdiObject [MFC], Detach
- CGdiObject [MFC], FromHandle
- CGdiObject [MFC], GetObject
- CGdiObject [MFC], GetObjectType
- CGdiObject [MFC], GetSafeHandle
- CGdiObject [MFC], UnrealizeObject
- CGdiObject [MFC], m_hObject
ms.assetid: 1cba3ba5-3d49-4e43-8293-209299f2f6f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e72c7ea788085f25dc2a4ec1b2f8682df9e20b25
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209124"
---
# <a name="cgdiobject-class"></a>Cgdiobject – třída
Poskytuje základní třídu pro různé druhy grafiky Windows objekty rozhraní GDI systému zařízení, jako je například rastrové obrázky, oblasti, štětce, pera, palety a písma.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CGdiObject : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CGdiObject::CGdiObject](#cgdiobject)|Vytvoří `CGdiObject` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CGdiObject::Attach](#attach)|Připojí objektů Windows GDI do `CGdiObject` objektu.|  
|[CGdiObject::CreateStockObject](#createstockobject)|Načte popisovač na jednu z předdefinovaných uložených pera Windows, štětce nebo písma.|  
|[CGdiObject::DeleteObject](#deleteobject)|Odstraní objektů Windows GDI připojené k `CGdiObject` objekt z paměti uvolněním veškeré součásti úložiště systémové přidružená k objektu.|  
|[CGdiObject::DeleteTempMap](#deletetempmap)|Odstraní všechny dočasné `CGdiObject` objekty vytvořené `FromHandle`.|  
|[CGdiObject::Detach](#detach)|Odpojí objektů Windows GDI z `CGdiObject` objekt a vrátí popisovač do objektů Windows GDI.|  
|[CGdiObject::FromHandle](#fromhandle)|Vrací ukazatel `CGdiObject` objekt daný popisovač objektů Windows GDI.|  
|[CGdiObject::GetObject](#getobject)|Výplně vyrovnávací paměti s daty, která popisuje objektů Windows GDI připojené k `CGdiObject` objektu.|  
|[CGdiObject::GetObjectType](#getobjecttype)|Získá typ objektu GDI.|  
|[CGdiObject::GetSafeHandle](#getsafehandle)|Vrátí `m_hObject` Pokud **to** má hodnotu NULL, ve kterém je vrácena hodnota case NULL.|  
|[CGdiObject::UnrealizeObject](#unrealizeobject)|Obnoví původní štětce nebo obnoví logickou paletu.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CGdiObject::operator! =](#operator_neq)|Určuje, zda dva objekty GDI logicky není rovno.|  
|[CGdiObject::operator ==](#operator_eq_eq)|Určuje, jestli jsou dva objekty GDI logicky stejné.|  
|[CGdiObject::operator HGDIOBJ](#operator_hgdiobj)|Načte POPISOVAČ připojených objektů Windows GDI.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CGdiObject::m_hObject](#m_hobject)|POPISOVAČ obsahující HBITMAP HPALETTE, HRGN, HBRUSH, HPEN nebo HFONT připojené k tomuto objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Nikdy nevytvářejte `CGdiObject` přímo. Místo toho vytvoření objektu z jednoho z jeho odvozených tříd, jako například `CPen` nebo `CBrush`.  
  
 Další informace o `CGdiObject`, naleznete v tématu [grafické objekty](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 `CGdiObject`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="attach"></a>  CGdiObject::Attach  
 Připojí objektů Windows GDI do `CGdiObject` objektu.  
  
```  
BOOL Attach(HGDIOBJ hObject);
```  
  
### <a name="parameters"></a>Parametry  
 *hObject*  
 POPISOVAČ pro objekt Windows GDI (například HPEN nebo HBRUSH).  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšné; přílohy jinak 0.  
  
##  <a name="cgdiobject"></a>  CGdiObject::CGdiObject  
 Vytvoří `CGdiObject` objektu.  
  
```  
CGdiObject();
```  
  
### <a name="remarks"></a>Poznámky  
 Nikdy nevytvářejte `CGdiObject` přímo. Místo toho vytvoření objektu z jednoho z jeho odvozených tříd, jako například `CPen` nebo `Cbrush`.  
  
##  <a name="createstockobject"></a>  CGdiObject::CreateStockObject  
 Načte popisovač na jednu z předdefinovaných uložených Windows GDI pera, štětce nebo písma a připojí rozhraní GDI objekt, který má `CGdiObject` objektu.  
  
```  
BOOL CreateStockObject(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Konstanta určující typ požadovaného skladový objekt. Zobrazit parametr *fnObject* pro [GetStockObject](/windows/desktop/api/wingdi/nf-wingdi-getstockobject) v sadě Windows SDK pro popis příslušné hodnoty.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce s jednou z odvozené třídy, která odpovídá typ objektů Windows GDI, jako například `CPen` uložených pera.  
  
##  <a name="deleteobject"></a>  CGdiObject::DeleteObject  
 Odstraní připojených objektů Windows GDI z paměti uvolněním přidružené objektů Windows GDI všechna úložiště v systému.  
  
```  
BOOL DeleteObject();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud se úspěšně odstranil objekt rozhraní GDI; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Úložiště přidružené k `CGdiObject` objekt nemá vliv tohoto volání. Aplikace by neměl volat `DeleteObject` na `CGdiObject` objekt, který je aktuálně vybrána v kontextu zařízení.  
  
 Při odstranění štětce vzor rastrový obrázek přidružený k štětce není odstraněn. Rastrový obrázek dají odstranit samostatně.  
  
##  <a name="deletetempmap"></a>  CGdiObject::DeleteTempMap  
 Volá se automaticky `CWinApp` doby nečinnosti obslužnou rutinu, `DeleteTempMap` odstraní všechny dočasné `CGdiObject` objekty vytvořené `FromHandle`.  
  
```  
static void PASCAL DeleteTempMap();
```  
  
### <a name="remarks"></a>Poznámky  
 `DeleteTempMap` Odpojí objektů Windows GDI připojené do dočasného `CGdiObject` objektu před odstraněním `CGdiObject` objektu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#175](../../mfc/codesnippet/cpp/cgdiobject-class_1.cpp)]  
  
##  <a name="detach"></a>  CGdiObject::Detach  
 Odpojí objektů Windows GDI z `CGdiObject` objekt a vrátí popisovač do objektů Windows GDI.  
  
```  
HGDIOBJ Detach();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `HANDLE` Windows GDI na objekt odpojit; v opačném případě hodnota NULL, pokud je připojen žádný objekt GDI.  
  
##  <a name="fromhandle"></a>  CGdiObject::FromHandle  
 Vrací ukazatel `CGdiObject` objekt daný popisovač objektů Windows GDI.  
  
```  
static CGdiObject* PASCAL FromHandle(HGDIOBJ hObject);
```  
  
### <a name="parameters"></a>Parametry  
 *hObject*  
 POPISOVAČ pro objekt Windows GDI.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `CGdiObject` , které můžou být dočasné nebo trvalé.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `CGdiObject` objekt už není připojen ke objektů Windows GDI, dočasný `CGdiObject` objekt se vytvoří a připojí.  
  
 Tento dočasný `CGdiObject` objektu je platná pouze až do příštího aplikace má čas nečinnosti v jeho smyčkou událostí, po kterém se odstraní všechny dočasné grafických objektů. Jinými slovy to je, že dočasný objekt platí pouze při zpracování zprávy jedno okno.  
  
##  <a name="getobject"></a>  CGdiObject::GetObject  
 Naplní vyrovnávací paměť s daty, která definuje zadaného objektu.  
  
```  
int GetObject(
    int nCount,  
    LPVOID lpObject) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nCount*  
 Určuje počet bajtů, které mají zkopírovat do *lpObject* vyrovnávací paměti.  
  
 *lpObject*  
 Odkazuje na vyrovnávací paměť uživatelem zadané, která je k získání požadovaných informací.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet bajtů načtených; v opačném případě dojde k 0, pokud chybu.  
  
### <a name="remarks"></a>Poznámky  
 Funkce načte do datové struktury, jehož typ závisí na typu grafický objekt, jak je znázorněno v následujícím seznamu:  
  
|Objekt|Typ vyrovnávací paměti|  
|------------|-----------------|  
|`CPen`|[LOGPEN –](../../mfc/reference/logpen-structure.md)|  
|`CBrush`|[LOGBRUSH –](../../mfc/reference/logbrush-structure.md)|  
|`CFont`|[LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)|  
|`CBitmap`|[RASTROVÝ OBRÁZEK](../../mfc/reference/bitmap-structure.md)|  
|`CPalette`|WORD|  
|`CRgn`|Nepodporováno|  
  
 Pokud je objekt `CBitmap` objektu, `GetObject` vrátí pouze šířku, výšku a informace o formátu barvy rastrového obrázku. Skutečné službu bits můžete načíst pomocí [CBitmap::GetBitmapBits](../../mfc/reference/cbitmap-class.md#getbitmapbits).  
  
 Pokud je objekt `CPalette` objektu, `GetObject` načte slova, která určuje počet položek, které na paletě. Funkce nenačte [LOGPALETTE](/windows/desktop/api/wingdi/ns-wingdi-taglogpalette) strukturu, která definuje paletu. Aplikaci můžete získat informace o palety voláním [CPalette::GetPaletteEntries](../../mfc/reference/cpalette-class.md#getpaletteentries).  
  
##  <a name="getobjecttype"></a>  CGdiObject::GetObjectType  
 Získá typ objektu GDI.  
  
```  
UINT GetObjectType() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Typ objektu, v případě úspěchu; jinak 0. Hodnota může být jeden z následujících akcí:  
  
- OBJ_BITMAP rastrový obrázek  
  
- OBJ_BRUSH štětce  
  
- OBJ_FONT písma  
  
- OBJ_PAL palety  
  
- OBJ_PEN pera  
  
- Rozšířené OBJ_EXTPEN pera  
  
- OBJ_REGION oblasti  
  
- Kontext zařízení OBJ_DC  
  
- Kontext zařízení OBJ_MEMDC paměti  
  
- OBJ_METAFILE metasoubor  
  
- Kontextu zařízení metasouboru OBJ_METADC  
  
- OBJ_ENHMETAFILE rozšířený metasoubor  
  
- Kontext zařízení Enhanced metafile OBJ_ENHMETADC  
  
##  <a name="getsafehandle"></a>  CGdiObject::GetSafeHandle  
 Vrátí `m_hObject` Pokud **to** má hodnotu NULL, ve kterém je vrácena hodnota case NULL.  
  
```  
HGDIOBJ GetSafeHandle() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 POPISOVAČ připojených objektů Windows GDI; jinak hodnota NULL, pokud je připojen žádný objekt.  
  
### <a name="remarks"></a>Poznámky  
 To je součástí rozhraní paradigma obecné popisovač a je užitečné, když hodnota NULL je platné nebo zvláštní hodnota pro popisovač.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CWnd::IsWindowEnabled](../../mfc/reference/cwnd-class.md#iswindowenabled).  
  
##  <a name="m_hobject"></a>  CGdiObject::m_hObject  
 POPISOVAČ obsahující HBITMAP HRGN, HBRUSH, HPEN, HPALETTE nebo HFONT připojené k tomuto objektu.  
  
```  
HGDIOBJ m_hObject;  
```  
  
##  <a name="operator_neq"></a>  CGdiObject::operator! =  
 Určuje, zda dva objekty GDI logicky není rovno.  
  
```  
BOOL operator!=(const CGdiObject& obj) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *obj*  
 Ukazatel na existující `CGdiObject`.  
  
### <a name="remarks"></a>Poznámky  
 Určuje, zda objekt rozhraní GDI na levé straně není roven objektu GDI na pravé straně.  
  
##  <a name="operator_eq_eq"></a>  CGdiObject::operator ==  
 Určuje, jestli jsou dva objekty GDI logicky stejné.  
  
```  
BOOL operator==(const CGdiObject& obj) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *obj*  
 Odkaz na existující `CGdiObject`.  
  
### <a name="remarks"></a>Poznámky  
 Určuje, zda je objekt rozhraní GDI na levé straně stejný GDI objekt na pravé straně.  
  
##  <a name="operator_hgdiobj"></a>  CGdiObject::operator HGDIOBJ  
 Načte POPISOVAČ připojených objektů Windows GDI; jinak hodnota NULL, pokud je připojen žádný objekt.  
  
```  
operator HGDIOBJ() const;  
```  
  
##  <a name="unrealizeobject"></a>  CGdiObject::UnrealizeObject  
 Obnoví původní štětce nebo obnoví logickou paletu.  
  
```  
BOOL UnrealizeObject();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Zatímco `UnrealizeObject` je členská funkce `CGdiObject` třídy, to by mělo být vyvoláno pouze na `CBrush` nebo `CPalette` objekty.  
  
 Pro `CBrush` objekty, `UnrealizeObject` určí, že systém resetovat původu dané štětce příště, vybere se do kontextu zařízení. Pokud je objekt `CPalette` objektu, `UnrealizeObject` určí, že systém pro realizaci paletu, jakoby nebyly dříve realizovat. Aplikace volá při příštím [CDC::RealizePalette](../../mfc/reference/cdc-class.md#realizepalette) funkce pro zadaný paletu systému úplně změní logickou paletu na paletě systému.  
  
 `UnrealizeObject` Funkce by neměla být použita s uložených objektů. `UnrealizeObject` Funkce musí být volána pokaždé, když je nastavena nová původu štětce (prostřednictvím [CDC::SetBrushOrg](../../mfc/reference/cdc-class.md#setbrushorg) funkce). `UnrealizeObject` Funkce nesmí být volána pro aktuálně vybrané štětce nebo aktuálně vybraného paletu jakýkoli kontext zobrazení.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Cbitmap – třída](../../mfc/reference/cbitmap-class.md)   
 [Cbrush – třída](../../mfc/reference/cbrush-class.md)   
 [Cfont – třída](../../mfc/reference/cfont-class.md)   
 [Cpalette – třída](../../mfc/reference/cpalette-class.md)   
 [Cpen – třída](../../mfc/reference/cpen-class.md)   
 [CRgn – třída](../../mfc/reference/crgn-class.md)
