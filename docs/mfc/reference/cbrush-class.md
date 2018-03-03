---
title: "CBrush – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CBrush
- AFXWIN/CBrush
- AFXWIN/CBrush::CBrush
- AFXWIN/CBrush::CreateBrushIndirect
- AFXWIN/CBrush::CreateDIBPatternBrush
- AFXWIN/CBrush::CreateHatchBrush
- AFXWIN/CBrush::CreatePatternBrush
- AFXWIN/CBrush::CreateSolidBrush
- AFXWIN/CBrush::CreateSysColorBrush
- AFXWIN/CBrush::FromHandle
- AFXWIN/CBrush::GetLogBrush
dev_langs:
- C++
helpviewer_keywords:
- CBrush [MFC], CBrush
- CBrush [MFC], CreateBrushIndirect
- CBrush [MFC], CreateDIBPatternBrush
- CBrush [MFC], CreateHatchBrush
- CBrush [MFC], CreatePatternBrush
- CBrush [MFC], CreateSolidBrush
- CBrush [MFC], CreateSysColorBrush
- CBrush [MFC], FromHandle
- CBrush [MFC], GetLogBrush
ms.assetid: e5ef2c62-dd95-4973-9090-f52f605900e1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f2c60be4501e14c1a3b55789905be1fb6e753731
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cbrush-class"></a>CBrush – třída
Zapouzdří štětce Windows zařízení grafické rozhraní (GDI).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CBrush : public CGdiObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CBrush::CBrush](#cbrush)|Vytvoří `CBrush` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CBrush::CreateBrushIndirect](#createbrushindirect)|Inicializuje štětce styl, barvu a vzorem zadaným v [logbrush –](http://msdn.microsoft.com/library/windows/desktop/dd145035) struktura.|  
|[CBrush::CreateDIBPatternBrush](#createdibpatternbrush)|Inicializuje štětce pomocí vzoru určeného device independent bitmap (DIB).|  
|[CBrush::CreateHatchBrush](#createhatchbrush)|Inicializuje štětce s zadaný vzor šrafované a barvy.|  
|[CBrush::CreatePatternBrush](#createpatternbrush)|Inicializuje štětce pomocí vzoru určeného rastrový obrázek.|  
|[CBrush::CreateSolidBrush](#createsolidbrush)|Inicializuje štětce zadaný plnou barvou.|  
|[CBrush::CreateSysColorBrush](#createsyscolorbrush)|Vytvoří stopu, je výchozí barvu systému.|  
|[CBrush::FromHandle](#fromhandle)|Vrátí ukazatel `CBrush` objektu, pokud Zadaný popisovač se systémem Windows `HBRUSH` objektu.|  
|[CBrush::GetLogBrush](#getlogbrush)|Získá [logbrush –](http://msdn.microsoft.com/library/windows/desktop/dd145035) struktura.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CBrush::operator HBRUSH](#operator_hbrush)|Vrátí popisovač Windows připojené k `CBrush` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Použít `CBrush` objektu, vytvořit `CBrush` objektu a předejte ji do jakéhokoli `CDC` – členská funkce, která vyžaduje štětce.  
  
 Štětce může být plnou, zasílána nebo vzorované.  
  
 Další informace o `CBrush`, najdete v části [grafické objekty](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CBrush`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="cbrush"></a>CBrush::CBrush  
 Vytvoří `CBrush` objektu.  
  
```  
CBrush(); 
CBrush(COLORREF crColor); 
CBrush(int nIndex, COLORREF crColor); 
explicit CBrush(CBitmap* pBitmap);
```  
  
### <a name="parameters"></a>Parametry  
 `crColor`  
 Určuje barvu popředí stopy jako barva RGB. Pokud je zasílána štětec, tento parametr určuje barvu šrafování.  
  
 `nIndex`  
 Určuje styl šrafování štětce. Může být některého z následujících hodnot:  
  
- `HS_BDIAGONAL`Šrafování dolů (zleva doprava) na 45 stupňů  
  
- `HS_CROSS`Mřížkovaný vodorovně a svisle  
  
- `HS_DIAGCROSS`Mřížky po 45 stupňů  
  
- `HS_FDIAGONAL`Šrafování nahoru (zleva doprava) na 45 stupňů  
  
- `HS_HORIZONTAL`Vodorovné šrafování  
  
- `HS_VERTICAL`Vertikální šrafování  
  
 `pBitmap`  
 Odkazuje na `CBitmap` objekt, který určuje, ke kterému stopy vybarví rastrový obrázek.  
  
### <a name="remarks"></a>Poznámky  
 `CBrush`má čtyři přetížené konstruktory. Konstruktor bez argumentů vytvoří Neinicializovaný `CBrush` objekt, který se musí inicializovat před použitím.  
  
 Pokud používáte konstruktor bez argumentů, musí inicializovat výsledná `CBrush` objektu s [CreateSolidBrush](#createsolidbrush), [CreateHatchBrush](#createhatchbrush), [CreateBrushIndirect](#createbrushindirect), [CreatePatternBrush](#createpatternbrush), nebo [CreateDIBPatternBrush](#createdibpatternbrush). Pokud použijete jeden z konstruktorů, které má argumenty, pak žádné další inicializace je nutné. Konstruktory s argumenty může vyvolat výjimku, pokud dojde k chybám, když bude vždy úspěšné konstruktor bez argumentů.  
  
 Konstruktor s jedním [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) parametr vytvoří plného štětce určenou barvou. Určuje hodnotu RGB barva a konstruovat s `RGB` makro v systému WINDOWS. H.  
  
 Konstruktor s dva parametry vytvoří štětce šrafování. `nIndex` Parametrem index šrafované vzor. `crColor` Parametr určuje barvu.  
  
 Konstruktor s `CBitmap` parametr vytvoří vzorkem štětce. Tento parametr identifikuje rastrový obrázek. Bitmapy se předpokládá, že byly vytvořeny pomocí [CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap), [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [CBitmap::LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap), nebo [ CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap). Minimální velikost rastrového obrázku pro použití v vzorek výplně je 8 × 8 pixelů.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#21](../../mfc/codesnippet/cpp/cbrush-class_1.cpp)]  
  
##  <a name="createbrushindirect"></a>CBrush::CreateBrushIndirect  
 Inicializuje štětce styl, barvu a vzorem zadaným v [logbrush –](http://msdn.microsoft.com/library/windows/desktop/dd145035) struktura.  
  
```  
BOOL CreateBrushIndirect(const LOGBRUSH* lpLogBrush);
```  
  
### <a name="parameters"></a>Parametry  
 *lpLogBrush*  
 Odkazuje na [logbrush –](http://msdn.microsoft.com/library/windows/desktop/dd145035) struktura, která obsahuje informace o stopy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Štětec lze následně vybrat jako aktuální štětce pro jakýkoli kontext zařízení.  
  
 Štětce vytvořený rastrový obrázek černobílý tisk (1 rovině, 1 bitů na pixel) je vykreslovány pomocí aktuální barvu textu a pozadí. S aktuálním barvy budou vykreslovat pixelů reprezentována chvilku nastaven na hodnotu 0. Aktuální barvou pozadí budou vykreslovat pixelů reprezentována chvilku nastavena na hodnotu 1.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#22](../../mfc/codesnippet/cpp/cbrush-class_2.cpp)]  
  
##  <a name="createdibpatternbrush"></a>CBrush::CreateDIBPatternBrush  
 Inicializuje štětce vzoru určeného device independent bitmap (DIB).  
  
```  
BOOL CreateDIBPatternBrush(
    HGLOBAL hPackedDIB,  
    UINT nUsage);

 
BOOL CreateDIBPatternBrush(
    const void* lpPackedDIB,  
    UINT nUsage);
```  
  
### <a name="parameters"></a>Parametry  
 *hPackedDIB*  
 Identifikuje objekt globální paměť obsahující sbalené device independent bitmap (DIB).  
  
 *nUsage*  
 Určuje, zda **[bmiColors]** pole [bitmapinfo –](../../mfc/reference/bitmapinfo-structure.md) datové struktury (součástí "zabaleny DIB") obsahují explicitní hodnoty RGB nebo indexy, které do aktuálně zjištěné logické palety. Parametr musí mít jednu z následujících hodnot:  
  
- **DIB_PAL_COLORS** tabulce barev se skládá z pole indexů 16 bitů.  
  
- **DIB_RGB_COLORS** tabulce barev obsahuje literál hodnoty RGB.  
  
 *lpPackedDIB*  
 Odkazuje na sbalené DIB skládající se z `BITMAPINFO` struktura bezprostředně následované pole bajtů definování pixelů bitmapy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Štětec lze následně vybrat pro jakýkoli kontext zařízení, která podporuje rastrové operace.  
  
 Dvě verze lišit ve způsobu zpracování DIB:  
  
-   V první verzi, chcete-li získat popisovač DIB zavolejte Windows **GlobalAlloc** funkce přidělit globální paměť blok a pak zadejte velikost paměti s sbalené DIB.  
  
-   V druhé verzi, není nutné volat **GlobalAlloc** přidělit paměť pro sbalený DIB.  
  
 Zabalená DIB se skládá z `BITMAPINFO` datová struktura bezprostředně následované pole bajtů, která definuje pixelů bitmapy. Rastrové obrázky použít jako výplň vzory by měl být 8 × 8 pixelů. Pokud bitmapy je větší, vytvoří Windows vzorek výplně pomocí pouze bits odpovídající prvních 8 řádků a sloupců 8 pixelů v levém horním rohu bitmapy.  
  
 Když aplikace vybere štětce vzor DIB dvě barvy v kontextu černobílý zařízení, systém Windows bude ignorovat barvy definované v DIB a místo toho zobrazí štětce vzor pomocí barvy textu a pozadí, aktuálním kontextu zařízení. Pixelů namapované na první barva DIB (u posunu 0 v tabulce barev DIB) se zobrazí pomocí barvu textu. Pixelů namapována na druhý barvu (na posunu 1 v tabulce barev) se zobrazí pomocí barvu pozadí.  
  
 Informace o používání následující funkce Windows najdete v tématu Windows SDK:  
  
- [CreateDIBPatternBrush](http://msdn.microsoft.com/library/windows/desktop/dd183492) (Tato funkce slouží pouze k zajištění kompatibility s aplikacemi, které jsou napsané pro verzích Windows starších než 3.0; použít **CreateDIBPatternBrushPt** funkce.)  
  
- [CreateDIBPatternBrushPt](http://msdn.microsoft.com/library/windows/desktop/dd183493) (Tato funkce slouží pro aplikace založené na Win32.)  
  
- [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574)  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#23](../../mfc/codesnippet/cpp/cbrush-class_3.cpp)]  
  
##  <a name="createhatchbrush"></a>CBrush::CreateHatchBrush  
 Inicializuje štětce s zadaný vzor šrafované a barvy.  
  
```  
BOOL CreateHatchBrush(
    int nIndex,  
    COLORREF crColor);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Určuje styl šrafování štětce. Může být některého z následujících hodnot:  
  
- `HS_BDIAGONAL`Šrafování dolů (zleva doprava) na 45 stupňů  
  
- `HS_CROSS`Mřížkovaný vodorovně a svisle  
  
- `HS_DIAGCROSS`Mřížky po 45 stupňů  
  
- `HS_FDIAGONAL`Šrafování nahoru (zleva doprava) na 45 stupňů  
  
- `HS_HORIZONTAL`Vodorovné šrafování  
  
- `HS_VERTICAL`Vertikální šrafování  
  
 `crColor`  
 Určuje barvu popředí stopy jako barva RGB (barvu šrafování). V tématu [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) ve Windows SDK pro další informace.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Štětec lze následně vybrat jako aktuální štětce pro jakýkoli kontext zařízení.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#24](../../mfc/codesnippet/cpp/cbrush-class_4.cpp)]  
  
##  <a name="createpatternbrush"></a>CBrush::CreatePatternBrush  
 Inicializuje štětce pomocí vzoru určeného rastrový obrázek.  
  
```  
BOOL CreatePatternBrush(CBitmap* pBitmap);
```  
  
### <a name="parameters"></a>Parametry  
 `pBitmap`  
 Identifikuje rastrový obrázek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Štětec lze následně vybrat pro jakýkoli kontext zařízení, která podporuje rastrové operace. Rastrový obrázek identifikovaný `pBitmap` se obvykle inicializují pomocí [CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap), [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [CBitmap::LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap), nebo [CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap) funkce.  
  
 Rastrové obrázky použít jako výplň vzory by měl být 8 × 8 pixelů. Bitmapy je větší, v systému Windows se použije pouze na bits odpovídající prvních 8 řádků a sloupců pixelů v levém horním rohu bitmapy.  
  
 Vzor štětce se dá odstranit bez ovlivnění přidružené bitové mapy. To znamená, že bitmapy může být použit k vytvoření libovolný počet štětce vzor.  
  
 Štětce vytvořený černobílý rastrový obrázek (1 barva rovině, 1 bitů na pixel) je vykreslovány pomocí aktuální barvu textu a pozadí. S aktuálním barvy jsou vykreslovány pixelů reprezentována chvilku nastaven na hodnotu 0. Aktuální barvou pozadí se vykresluje pixelů reprezentována chvilku nastavena na hodnotu 1.  
  
 Informace o používání [CreatePatternBrush](http://msdn.microsoft.com/library/windows/desktop/dd183508), systému Windows fungovat, najdete v části Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#25](../../mfc/codesnippet/cpp/cbrush-class_5.cpp)]  
  
##  <a name="createsolidbrush"></a>CBrush::CreateSolidBrush  
 Inicializuje štětce zadaný plnou barvou.  
  
```  
BOOL CreateSolidBrush(COLORREF crColor);
```  
  
### <a name="parameters"></a>Parametry  
 `crColor`  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) struktura, která určuje barvu štětce. Určuje hodnotu RGB barva a konstruovat s `RGB` makro v systému WINDOWS. H.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Štětec lze následně vybrat jako aktuální štětce pro jakýkoli kontext zařízení.  
  
 Když aplikace dokončí štětce vytvořené pomocí `CreateSolidBrush`, ho měli vybrat štětce mimo kontext zařízení.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CBrush::CBrush](#cbrush).  
  
##  <a name="createsyscolorbrush"></a>CBrush::CreateSysColorBrush  
 Inicializuje štětce barev.  
  
```  
BOOL CreateSysColorBrush(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Určuje barvu index. Tato hodnota odpovídá barvu použitou k vyplnění jeden z elementů 21 okno. V tématu [GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371) ve Windows SDK pro seznam hodnot.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Štětec lze následně vybrat jako aktuální štětce pro jakýkoli kontext zařízení.  
  
 Když aplikace dokončí štětce vytvořené pomocí `CreateSysColorBrush`, ho měli vybrat štětce mimo kontext zařízení.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#26](../../mfc/codesnippet/cpp/cbrush-class_6.cpp)]  
  
##  <a name="fromhandle"></a>CBrush::FromHandle  
 Vrátí ukazatel `CBrush` objektu, pokud Zadaný popisovač se systémem Windows [HBRUSH](#operator_hbrush) objektu.  
  
```  
static CBrush* PASCAL FromHandle(HBRUSH hBrush);
```  
  
### <a name="parameters"></a>Parametry  
 `hBrush`  
 `HANDLE`k štětce GDI systému Windows.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `CBrush` objekt, je-li úspěšná, jinak hodnota **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `CBrush` objekt není už připojený k popisovač dočasného `CBrush` objekt se vytvoří a připojené. Toto dočasný `CBrush` je objekt platný pouze až po příštím aplikace má čas nečinnosti v jeho událostí smyčky. V tomto okamžiku se odstraní všechny dočasné grafické objekty. Jinými slovy dočasný objekt platí pouze při zpracování zprávy jeden interval.  
  
 Další informace o použití grafických objektů najdete v tématu [obrázek objekty](http://msdn.microsoft.com/library/windows/desktop/dd144962) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CBrush::CBrush](#cbrush).  
  
##  <a name="getlogbrush"></a>CBrush::GetLogBrush  
 Volání této funkce člen načíst `LOGBRUSH` struktura.  
  
```  
int GetLogBrush(LOGBRUSH* pLogBrush);
```  
  
### <a name="parameters"></a>Parametry  
 `pLogBrush`  
 Odkazuje na [logbrush –](http://msdn.microsoft.com/library/windows/desktop/dd145035) struktura, která obsahuje informace o stopy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud funkci úspěšné, a `pLogBrush` platný ukazatel vrácená hodnota je počet bajtů, které jsou uložené do vyrovnávací paměti.  
  
 Pokud funkci úspěšné, a `pLogBrush` je **NULL**, vrácená hodnota je počet bajtů požadovaných k uložení informace funkce by ukládání do vyrovnávací paměti.  
  
 Pokud se funkce nezdaří, je vrácenou hodnotu 0.  
  
### <a name="remarks"></a>Poznámky  
 `LOGBRUSH` Struktura definuje styl, barvu a vzor štětce.  
  
 Například volání `GetLogBrush` tak, aby odpovídala konkrétním barvu nebo vzorek bitmapy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#27](../../mfc/codesnippet/cpp/cbrush-class_7.cpp)]  
  
##  <a name="operator_hbrush"></a>CBrush::operator HBRUSH  
 Tento operátor. použijte k získání připojené popisovač GDI systému Windows `CBrush` objektu.  
  
```  
operator HBRUSH() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud úspěšné, popisovač pro objekt Windows GDI reprezentována `CBrush` objektu; v opačném případě **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Operátor je operátor přetypování, který podporuje přímý použití `HBRUSH` objektu.  
  
 Další informace o použití grafických objektů najdete v tématu [obrázek objekty](http://msdn.microsoft.com/library/windows/desktop/dd144962) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#28](../../mfc/codesnippet/cpp/cbrush-class_8.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC PROPDLG](../../visual-cpp-samples.md)   
 [CGdiObject – třída](../../mfc/reference/cgdiobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CBitmap – třída](../../mfc/reference/cbitmap-class.md)   
 [CDC – třída](../../mfc/reference/cdc-class.md)
