---
title: CPalette – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPalette
- AFXWIN/CPalette
- AFXWIN/CPalette::CPalette
- AFXWIN/CPalette::AnimatePalette
- AFXWIN/CPalette::CreateHalftonePalette
- AFXWIN/CPalette::CreatePalette
- AFXWIN/CPalette::FromHandle
- AFXWIN/CPalette::GetEntryCount
- AFXWIN/CPalette::GetNearestPaletteIndex
- AFXWIN/CPalette::GetPaletteEntries
- AFXWIN/CPalette::ResizePalette
- AFXWIN/CPalette::SetPaletteEntries
dev_langs:
- C++
helpviewer_keywords:
- CPalette [MFC], CPalette
- CPalette [MFC], AnimatePalette
- CPalette [MFC], CreateHalftonePalette
- CPalette [MFC], CreatePalette
- CPalette [MFC], FromHandle
- CPalette [MFC], GetEntryCount
- CPalette [MFC], GetNearestPaletteIndex
- CPalette [MFC], GetPaletteEntries
- CPalette [MFC], ResizePalette
- CPalette [MFC], SetPaletteEntries
ms.assetid: 8cd95498-53ed-4852-85e1-70e522541114
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 36cc13fa77becf5bdeb3960f6ac9db18d5d63dbb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33377273"
---
# <a name="cpalette-class"></a>CPalette – třída
Zapouzdří palety barev systému Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CPalette : public CGdiObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CPalette::CPalette](#cpalette)|Vytvoří `CPalette` objekt s žádné připojené paletu systému Windows. Je třeba inicializovat `CPalette` objektu s jedním z členské funkce inicializace před použitím.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CPalette::AnimatePalette](#animatepalette)|Nahradí položky v logické palety identifikovaný `CPalette` objektu. Aplikace nemá klientské oblasti, aktualizovat, protože Windows mapuje nové položky do systémové palety okamžitě.|  
|[CPalette::CreateHalftonePalette](#createhalftonepalette)|Vytvoří polotónování palety pro kontext zařízení a připojí jej k `CPalette` objektu.|  
|[CPalette::CreatePalette](#createpalette)|Palety barev Windows vytvoří a připojí jej k `CPalette` objektu.|  
|[CPalette::FromHandle](#fromhandle)|Vrátí ukazatel na `CPalette` objektu, pokud Zadaný popisovač na objekt palety Windows.|  
|[CPalette::GetEntryCount](#getentrycount)|Načte počet položek palety v logické palety.|  
|[CPalette::GetNearestPaletteIndex](#getnearestpaletteindex)|Vrátí index položky v logické palety, která nejvíce odpovídá implementované hodnoty barvy.|  
|[CPalette::GetPaletteEntries](#getpaletteentries)|Načte rozsah palety v logické palety.|  
|[CPalette::ResizePalette](#resizepalette)|Změní velikost logické palety určeného `CPalette` objekt, který má zadaný počet položek.|  
|[CPalette::SetPaletteEntries](#setpaletteentries)|Nastaví v rozsahu položek v logické palety RGB – hodnoty barev a značky.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CPalette::operator HPALETTE](#operator_hpalette)|Vrátí `HPALETTE` připojené k `CPalette`.|  
  
## <a name="remarks"></a>Poznámky  
 Paleta poskytuje rozhraní mezi aplikací a zařízení výstup barvu (například zobrazení zařízení). Rozhraní umožňuje aplikace, abyste mohli plně využívat funkce barva výstupního zařízení bez vážně zasahovala do činnosti barev zobrazí jiné aplikace. Windows používá k určení barvy používané aplikace logické palety (seznam potřebné barev) a systémové palety (definující dostupné barvy).  
  
 A `CPalette` objekt poskytuje členské funkce pro manipulaci s palety, na které odkazuje objekt. Vytvořit `CPalette` objektu a použít jeho členské funkce pro vytvoření skutečné palety objekt grafické rozhraní (GDI) zařízení a k manipulaci s jeho položek a dalších vlastností.  
  
 Další informace o používání `CPalette`, najdete v části [grafické objekty](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CPalette`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="animatepalette"></a>  CPalette::AnimatePalette  
 Nahradí položky v logické palety připojené k `CPalette` objektu.  
  
```  
void AnimatePalette(
    UINT nStartIndex,  
    UINT nNumEntries,  
    LPPALETTEENTRY lpPaletteColors);
```  
  
### <a name="parameters"></a>Parametry  
 `nStartIndex`  
 Určuje první položku v palety být animace.  
  
 `nNumEntries`  
 Určuje počet položek v palety být animace.  
  
 `lpPaletteColors`  
 Odkazuje na první prvek pole [PALETTEENTRY](http://msdn.microsoft.com/library/windows/desktop/dd162769) struktury nahradit palety identifikovaný `nStartIndex` a `nNumEntries`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud aplikace zavolá `AnimatePalette`, nemá aktualizovat klientské oblasti, protože Windows mapuje nové položky do systémové palety okamžitě.  
  
 `AnimatePalette` Funkce se změní pouze položky s **PC_RESERVED** nastaven do odpovídajícího příznak **palPaletteEntry** členem [LOGPALETTE](http://msdn.microsoft.com/library/windows/desktop/dd145040) struktura připojená k `CPalette` objektu. V tématu **LOGPALETTE** ve Windows SDK pro další informace o tuto strukturu.  
  
##  <a name="cpalette"></a>  CPalette::CPalette  
 Vytvoří `CPalette` objektu.  
  
```  
CPalette();
```  
  
### <a name="remarks"></a>Poznámky  
 Objekt nemá žádné připojené palety, dokud zavoláte `CreatePalette` jeden připojit.  
  
##  <a name="createhalftonepalette"></a>  CPalette::CreateHalftonePalette  
 Vytvoří se paleta polotónování pro kontext zařízení.  
  
```  
BOOL CreateHalftonePalette(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Identifikuje kontextu zařízení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Aplikace měli vytvořit polotónování palety, když roztažení režim kontextu zařízení je nastaven na **POLOTÓNOVÁNÍ**. Palety logické polotónování vrácený [CreateHalftonePalette](http://msdn.microsoft.com/library/windows/desktop/dd183503) – členská funkce pak by měl vybraný a uvědomili si do kontextu zařízení před [CDC::StretchBlt](../../mfc/reference/cdc-class.md#stretchblt) nebo [ StretchDIBits](http://msdn.microsoft.com/library/windows/desktop/dd145121) funkce je volána.  
  
 Najdete v části sada Windows SDK pro další informace `CreateHalftonePalette` a **StretchDIBits**.  
  
##  <a name="createpalette"></a>  CPalette::CreatePalette  
 Inicializuje `CPalette` objekt vytvořením palety barev logické Windows a připojíte ho k `CPalette` objektu.  
  
```  
BOOL CreatePalette(LPLOGPALETTE lpLogPalette);
```  
  
### <a name="parameters"></a>Parametry  
 `lpLogPalette`  
 Odkazuje na [LOGPALETTE](http://msdn.microsoft.com/library/windows/desktop/dd145040) struktura, která obsahuje informace o barev v logické palety.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Najdete v části sada Windows SDK pro další informace **LOGPALETTE** struktury.  
  
##  <a name="fromhandle"></a>  CPalette::FromHandle  
 Vrátí ukazatel na `CPalette` objektu, pokud Zadaný popisovač na objekt palety Windows.  
  
```  
static CPalette* PASCAL FromHandle(HPALETTE hPalette);
```  
  
### <a name="parameters"></a>Parametry  
 `hPalette`  
 Popisovač pro palety barev GDI systému Windows.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `CPalette` objekt, je-li úspěšná, jinak hodnota **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `CPalette` objekt není už připojený k Windows palety, dočasného `CPalette` objekt se vytvoří a připojené. Toto dočasný `CPalette` je objekt platný pouze dokud příště aplikace má čas nečinnosti v jeho událostí smyčky, na který čas všechny dočasné obrázek objekty jsou odstraněny. Jinými slovy dočasný objekt platí pouze při zpracování zprávy jeden interval.  
  
##  <a name="getentrycount"></a>  CPalette::GetEntryCount  
 Volání této funkce člen načíst počet položek v dané logické palety.  
  
```  
int GetEntryCount();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek v logické palety.  
  
##  <a name="getnearestpaletteindex"></a>  CPalette::GetNearestPaletteIndex  
 Vrátí index položky v logické palety, která nejvíce odpovídá implementované hodnoty zadané barvy.  
  
```  
UINT GetNearestPaletteIndex(COLORREF crColor) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `crColor`  
 Určuje barvu, která bude odpovídat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index položky v logické palety. Položka obsahuje barvu, která co nejvíce shoduje zadaná barva.  
  
##  <a name="getpaletteentries"></a>  CPalette::GetPaletteEntries  
 Načte rozsah palety v logické palety.  
  
```  
UINT GetPaletteEntries(
    UINT nStartIndex,  
    UINT nNumEntries,  
    LPPALETTEENTRY lpPaletteColors) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nStartIndex`  
 Určuje první položku v logické palety mají být načteny.  
  
 `nNumEntries`  
 Určuje počet položek v logické palety mají být načteny.  
  
 `lpPaletteColors`  
 Odkazuje na pole [PALETTEENTRY](http://msdn.microsoft.com/library/windows/desktop/dd162769) datové struktury pro příjem palety položky. Pole musí obsahovat alespoň tolik datové struktury podle specifikace `nNumEntries`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek, které jsou načteny z logické palety; 0, pokud funkce se nezdařilo.  
  
##  <a name="operator_hpalette"></a>  CPalette::operator HPALETTE  
 Tento operátor. použijte k získání připojené popisovač GDI systému Windows `CPalette` objektu.  
  
```  
operator HPALETTE() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud úspěšné, popisovač pro objekt Windows GDI reprezentována `CPalette` objektu; v opačném případě **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Operátor je operátor přetypování, který podporuje přímý použití `HPALETTE` objektu.  
  
 Další informace o použití grafických objektů najdete v článku [obrázek objekty](http://msdn.microsoft.com/library/windows/desktop/dd144962) ve Windows SDK.  
  
##  <a name="resizepalette"></a>  CPalette::ResizePalette  
 Změní velikost logické palety připojené k `CPalette` objekt, který má počet položek určeného `nNumEntries`.  
  
```  
BOOL ResizePalette(UINT nNumEntries);
```  
  
### <a name="parameters"></a>Parametry  
 `nNumEntries`  
 Určuje počet položek v paletě po změně velikosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byla úspěšně nastavena velikost palety; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud aplikace zavolá `ResizePalette` ke snížení velikosti palety, budou položky zbývající změněnou palety beze změny. Pokud aplikace zavolá `ResizePalette` zvětšení palety, další palety nastaveny na černé (červené, zelené a modré hodnoty jsou všechny 0), a pro všechny další záznamy příznaky jsou nastaveny na hodnotu 0.  
  
 Další informace o rozhraní API systému Windows `ResizePalette`, najdete v části [ResizePalette](http://msdn.microsoft.com/library/windows/desktop/dd162928) ve Windows SDK.  
  
##  <a name="setpaletteentries"></a>  CPalette::SetPaletteEntries  
 Nastaví v rozsahu položek v logické palety RGB – hodnoty barev a značky.  
  
```  
UINT SetPaletteEntries(
    UINT nStartIndex,  
    UINT nNumEntries,  
    LPPALETTEENTRY lpPaletteColors);
```  
  
### <a name="parameters"></a>Parametry  
 `nStartIndex`  
 Určuje první položku v logické palety nastavit.  
  
 `nNumEntries`  
 Určuje počet položek v logické palety nastavit.  
  
 `lpPaletteColors`  
 Odkazuje na pole [PALETTEENTRY](http://msdn.microsoft.com/library/windows/desktop/dd162769) datové struktury pro příjem palety položky. Pole musí obsahovat alespoň tolik datové struktury podle specifikace `nNumEntries`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nastavit počet položek v logické palety; 0, pokud funkce se nezdařilo.  
  
### <a name="remarks"></a>Poznámky  
 Pokud logické palety je vybrána v kontextu zařízení, pokud aplikace zavolá `SetPaletteEntries`, změny se projeví až volání aplikace [CDC::RealizePalette](../../mfc/reference/cdc-class.md#realizepalette).  
  
 Další informace o struktuře Windows **PALETTEENTRY**, najdete v části [PALETTEENTRY](http://msdn.microsoft.com/library/windows/desktop/dd162769) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC DIBLOOK](../../visual-cpp-samples.md)   
 [CGdiObject – třída](../../mfc/reference/cgdiobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CPalette::GetPaletteEntries](#getpaletteentries)   
 [CPalette::SetPaletteEntries](#setpaletteentries)



