---
title: Cbitmap – třída
ms.date: 11/04/2016
f1_keywords:
- CBitmap
- AFXWIN/CBitmap
- AFXWIN/CBitmap::CBitmap
- AFXWIN/CBitmap::CreateBitmap
- AFXWIN/CBitmap::CreateBitmapIndirect
- AFXWIN/CBitmap::CreateCompatibleBitmap
- AFXWIN/CBitmap::CreateDiscardableBitmap
- AFXWIN/CBitmap::FromHandle
- AFXWIN/CBitmap::GetBitmap
- AFXWIN/CBitmap::GetBitmapBits
- AFXWIN/CBitmap::GetBitmapDimension
- AFXWIN/CBitmap::LoadBitmap
- AFXWIN/CBitmap::LoadMappedBitmap
- AFXWIN/CBitmap::LoadOEMBitmap
- AFXWIN/CBitmap::SetBitmapBits
- AFXWIN/CBitmap::SetBitmapDimension
helpviewer_keywords:
- CBitmap [MFC], CBitmap
- CBitmap [MFC], CreateBitmap
- CBitmap [MFC], CreateBitmapIndirect
- CBitmap [MFC], CreateCompatibleBitmap
- CBitmap [MFC], CreateDiscardableBitmap
- CBitmap [MFC], FromHandle
- CBitmap [MFC], GetBitmap
- CBitmap [MFC], GetBitmapBits
- CBitmap [MFC], GetBitmapDimension
- CBitmap [MFC], LoadBitmap
- CBitmap [MFC], LoadMappedBitmap
- CBitmap [MFC], LoadOEMBitmap
- CBitmap [MFC], SetBitmapBits
- CBitmap [MFC], SetBitmapDimension
ms.assetid: 3980616a-c59d-495a-86e6-62bd3889c84c
ms.openlocfilehash: 11e210680bdf68f1a1dcbfaed18ae56ce006c8ad
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58769898"
---
# <a name="cbitmap-class"></a>Cbitmap – třída

Zapouzdřuje bitmapy rozhraní GDI systému Windows grafiky zařízení a poskytuje členské funkce pro manipulaci s rastrového obrázku.

## <a name="syntax"></a>Syntaxe

```
class CBitmap : public CGdiObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CBitmap::CBitmap](#cbitmap)|Vytvoří `CBitmap` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CBitmap::CreateBitmap](#createbitmap)|Inicializuje objekt, který má nastavená šířka, výška a bitový vzor bitmapa paměti závislé na zařízení.|
|[CBitmap::CreateBitmapIndirect](#createbitmapindirect)|Inicializuje objekt s rastrový obrázek šířku, výšku a bitový vzor (Pokud je zadaná) podle `BITMAP` struktury.|
|[CBitmap::CreateCompatibleBitmap](#createcompatiblebitmap)|Inicializuje objekt s rastrový obrázek tak, aby byl kompatibilní s určitým zařízením.|
|[CBitmap::CreateDiscardableBitmap](#creatediscardablebitmap)|Inicializuje objekt s discardable rastrový obrázek, který je kompatibilní s určitým zařízením.|
|[CBitmap::FromHandle](#fromhandle)|Vrací ukazatel na `CBitmap` objektu, když je zadaný popisovač Windows `HBITMAP` rastrového obrázku.|
|[CBitmap::GetBitmap](#getbitmap)|Vyplní `BITMAP` struktura s informacemi o rastrového obrázku.|
|[CBitmap::GetBitmapBits](#getbitmapbits)|Bity Zadaný rastrový obrázek zkopíruje do zadané vyrovnávací paměti.|
|[CBitmap::GetBitmapDimension](#getbitmapdimension)|Vrátí šířku a výšku rastrového obrázku. Výška a šířka jsou předpokládá, že jste dříve nastavili [SetBitmapDimension](#setbitmapdimension) členskou funkci.|
|[CBitmap::LoadBitmap](#loadbitmap)|Inicializuje objekt načítání pojmenovaných rastrový obrázek prostředků ze spustitelného souboru aplikace a připojení k objektu rastrového obrázku.|
|[CBitmap::LoadMappedBitmap](#loadmappedbitmap)|Načte rastrový obrázek a barvy se mapuje na aktuální systémových barev.|
|[CBitmap::LoadOEMBitmap](#loadoembitmap)|Inicializuje objekt načtením předdefinované rastrového obrázku Windows a rastrový obrázek se připojuje k objektu.|
|[CBitmap::SetBitmapBits](#setbitmapbits)|Nastaví zadané bitové hodnoty bitů rastrový obrázek.|
|[CBitmap::SetBitmapDimension](#setbitmapdimension)|Přiřadí šířku a výšku rastrového obrázku v jednotkách milimetru 0,1.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CBitmap::operator HBITMAP](#operator_hbitmap)|Vrátí popisovač Windows připojené k `CBitmap` objektu.|

## <a name="remarks"></a>Poznámky

Použití `CBitmap` objektu, sestavte objekt, připojit se k němu s jedním z členské funkce inicializace popisovače rastrový obrázek a pak volat objektu členské funkce.

Další informace o použití grafických objektů, jako jsou `CBitmap`, naleznete v tématu [objektů grafiky](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBitmap`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

##  <a name="cbitmap"></a>  CBitmap::CBitmap

Vytvoří `CBitmap` objektu.

```
CBitmap();
```

### <a name="remarks"></a>Poznámky

Výsledný objekt musí inicializovat s jedním z inicializace členských funkcí.

##  <a name="createbitmap"></a>  CBitmap::CreateBitmap

Inicializuje paměti závislé na zařízení rastrový obrázek, který má nastavená šířka, výška a bitový vzor.

```
BOOL CreateBitmap(
    int nWidth,
    int nHeight,
    UINT nPlanes,
    UINT nBitcount,
    const void* lpBits);
```

### <a name="parameters"></a>Parametry

*nWidth*<br/>
Určuje šířku rastrového obrázku (v pixelech).

*nHeight*<br/>
Určuje výšku rastrového obrázku (v pixelech).

*nPlanes*<br/>
Určuje počet barevných rovin rastrového obrázku.

*nBitcount*<br/>
Určuje počet barev bitů na pixel zobrazení.

*lpBits*<br/>
Odkazuje na pole bajtů, které obsahuje počáteční rastrový obrázek bitové hodnoty. Pokud je hodnota NULL, je ponecháno nový rastrový obrázek Neinicializovaný.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Barvy rastrového obrázku buď *nPlanes* nebo *nBitcount* parametr by měl být nastaven na hodnotu 1. Pokud oba tyto parametry jsou nastavena na hodnotu 1, `CreateBitmap` vytvoří monochromatický rastrový obrázek.

I když pro zobrazovací zařízení nelze přímo vybrat rastrový obrázek, ji lze vybrat jako aktuální rastrový obrázek pro "paměti kontextu zařízení" s použitím [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) a zkopírován do kontextu libovolné kompatibilní zařízení s použitím [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) funkce.

Po dokončení se `CBitmap` objekt vytvořený pomocí `CreateBitmap` funkci, nejprve vybrat rastrový obrázek mimo kontext zařízení a pak odstranit `CBitmap` objektu.

Další informace najdete v popisu `bmBits` pole `BITMAP` struktury. [Rastrový OBRÁZEK](/windows/desktop/api/wingdi/ns-wingdi-tagbitmap) struktura je popsaný v části [CBitmap::CreateBitmapIndirect](#createbitmapindirect) členskou funkci.

##  <a name="createbitmapindirect"></a>  CBitmap::CreateBitmapIndirect

Inicializuje rastrový obrázek, který má šířku, výšku a bitový vzor (Pokud je zadaná) zadaný ve struktuře, na které odkazuje *lpBitmap*.

```
BOOL CreateBitmapIndirect(LPBITMAP lpBitmap);
```

### <a name="parameters"></a>Parametry

*lpBitmap*<br/>
Odkazuje [rastrový OBRÁZEK](/windows/desktop/api/wingdi/ns-wingdi-tagbitmap) strukturu, která obsahuje informace o rastrového obrázku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

I když pro zobrazovací zařízení nelze přímo vybrat rastrový obrázek, lze ji použít jako aktuální rastrový obrázek pro kontext zařízení paměti pomocí [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) a zkopírován do kontextu libovolné kompatibilní zařízení s použitím [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) nebo [CDC::StretchBlt](../../mfc/reference/cdc-class.md#stretchblt) funkce. ( [CDC::PatBlt](../../mfc/reference/cdc-class.md#patblt) funkce můžete zkopírovat rastrový obrázek pro aktuální štětec přímo do kontextu zařízení zobrazení.)

Pokud `BITMAP` struktury na které odkazují *lpBitmap* parametru byla vyplněna pomocí `GetObject` bity rastrového obrázku nejsou zadané funkce, a rastrového obrázku není inicializován. Inicializace rastrový obrázek, může aplikace používat funkce, jako [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) nebo [SetDIBits](/windows/desktop/api/wingdi/nf-wingdi-setdibits) bude kopírováno bity rastrový obrázek identifikovaný první parametr `CGdiObject::GetObject` do bitmapy vytvořil `CreateBitmapIndirect`.

Po dokončení se `CBitmap` objekt vytvořený pomocí `CreateBitmapIndirect` funkci, nejprve vybrat rastrový obrázek mimo kontext zařízení a pak odstranit `CBitmap` objektu.

##  <a name="createcompatiblebitmap"></a>  CBitmap::CreateCompatibleBitmap

Inicializuje rastrový obrázek, který je kompatibilní s zařízení určeného *primárního řadiče domény*.

```
BOOL CreateCompatibleBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Určuje kontext zařízení.

*nWidth*<br/>
Určuje šířku rastrového obrázku (v pixelech).

*nHeight*<br/>
Určuje výšku rastrového obrázku (v pixelech).

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Bitmapa má stejný počet barevných rovin nebo stejný formát bitů na pixel jako kontext zařízení. Jej lze vybrat jako aktuální rastrového obrázku pro všechny paměťové zařízení, která je kompatibilní s vlákna zadaného parametrem *primárního řadiče domény*.

Pokud *primárního řadiče domény* kontextu paměti zařízení, je vrácena bitmapa má stejný formát jako aktuálně vybraný rastrového obrázku v tomto kontextu zařízení. "Paměti kontextu zařízení" je blok paměti, která představuje zobrazovacím povrchu. Slouží k přípravě bitové kopie v paměti před jejich kopírování skutečné zobrazovacím povrchu kompatibilní zařízení.

Po vytvoření kontextu zařízení paměti GDI automaticky vybere monochromatický rastrový obrázek uložených pro něj.

Protože kontextu zařízení barva paměti může mít barvy nebo vybrané monochromatický rastrové obrázky, formát rastrového obrázku vrácené `CreateCompatibleBitmap` funkce není vždy stejná; formát kompatibilní rastrový obrázek pro kontext zařízení nonmemory je však vždy v Formát zařízení.

Po dokončení se `CBitmap` objekt vytvořený pomocí `CreateCompatibleBitmap` funkci, nejprve vybrat rastrový obrázek mimo kontext zařízení a pak odstranit `CBitmap` objektu.

##  <a name="creatediscardablebitmap"></a>  CBitmap::CreateDiscardableBitmap

Inicializuje discardable rastrový obrázek, který je kompatibilní s kontextem zařízení identifikovaný *primárního řadiče domény*.

```
BOOL CreateDiscardableBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Určuje kontext zařízení.

*nWidth*<br/>
Určuje šířku rastrového obrázku (v bitech).

*nHeight*<br/>
Určuje výšku rastrového obrázku (v bitech).

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Bitmapa má stejný počet barevných rovin nebo stejný formát bitů na pixel jako kontext zařízení. Aplikace můžete vybrat tato rastrového obrázku jako aktuální rastrový obrázek pro paměťového zařízení, která je kompatibilní s vlákna zadaného parametrem *primárního řadiče domény*.

Windows zahodit rastrový obrázek vytvořené touto funkcí pouze v případě, že aplikace nebyla vybrali ji do kontextu zobrazení. Pokud Windows zahodí rastrového obrázku, pokud není zaškrtnuto a později se aplikace pokusí vyberte to, [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) funkce vrátí hodnotu NULL.

Po dokončení se `CBitmap` objekt vytvořený pomocí `CreateDiscardableBitmap` funkci, nejprve vybrat rastrový obrázek mimo kontext zařízení a pak odstranit `CBitmap` objektu.

##  <a name="fromhandle"></a>  CBitmap::FromHandle

Vrací ukazatel `CBitmap` objektu, pokud Zadaný popisovač rastrového obrázku Windows GDI.

```
static CBitmap* PASCAL FromHandle(HBITMAP hBitmap);
```

### <a name="parameters"></a>Parametry

*hBitmap*<br/>
Určuje rastrového obrázku Windows GDI.

### <a name="return-value"></a>Návratová hodnota

Ukazatel `CBitmap` objekt Pokud úspěšné; jinak hodnota NULL.

### <a name="remarks"></a>Poznámky

Pokud `CBitmap` objekt už není připojen ke zpracování, dočasný `CBitmap` objekt se vytvoří a připojí. Tento dočasný `CBitmap` objektu je platná pouze v až při příštím má aplikace čas nečinnosti v jeho smyčkou událostí, na které čas všechny dočasné obrázek objekty budou odstraněny. Jinými slovy to je, že dočasný objekt platí pouze při zpracování zprávy jedno okno.

##  <a name="getbitmap"></a>  CBitmap::GetBitmap

Načte vlastnosti bitové kopie pro připojené rastrový obrázek.

```
int GetBitmap(BITMAP* pBitMap);
```

### <a name="parameters"></a>Parametry

*pBitMap*<br/>
Ukazatel [rastrový OBRÁZEK](/windows/desktop/api/wingdi/ns-wingdi-tagbitmap) struktura, která se zobrazí vlastnosti bitové kopie. Tento parametr nesmí mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud metoda byla úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

##  <a name="getbitmapbits"></a>  CBitmap::GetBitmapBits

Bitový vzor připojené rastrového obrázku se zkopíruje do zadané vyrovnávací paměti.

```
DWORD GetBitmapBits(
    DWORD dwCount,
    LPVOID lpBits) const;
```

### <a name="parameters"></a>Parametry

*dwCount*<br/>
Počet bajtů, které mají zkopírovat do vyrovnávací paměti.

*lpBits*<br/>
Ukazatel do vyrovnávací paměti, která bude dostávat rastrového obrázku.

### <a name="return-value"></a>Návratová hodnota

Počet bajtů, které jsou zkopírovány do vyrovnávací paměti, pokud metoda byla úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Použití [CBitmap::GetBitmap](#getbitmap) určit velikost požadované vyrovnávací paměti.

##  <a name="getbitmapdimension"></a>  CBitmap::GetBitmapDimension

Vrátí šířku a výšku rastrového obrázku.

```
CSize GetBitmapDimension() const;
```

### <a name="return-value"></a>Návratová hodnota

Šířku a výšku rastrového obrázku, měřenou v jednotkách milimetru 0,1. Výška se `cy` členem `CSize` objektu a šířka jsou v `cx` člen. Pokud rastrový obrázek šířku a výšku nebyly nastaveny pomocí `SetBitmapDimension`, vrácená hodnota je 0.

### <a name="remarks"></a>Poznámky

Výška a šířka jsou předpokládá, že jste dříve nastavili pomocí [SetBitmapDimension](#setbitmapdimension) členskou funkci.

##  <a name="loadbitmap"></a>  CBitmap::LoadBitmap

Načte prostředek rastrového obrázku s názvem podle *lpszResourceName* nebo identifikována číslem ID v *nIDResource* ze spustitelného souboru aplikace.

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Odkazuje na řetězec zakončený hodnotou null, který obsahuje název prostředku rastrového obrázku.

*nIDResource*<br/>
Určuje identifikační číslo prostředku prostředku rastrového obrázku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Načíst rastrového obrázku je připojen k `CBitmap` objektu.

Pokud rastrový obrázek identifikovaný *lpszResourceName* neexistuje nebo není dostatek paměti k načtení rastrový obrázek, funkce vrátí 0.

Můžete použít [CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) funkce Odstranit rastrový obrázek načetl `LoadBitmap` funkce, nebo `CBitmap` destruktor odstraní objekt za vás.

> [!CAUTION]
>  Než odstraníte objekt, ujistěte se, že není vybraná kontextu zařízení.

Následující rastrových obrázků, které byly přidány do Windows verze 3.1 nebo novější:

OBM_UPARRROWIOBM_DNARROWIOBM_RGARROWIOBM_LFARROWI

Tyto rastrové obrázky nejsou k dispozici v ovladače zařízení pro Windows verze 3.0 a starší. Úplný seznam rastrové obrázky a zobrazení jejich výskytu najdete v sadě Windows SDK.

##  <a name="loadmappedbitmap"></a>  CBitmap::LoadMappedBitmap

Voláním této členské funkce načíst bitmapu a přiřazení barev k aktuální systémových barev.

```
BOOL LoadMappedBitmap(
    UINT nIDBitmap,
    UINT nFlags = 0,
    LPCOLORMAP lpColorMap = NULL,
    int nMapSize = 0);
```

### <a name="parameters"></a>Parametry

*nIDBitmap*<br/>
ID prostředku rastrového obrázku.

*nFlags*<br/>
Příznak pro rastrový obrázek. Může být nula nebo CMB_MASKED.

*lpColorMap*<br/>
Ukazatel `COLORMAP` strukturu, která obsahuje informace o barvě potřebné k mapování rastrové obrázky. Pokud má parametr hodnotu NULL, funkce používá výchozí mapování barev.

*nMapSize*<br/>
Počet barev mapy odkazované *lpColorMap*.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení `LoadMappedBitmap` provede mapování barev používaných v glyfech tlačítko.

Informace o vytváření mapované rastrový obrázek, podívat se na funkci Windows [CreateMappedBitmap](http://go.microsoft.com/fwlink/p/?linkid=230562) a [COLORMAP](/windows/desktop/api/commctrl/ns-commctrl-_colormap) struktura v sadě Windows SDK.

##  <a name="loadoembitmap"></a>  CBitmap::LoadOEMBitmap

Načte předdefinované rastrový obrázek používá Windows.

```
BOOL LoadOEMBitmap(UINT nIDBitmap);
```

### <a name="parameters"></a>Parametry

*nIDBitmap*<br/>
Číslo ID předdefinovaného rastrového obrázku Windows. Možné hodnoty jsou uvedeny níže ze systému WINDOWS. V:

|||
|-|-|
|OBM_BTNCORNERS|OBM_OLD_RESTORE|
|OBM_BTSIZE|OBM_OLD_RGARROW|
|OBM_CHECK|OBM_OLD_UPARROW|
|OBM_CHECKBOXES|OBM_OLD_ZOOM|
|OBM_CLOSE|OBM_REDUCE|
|OBM_COMBO|OBM_REDUCED|
|OBM_DNARROW|OBM_RESTORE|
|OBM_DNARROWD|OBM_RESTORED|
|OBM_DNARROWI|OBM_RGARROW|
|OBM_LFARROW|OBM_RGARROWD|
|OBM_LFARROWD|OBM_RGARROWI|
|OBM_LFARROWI|OBM_SIZE|
|OBM_MNARROW|OBM_UPARROW|
|OBM_OLD_CLOSE|OBM_UPARROWD|
|OBM_OLD_DNARROW|OBM_UPARROW|
|OBM_OLD_LFARROW|OBM_ZOOM|
|OBM_OLD_REDUCE|OBM_ZOOMD|

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Rastrový obrázek názvy, které začínají OBM_OLD představují rastrové obrázky používané verze Windows starší než 3.0.

Všimněte si, že konstantní OEMRESOURCE musí být definovaná před včetně systému WINDOWS. H, aby bylo možné použít některý z **OBM_** konstanty.

##  <a name="operator_hbitmap"></a>  CBitmap::operator HBITMAP

Tento operátor se získat popisovač Windows GDI připojené `CBitmap` objektu.

```
operator HBITMAP() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud úspěchu popisovač objektů Windows GDI reprezentována `CBitmap` objektu; v opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

Tento operátor je operátor přetypování, která podporuje používání s přímým přístupem `HBITMAP` objektu.

Další informace o použití grafických objektů najdete v tématu [objektů grafiky](/windows/desktop/gdi/graphic-objects) v sadě Windows SDK.

##  <a name="setbitmapbits"></a>  CBitmap::SetBitmapBits

Nastaví bity rastrový obrázek bitové hodnoty poskytnuté *lpBits*.

```
DWORD SetBitmapBits(
    DWORD dwCount,
    const void* lpBits);
```

### <a name="parameters"></a>Parametry

*dwCount*<br/>
Určuje počet bajtů, na které odkazuje *lpBits*.

*lpBits*<br/>
Odkazuje na pole BAJTŮ, který obsahuje pixel hodnoty, které mají být zkopírován do `CBitmap` objektu. V pořadí rastrového obrázku, abyste mohli správně vykreslit jeho image tak, aby odpovídal na výšku, šířku a barvu hodnoty hloubka, která jste zadali při vytváření instance cbitmap – formátování hodnoty. Další informace najdete v tématu [CBitmap::CreateBitmap](#createbitmap).

### <a name="return-value"></a>Návratová hodnota

Počet bajtů použitých v nastavení rastrové bity; 0, pokud funkce selže.

##  <a name="setbitmapdimension"></a>  CBitmap::SetBitmapDimension

Přiřadí šířku a výšku rastrového obrázku v jednotkách milimetru 0,1.

```
CSize SetBitmapDimension(
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parametry

*nWidth*<br/>
Určuje šířku rastrového obrázku (v jednotkách 0,1 milimetru).

*nHeight*<br/>
Určuje výšku rastrového obrázku (v jednotkách 0,1 milimetru).

### <a name="return-value"></a>Návratová hodnota

Předchozí dimenze rastrového obrázku. Výška bude v `cy` členské proměnné `CSize` a šířky objektu je v `cx` členské proměnné.

### <a name="remarks"></a>Poznámky

Rozhraní GDI nepoužívá tyto hodnoty s výjimkou a vracet je aplikace zavolá [GetBitmapDimension](#getbitmapdimension) členskou funkci.

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC MDI](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject – třída](../../mfc/reference/cgdiobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
