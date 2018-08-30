---
title: Cpalette – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: ff3a68e585cecb8affb0a5f4ffb7ff81929c955a
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43201100"
---
# <a name="cpalette-class"></a>Cpalette – třída
Zapouzdřuje barevnou paletu barev Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CPalette : public CGdiObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CPalette::CPalette](#cpalette)|Vytvoří `CPalette` objekt se žádné připojené palety Windows. Je třeba inicializovat `CPalette` objekt s jedním z inicializace členských funkcí předtím, než je možné.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CPalette::AnimatePalette](#animatepalette)|Nahradí položky v logickou paletu identifikován `CPalette` objektu. Aplikace nemá klientské oblasti, aktualizovat, protože Windows mapuje nové položky do systémové palety okamžitě.|  
|[CPalette::CreateHalftonePalette](#createhalftonepalette)|Vytvoří barevnou paletu polotónování pro kontext zařízení a připojí ho k `CPalette` objektu.|  
|[CPalette::CreatePalette](#createpalette)|Vytvoří paletu barev Windows a připojí ho k `CPalette` objektu.|  
|[CPalette::FromHandle](#fromhandle)|Vrací ukazatel `CPalette` objektu při popisovač objektu palety Windows.|  
|[CPalette::GetEntryCount](#getentrycount)|Získá počet palety v logickou paletu.|  
|[CPalette::GetNearestPaletteIndex](#getnearestpaletteindex)|Vrátí index položky v logickou paletu, která nejlépe odpovídá hodnotu barvy.|  
|[CPalette::GetPaletteEntries](#getpaletteentries)|Načte rozsah palety v logickou paletu.|  
|[CPalette::ResizePalette](#resizepalette)|Změní velikost logickou paletu určené `CPalette` objekt pro zadaný počet položek.|  
|[CPalette::SetPaletteEntries](#setpaletteentries)|Nastaví RGB – hodnoty barev a příznaky v rozsahu položek v logickou paletu.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CPalette::operator HPALETTE](#operator_hpalette)|Vrátí HPALETTE připojené k `CPalette`.|  
  
## <a name="remarks"></a>Poznámky  
 Barevnou paletu poskytuje rozhraní mezi aplikací a zařízení barva výstupu (jako je například zobrazovací zařízení). Rozhraní umožňuje aplikaci plně využít možnosti barva výstupního zařízení bez zásahů vážně barev zobrazí jiné aplikace. Windows používá k určení barvy použité logickou paletu. aplikace (seznam potřebné barev) a systémové palety (definující dostupných barev).  
  
 A `CPalette` objekt poskytuje členské funkce pro manipulaci s na paletě uvedené v objektu. Vytvoření `CPalette` objektu a použít její členské funkce k vytvoření skutečné palety, grafický objekt zařízení rozhraní (GDI) a k manipulaci s jeho položek a dalších vlastností.  
  
 Další informace o používání `CPalette`, naleznete v tématu [grafické objekty](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [Cgdiobject –](../../mfc/reference/cgdiobject-class.md)  
  
 `CPalette`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="animatepalette"></a>  CPalette::AnimatePalette  
 Nahradí položky v logickou paletu připojené k `CPalette` objektu.  
  
```  
void AnimatePalette(
    UINT nStartIndex,  
    UINT nNumEntries,  
    LPPALETTEENTRY lpPaletteColors);
```  
  
### <a name="parameters"></a>Parametry  
 *nStartIndex*  
 Určuje první položku v palety animovat.  
  
 *nNumEntries*  
 Určuje počet položek v palety animovat.  
  
 *lpPaletteColors*  
 Odkazuje na první člen pole [PALETTEENTRY](https://msdn.microsoft.com/library/windows/desktop/dd162769) struktury k nahrazení palety identifikovaný *nStartIndex* a *nNumEntries*.  
  
### <a name="remarks"></a>Poznámky  
 Pokud aplikace zavolá `AnimatePalette`, nemusí se aktualizovat jeho klientské oblasti, protože Windows mapuje nové položky do systémové palety okamžitě.  
  
 `AnimatePalette` Funkce se změní pouze položky s příznakem PC_RESERVED nastavit v odpovídající `palPaletteEntry` člena [LOGPALETTE](/windows/desktop/api/wingdi/ns-wingdi-taglogpalette) struktura, která je připojena k `CPalette` objektu. Zobrazit LOGPALETTE v sadě Windows SDK pro další informace o této struktury.  
  
##  <a name="cpalette"></a>  CPalette::CPalette  
 Vytvoří `CPalette` objektu.  
  
```  
CPalette();
```  
  
### <a name="remarks"></a>Poznámky  
 Objekt nemá žádné připojené palety až do okamžiku volání `CreatePalette` připojit jeden.  
  
##  <a name="createhalftonepalette"></a>  CPalette::CreateHalftonePalette  
 Vytvoří barevnou paletu polotónování kontextu zařízení.  
  
```  
BOOL CreateHalftonePalette(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 *primární řadič domény*  
 Určuje kontext zařízení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Aplikace by měl vytvořit paletu polotónování při režim roztažení kontextu zařízení nastavena na POLOTÓNOVÁNÍ. Logické polotónování palety vrácené [CreateHalftonePalette](/windows/desktop/api/wingdi/nf-wingdi-createhalftonepalette) členskou funkci pak by měl vybraný a realizovat do kontextu zařízení před [CDC::StretchBlt](../../mfc/reference/cdc-class.md#stretchblt) nebo [ StretchDIBits](/windows/desktop/api/wingdi/nf-wingdi-stretchdibits) funkce je volána.  
  
 Zobrazit sady Windows SDK pro další informace o `CreateHalftonePalette` a `StretchDIBits`.  
  
##  <a name="createpalette"></a>  CPalette::CreatePalette  
 Inicializuje `CPalette` vytvořením logických barevné palety Windows a připojíte ho k objektu `CPalette` objektu.  
  
```  
BOOL CreatePalette(LPLOGPALETTE lpLogPalette);
```  
  
### <a name="parameters"></a>Parametry  
 *lpLogPalette*  
 Odkazuje [LOGPALETTE](/windows/desktop/api/wingdi/ns-wingdi-taglogpalette) strukturu, která obsahuje informace o barvy v logickou paletu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit sady Windows SDK pro další informace o `LOGPALETTE` struktury.  
  
##  <a name="fromhandle"></a>  CPalette::FromHandle  
 Vrací ukazatel `CPalette` objektu při popisovač objektu palety Windows.  
  
```  
static CPalette* PASCAL FromHandle(HPALETTE hPalette);
```  
  
### <a name="parameters"></a>Parametry  
 *hPalette*  
 Popisovač paletu barev Windows GDI.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `CPalette` objekt Pokud úspěšné; jinak hodnota NULL.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `CPalette` objekt už není připojen k paletě Windows dočasný `CPalette` objekt se vytvoří a připojí. Tento dočasný `CPalette` objektu je platná pouze v až při příštím má aplikace čas nečinnosti v jeho smyčkou událostí, na které čas všechny dočasné obrázek objekty budou odstraněny. Jinými slovy dočasný objekt platí pouze při zpracování zprávy jedno okno.  
  
##  <a name="getentrycount"></a>  CPalette::GetEntryCount  
 Voláním této členské funkce se načíst počet položek v dané logickou paletu.  
  
```  
int GetEntryCount();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek v logickou paletu.  
  
##  <a name="getnearestpaletteindex"></a>  CPalette::GetNearestPaletteIndex  
 Vrátí index položky v logickou paletu, která nejlépe odpovídá hodnotě zadané barvy.  
  
```  
UINT GetNearestPaletteIndex(COLORREF crColor) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *crColor*  
 Určuje barvu, která bude odpovídat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index položky v logickou paletu. Položka obsahuje barvu, která nejvíce téměř odpovídá zadané barvy.  
  
##  <a name="getpaletteentries"></a>  CPalette::GetPaletteEntries  
 Načte rozsah palety v logickou paletu.  
  
```  
UINT GetPaletteEntries(
    UINT nStartIndex,  
    UINT nNumEntries,  
    LPPALETTEENTRY lpPaletteColors) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nStartIndex*  
 Určuje první položku v logickou paletu, která se má načíst.  
  
 *nNumEntries*  
 Určuje počet položek v logickou paletu, která se má načíst.  
  
 *lpPaletteColors*  
 Odkazuje na pole [PALETTEENTRY](https://msdn.microsoft.com/library/windows/desktop/dd162769) datové struktury pro příjem položky palety. Pole musí obsahovat alespoň tolik datových struktur podle specifikace *nNumEntries*.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek, které získaných logickou paletu; 0, pokud funkce se nezdařilo.  
  
##  <a name="operator_hpalette"></a>  CPalette::operator HPALETTE  
 Tento operátor se získat popisovač Windows GDI připojené `CPalette` objektu.  
  
```  
operator HPALETTE() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud úspěchu popisovač objektů Windows GDI reprezentována `CPalette` objektu; v opačném případě hodnota NULL.  
  
### <a name="remarks"></a>Poznámky  
 Tento operátor je operátor přetypování, která podporuje přímému použití objektu HPALETTE.  
  
 Další informace o použití grafických objektů najdete v článku [objektů grafiky](/windows/desktop/gdi/graphic-objects) v sadě Windows SDK.  
  
##  <a name="resizepalette"></a>  CPalette::ResizePalette  
 Změní velikost logickou paletu připojené k `CPalette` objektu na číslo určené položky *nNumEntries*.  
  
```  
BOOL ResizePalette(UINT nNumEntries);
```  
  
### <a name="parameters"></a>Parametry  
 *nNumEntries*  
 Určuje počet položek, které na paletě po se změnila.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud se úspěšně změnila na paletě; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud aplikace zavolá `ResizePalette` ke zmenšení velikosti palety, jsou položky zbývající změněnou paletě beze změny. Pokud aplikace volá `ResizePalette` zvětšíte paletu doplňková paleta položky jsou nastaveny na černé (červené, zelené a modré hodnoty jsou všechny 0) a jsou nastaveny příznaky pro všechny další položky na hodnotu 0.  
  
 Další informace o rozhraní API Windows `ResizePalette`, naleznete v tématu [ResizePalette](/windows/desktop/api/wingdi/nf-wingdi-resizepalette) v sadě Windows SDK.  
  
##  <a name="setpaletteentries"></a>  CPalette::SetPaletteEntries  
 Nastaví RGB – hodnoty barev a příznaky v rozsahu položek v logickou paletu.  
  
```  
UINT SetPaletteEntries(
    UINT nStartIndex,  
    UINT nNumEntries,  
    LPPALETTEENTRY lpPaletteColors);
```  
  
### <a name="parameters"></a>Parametry  
 *nStartIndex*  
 Určuje první položku v logickou paletu, která se má nastavit.  
  
 *nNumEntries*  
 Určuje počet položek v logickou paletu, která se má nastavit.  
  
 *lpPaletteColors*  
 Odkazuje na pole [PALETTEENTRY](https://msdn.microsoft.com/library/windows/desktop/dd162769) datové struktury pro příjem položky palety. Pole musí obsahovat alespoň tolik datových struktur podle specifikace *nNumEntries*.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nastavit počet položek v logickou paletu; 0, pokud funkce se nezdařilo.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je logickou paletu vybrána kontextu zařízení, pokud aplikace volá `SetPaletteEntries`, změny se projeví až do volání aplikace [CDC::RealizePalette](../../mfc/reference/cdc-class.md#realizepalette).  
  
 Další informace o struktuře Windows `PALETTEENTRY`, naleznete v tématu [PALETTEENTRY](https://msdn.microsoft.com/library/windows/desktop/dd162769) v sadě Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Ukázky knihovny MFC DIBLOOK](../../visual-cpp-samples.md)   
 [Cgdiobject – třída](../../mfc/reference/cgdiobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CPalette::GetPaletteEntries](#getpaletteentries)   
 [CPalette::SetPaletteEntries](#setpaletteentries)



