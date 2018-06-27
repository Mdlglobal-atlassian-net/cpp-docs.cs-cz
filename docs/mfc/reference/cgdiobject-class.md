---
title: Třída CGdiObject | Microsoft Docs
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
ms.openlocfilehash: eb8cc37396069dc7e0ea53506436b536100bdbb4
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956126"
---
# <a name="cgdiobject-class"></a>CGdiObject – třída
Poskytuje základní třídu pro různé druhy Windows grafické objekty rozhraní GDI zařízení například rastrové obrázky, oblasti, štětce, pera, palety a písem.  
  
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
|[CGdiObject::Attach](#attach)|Připojí do objekt GDI systému Windows `CGdiObject` objektu.|  
|[CGdiObject::CreateStockObject](#createstockobject)|Načte popisovač pro některý z předdefinovaných uložených pera Windows, štětce nebo písem.|  
|[CGdiObject::DeleteObject](#deleteobject)|Objekt Windows GDI připojený k odstranění `CGdiObject` objekt z paměti podle uvolnění všechny úložiště systému přidružená k objektu.|  
|[CGdiObject::DeleteTempMap](#deletetempmap)|Odstraní všechny dočasné `CGdiObject` objekty vytvořené `FromHandle`.|  
|[CGdiObject::Detach](#detach)|Umožňuje odpojit objekt GDI systému Windows z `CGdiObject` objektu a vrací popisovač objektu GDI systému Windows.|  
|[CGdiObject::FromHandle](#fromhandle)|Vrátí ukazatel na `CGdiObject` objekt daný popisovač objektu GDI systému Windows.|  
|[CGdiObject::GetObject](#getobject)|Výplněmi vyrovnávací paměti s daty, která popisuje Windows GDI objekt připojený k `CGdiObject` objektu.|  
|[CGdiObject::GetObjectType](#getobjecttype)|Načte typ objektu GDI.|  
|[CGdiObject::GetSafeHandle](#getsafehandle)|Vrátí `m_hObject` Pokud `this` je `NULL`, v takovém případě `NULL` je vrácen.|  
|[CGdiObject::UnrealizeObject](#unrealizeobject)|Obnoví původ štětce nebo obnoví logické palety.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CGdiObject::operator! =](#operator_neq)|Určuje, zda dva objekty GDI logicky není rovno.|  
|[CGdiObject::operator ==](#operator_eq_eq)|Určuje, jestli jsou dva objekty GDI logicky stejné.|  
|[CGdiObject::operator HGDIOBJ](#operator_hgdiobj)|Načte `HANDLE` k objektu připojené GDI systému Windows.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CGdiObject::m_hObject](#m_hobject)|A `HANDLE` obsahující `HBITMAP`, `HPALETTE`, `HRGN`, `HBRUSH`, `HPEN`, nebo `HFONT` připojen k tomuto objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Nikdy vytvoříte `CGdiObject` přímo. Místo toho vytvoříte objekt z jednoho z jeho odvozené třídy, jako například `CPen` nebo `CBrush`.  
  
 Další informace o `CGdiObject`, najdete v části [grafické objekty](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CGdiObject`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="attach"></a>  CGdiObject::Attach  
 Připojí do objekt GDI systému Windows `CGdiObject` objektu.  
  
```  
BOOL Attach(HGDIOBJ hObject);
```  
  
### <a name="parameters"></a>Parametry  
 *hObject*  
 A `HANDLE` na objekt GDI systému Windows (například `HPEN` nebo `HBRUSH`).  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud připojení úspěšné; jinak 0.  
  
##  <a name="cgdiobject"></a>  CGdiObject::CGdiObject  
 Vytvoří `CGdiObject` objektu.  
  
```  
CGdiObject();
```  
  
### <a name="remarks"></a>Poznámky  
 Nikdy vytvoříte `CGdiObject` přímo. Místo toho vytvoříte objekt z jednoho z jeho odvozené třídy, jako například `CPen` nebo `Cbrush`.  
  
##  <a name="createstockobject"></a>  CGdiObject::CreateStockObject  
 Načte popisovač pro některý z předdefinovaných uložených Windows GDI pera, štětce nebo písem a připojí GDI objekt, který má `CGdiObject` objektu.  
  
```  
BOOL CreateStockObject(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Určení typu objektu uložených potřeby konstanta. V tématu parametr *fnObject* pro [GetStockObject](http://msdn.microsoft.com/library/windows/desktop/dd144925) ve Windows SDK pro popis příslušné hodnoty.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce s jedním z odvozené třídy, která odpovídá typu objektů GDI systému Windows, jako například `CPen` pro pera uložené.  
  
##  <a name="deleteobject"></a>  CGdiObject::DeleteObject  
 Odstraní objekt připojené GDI systému Windows z paměti podle uvolnění všechny úložiště systému přidružená k objektu GDI systému Windows.  
  
```  
BOOL DeleteObject();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud objekt GDI byla úspěšně odstraněna; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Úložiště přidružený k `CGdiObject` objekt nemá vliv toto volání. Aplikace by neměla volat `DeleteObject` na `CGdiObject` objekt, který je aktuálně vybraný v kontextu zařízení.  
  
 Při odstranění štětce vzor rastrového obrázku přidružený stopy se neodstraní. Bitmapy musí odstranit samostatně.  
  
##  <a name="deletetempmap"></a>  CGdiObject::DeleteTempMap  
 Volá se automaticky `CWinApp` doby nečinnosti obslužnou rutinu, `DeleteTempMap` odstraní všechny dočasné `CGdiObject` objekty vytvořené `FromHandle`.  
  
```  
static void PASCAL DeleteTempMap();
```  
  
### <a name="remarks"></a>Poznámky  
 `DeleteTempMap` Umožňuje odpojit objekt Windows GDI připojen do dočasného `CGdiObject` objekt před odstraněním `CGdiObject` objektu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#175](../../mfc/codesnippet/cpp/cgdiobject-class_1.cpp)]  
  
##  <a name="detach"></a>  CGdiObject::Detach  
 Umožňuje odpojit objekt GDI systému Windows z `CGdiObject` objektu a vrací popisovač objektu GDI systému Windows.  
  
```  
HGDIOBJ Detach();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `HANDLE` do Windows GDI objekt odpojit; jinak hodnota **NULL** Pokud žádný objekt GDI je připojen.  
  
##  <a name="fromhandle"></a>  CGdiObject::FromHandle  
 Vrátí ukazatel na `CGdiObject` objekt daný popisovač objektu GDI systému Windows.  
  
```  
static CGdiObject* PASCAL FromHandle(HGDIOBJ hObject);
```  
  
### <a name="parameters"></a>Parametry  
 *hObject*  
 A `HANDLE` na objekt GDI systému Windows.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na `CGdiObject` , může být v dočasné nebo trvalé.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `CGdiObject` objekt není už připojený k objektu GDI systému Windows, dočasného `CGdiObject` objekt se vytvoří a připojené.  
  
 Toto dočasný `CGdiObject` objektu je platná pouze až po příštím aplikace má čas nečinnosti v jeho událostí ve smyčce, po kterém se odstraní všechny dočasné grafické objekty. Jinými slovy to je, že dočasný objekt platí pouze při zpracování zprávy jeden interval.  
  
##  <a name="getobject"></a>  CGdiObject::GetObject  
 Doplní vyrovnávací paměť s daty, která definuje zadaný objekt.  
  
```  
int GetObject(
    int nCount,  
    LPVOID lpObject) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nCount*  
 Určuje počet bajtů, které chcete zkopírovat do *lpObject* vyrovnávací paměti.  
  
 *lpObject*  
 Body do vyrovnávací paměti zadanou uživatelem, který je k získání požadovaných informací.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet bajtů načtených; v opačném případě dojde k 0, pokud se chyba.  
  
### <a name="remarks"></a>Poznámky  
 Funkce načte datová struktura, jejíž typ závisí na typu grafického objektu, jak je ukázáno v následujícím seznamu:  
  
|Objekt|Typ vyrovnávací paměti|  
|------------|-----------------|  
|`CPen`|[LOGPEN –](../../mfc/reference/logpen-structure.md)|  
|`CBrush`|[LOGBRUSH –](../../mfc/reference/logbrush-structure.md)|  
|`CFont`|[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)|  
|`CBitmap`|[RASTROVÝ OBRÁZEK](../../mfc/reference/bitmap-structure.md)|  
|`CPalette`|**WORD**|  
|`CRgn`|Nepodporováno|  
  
 Pokud je objekt `CBitmap` objekt, `GetObject` vrátí pouze šířky, výšky a informace o formátu barva bitmapy. Skutečné službu bits můžete načíst pomocí [CBitmap::GetBitmapBits](../../mfc/reference/cbitmap-class.md#getbitmapbits).  
  
 Pokud je objekt `CPalette` objekt, `GetObject` načte **WORD** určující počet položek v paletě. Funkce nenačítá [LOGPALETTE](http://msdn.microsoft.com/library/windows/desktop/dd145040) struktura, která definuje paletě. Aplikaci můžete získat informace o palety voláním [CPalette::GetPaletteEntries](../../mfc/reference/cpalette-class.md#getpaletteentries).  
  
##  <a name="getobjecttype"></a>  CGdiObject::GetObjectType  
 Načte typ objektu GDI.  
  
```  
UINT GetObjectType() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Typ objektu, pokud bylo úspěšné; jinak 0. Hodnota může být jeden z následujících akcí:  
  
- **OBJ_BITMAP** rastrového obrázku  
  
- **OBJ_BRUSH** štětce  
  
- **OBJ_FONT** písma  
  
- **OBJ_PAL** palety  
  
- **OBJ_PEN** pera  
  
- **OBJ_EXTPEN** rozšířené pera  
  
- **OBJ_REGION** oblast  
  
- **OBJ_DC** kontextu zařízení  
  
- **OBJ_MEMDC** paměti kontextu zařízení  
  
- **OBJ_METAFILE** Metafile  
  
- **OBJ_METADC** Metafile kontextu zařízení  
  
- **OBJ_ENHMETAFILE** Enhanced metafile  
  
- **OBJ_ENHMETADC** Enhanced metafile kontextu zařízení  
  
##  <a name="getsafehandle"></a>  CGdiObject::GetSafeHandle  
 Vrátí `m_hObject` Pokud **to** je **NULL**, v takovém případě **NULL** je vrácen.  
  
```  
HGDIOBJ GetSafeHandle() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `HANDLE` připojené Windows GDI objektu; v opačném případě **NULL** Pokud je připojen žádný objekt.  
  
### <a name="remarks"></a>Poznámky  
 To je součástí zlepší obecné popisovač rozhraní a je užitečné, když **NULL** je platný nebo speciální hodnotu pro popisovač.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CWnd::IsWindowEnabled](../../mfc/reference/cwnd-class.md#iswindowenabled).  
  
##  <a name="m_hobject"></a>  CGdiObject::m_hObject  
 A `HANDLE` obsahující `HBITMAP`, **HRGN**, `HBRUSH`, `HPEN`, `HPALETTE`, nebo **HFONT** připojen k tomuto objektu.  
  
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
 Ukazatele na existující `CGdiObject`.  
  
### <a name="remarks"></a>Poznámky  
 Určuje, zda GDI objekt na levé straně není rovno GDI objekt na pravé straně.  
  
##  <a name="operator_eq_eq"></a>  CGdiObject::operator ==  
 Určuje, jestli jsou dva objekty GDI logicky stejné.  
  
```  
BOOL operator==(const CGdiObject& obj) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *obj*  
 Odkaz na existující `CGdiObject`.  
  
### <a name="remarks"></a>Poznámky  
 Určuje, zda GDI objekt na levé straně stejný GDI objekt na pravé straně.  
  
##  <a name="operator_hgdiobj"></a>  CGdiObject::operator HGDIOBJ  
 Načte `HANDLE` připojené Windows GDI objektu; v opačném případě **NULL** Pokud je připojen žádný objekt.  
  
```  
operator HGDIOBJ() const;  
```  
  
##  <a name="unrealizeobject"></a>  CGdiObject::UnrealizeObject  
 Obnoví původ štětce nebo obnoví logické palety.  
  
```  
BOOL UnrealizeObject();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Při `UnrealizeObject` členských funkcí `CGdiObject` třídy, se by měla být volána pouze na `CBrush` nebo `CPalette` objekty.  
  
 Pro `CBrush` objekty, `UnrealizeObject` určí, že systém resetovat původ dané štětce příštím je vybrán v kontextu zařízení. Pokud je objekt `CPalette` objekt, `UnrealizeObject` určí, že systém si uvědomí palety, jako kdyby nebyla dříve realizováno. Při příštím aplikace volá [CDC::RealizePalette](../../mfc/reference/cdc-class.md#realizepalette) funkce pro zadaný palety systému úplně znovu mapuje logické palety na paletu systému.  
  
 `UnrealizeObject` Funkce by neměla být použita s uložených objekty. `UnrealizeObject` Funkce musí být volána při každé nové počátek štětce nastavena (prostřednictvím [CDC::SetBrushOrg](../../mfc/reference/cdc-class.md#setbrushorg) funkce). `UnrealizeObject` Funkce nesmí být volána pro aktuálně vybrané štětce nebo aktuálně vybrané paletu jakýkoliv kontext zobrazení.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CBitmap – třída](../../mfc/reference/cbitmap-class.md)   
 [CBrush – třída](../../mfc/reference/cbrush-class.md)   
 [CFont – třída](../../mfc/reference/cfont-class.md)   
 [CPalette – třída](../../mfc/reference/cpalette-class.md)   
 [CPen – třída](../../mfc/reference/cpen-class.md)   
 [CRgn – třída](../../mfc/reference/crgn-class.md)
