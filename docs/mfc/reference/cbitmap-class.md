---
title: "CBitmap – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 33e0ca4c92d22d8afaed4523a7f274b6b5d20a2b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cbitmap-class"></a>CBitmap – třída
Zapouzdří grafiky zařízení rozhraní GDI rastrového obrázku a poskytuje členské funkce k manipulaci s bitové mapy.  
  
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
  
|Název|Popis|  
|----------|-----------------|  
|[CBitmap::CreateBitmap](#createbitmap)|Inicializuje objekt s paměti závislé na zařízení rastrový obrázek, který má zadaný šířky, výšky a bitový.|  
|[CBitmap::CreateBitmapIndirect](#createbitmapindirect)|Inicializuje objekt s bitmap s šířky, výšky a bitový (Pokud je zadaná) v **rastrový OBRÁZEK** struktura.|  
|[CBitmap::CreateCompatibleBitmap](#createcompatiblebitmap)|Inicializuje objekt bitmapa, takže je kompatibilní s určitým zařízením.|  
|[CBitmap::CreateDiscardableBitmap](#creatediscardablebitmap)|Inicializuje objekt s discardable rastrový obrázek, který je kompatibilní s určitým zařízením.|  
|[CBitmap::FromHandle](#fromhandle)|Vrátí ukazatel na `CBitmap` objektu, pokud Zadaný popisovač se systémem Windows `HBITMAP` rastrového obrázku.|  
|[CBitmap::GetBitmap](#getbitmap)|Vyplní celé **rastrový OBRÁZEK** struktura s informacemi o bitové mapy.|  
|[CBitmap::GetBitmapBits](#getbitmapbits)|Službu bits Zadaný rastrový obrázek zkopíruje do zadané vyrovnávací paměti.|  
|[CBitmap::GetBitmapDimension](#getbitmapdimension)|Vrátí šířka a výška bitové mapy. Výška a šířka jsou předpokládá, že byla dříve nastavena [SetBitmapDimension](#setbitmapdimension) – členská funkce.|  
|[CBitmap::LoadBitmap](#loadbitmap)|Inicializuje objekt načítání prostředků s názvem rastrového obrázku z spustitelný soubor aplikace a připojení k objektu bitové mapy.|  
|[CBitmap::LoadMappedBitmap](#loadmappedbitmap)|Načte rastrový obrázek a barvy se mapuje na aktuální barvy systému.|  
|[CBitmap::LoadOEMBitmap](#loadoembitmap)|Inicializuje objekt načtením předdefinované rastrového a bitmapy se připojuje k objektu.|  
|[CBitmap::SetBitmapBits](#setbitmapbits)|Nastaví službu bits bitmapy zadaný bitových hodnot.|  
|[CBitmap::SetBitmapDimension](#setbitmapdimension)|Rastrový obrázek v jednotkách 0,1 milimetru přiřadí šířku a výšku.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CBitmap::operator HBITMAP](#operator_hbitmap)|Vrátí popisovač Windows připojené k `CBitmap` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Použít `CBitmap` objektu, vytvořit objekt, připojte ji můžete jedním inicializace členské funkce popisovač rastrového obrázku a pak volat objektu členské funkce.  
  
 Další informace o použití grafických objektů jako `CBitmap`, najdete v části [obrázek objekty](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CBitmap`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="cbitmap"></a>CBitmap::CBitmap  
 Vytvoří `CBitmap` objektu.  
  
```  
CBitmap();
```  
  
### <a name="remarks"></a>Poznámky  
 Výsledný objekt musí být inicializován s jedním z členské funkce inicializace.  
  
##  <a name="createbitmap"></a>CBitmap::CreateBitmap  
 Inicializuje paměti závislé na zařízení rastrový obrázek, který má zadaný šířky, výšky a bitový.  
  
```  
BOOL CreateBitmap(
    int nWidth,  
    int nHeight,  
    UINT nPlanes,  
    UINT nBitcount,  
    const void* lpBits);
```  
  
### <a name="parameters"></a>Parametry  
 `nWidth`  
 Určuje šířku bitovou mapu (v pixelech).  
  
 `nHeight`  
 Určuje výšku bitovou mapu (v pixelech).  
  
 `nPlanes`  
 Určuje počet barevných rovin rastrového obrázku.  
  
 `nBitcount`  
 Určuje počet barev bitů na pixel zobrazení.  
  
 `lpBits`  
 Bodů na pole bajtů, která obsahuje hodnoty bit počáteční rastrového obrázku. Pokud je **NULL**, je ponechán nové bitmapy Neinicializovaný.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Barva rastrového obrázku buď `nPlanes` nebo `nBitcount` parametr by měl být nastaven na hodnotu 1. Pokud jsou oba tyto parametry nastavit hodnotu 1, `CreateBitmap` vytvoří černobílý rastrového obrázku.  
  
 Přestože rastru není k dispozici přímo pro zobrazení zařízení, lze ji použít jako aktuální rastrový obrázek "paměti kontextu zařízení" s použitím [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) a zkopírovali do kontextu žádné kompatibilní zařízení pomocí [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) funkce.  
  
 Po dokončení se `CBitmap` objekt vytvořený `CreateBitmap` fungovat, nejprve vyberte bitovou mapu mimo kontext zařízení a pak odstraňte `CBitmap` objektu.  
  
 Další informace najdete v tématu Popis **bmBits** pole **rastrový OBRÁZEK** struktura. [Rastrový OBRÁZEK](../../mfc/reference/bitmap-structure.md) struktura je popsaný v části [CBitmap::CreateBitmapIndirect](#createbitmapindirect) – členská funkce.  
  
##  <a name="createbitmapindirect"></a>CBitmap::CreateBitmapIndirect  
 Inicializuje rastrový obrázek, který má šířky, výšky a bitový (Pokud je zadaná) zadaný ve struktuře, na kterou odkazuje `lpBitmap`.  
  
```  
BOOL CreateBitmapIndirect(LPBITMAP lpBitmap);
```  
  
### <a name="parameters"></a>Parametry  
 `lpBitmap`  
 Odkazuje na [rastrový OBRÁZEK](../../mfc/reference/bitmap-structure.md) struktura, která obsahuje informace o bitové mapy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Přestože rastru není k dispozici přímo pro zobrazení zařízení, lze ji použít jako aktuální rastrový obrázek kontextu zařízení paměti pomocí [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) a zkopírovali do kontextu žádné kompatibilní zařízení pomocí [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) nebo [CDC::StretchBlt](../../mfc/reference/cdc-class.md#stretchblt) funkce. ( [CDC::PatBlt](../../mfc/reference/cdc-class.md#patblt) funkce můžete zkopírovat bitovou mapu pro aktuální štětce přímo do kontextu zobrazení zařízení.)  
  
 Pokud **rastrový OBRÁZEK** struktura na kterou odkazuje `lpBitmap` parametr bylo vyplněno pomocí `GetObject` funkce, nejsou zadané bity bitovou mapu a rastrového obrázku není inicializován. K chybě při inicializaci bitovou mapu, aplikace můžete použít funkci, jako [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) nebo [SetDIBits](http://msdn.microsoft.com/library/windows/desktop/dd162973) zkopírujte bity z rastrový obrázek identifikovaný první parametr `CGdiObject::GetObject` pro bitovou mapu vytvořené `CreateBitmapIndirect`.  
  
 Po dokončení se `CBitmap` objektu vytvořeny s `CreateBitmapIndirect` fungovat, nejprve vyberte bitovou mapu mimo kontext zařízení a pak odstraňte `CBitmap` objektu.  
  
##  <a name="createcompatiblebitmap"></a>CBitmap::CreateCompatibleBitmap  
 Inicializuje rastrový obrázek, který je kompatibilní s do zařízení určeného `pDC`.  
  
```  
BOOL CreateCompatibleBitmap(
    CDC* pDC,  
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Určuje kontextu zařízení.  
  
 `nWidth`  
 Určuje šířku bitovou mapu (v pixelech).  
  
 `nHeight`  
 Určuje výšku bitovou mapu (v pixelech).  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Bitmapy má stejný počet barevných rovin nebo stejný formát jako kontext zadané zařízení bitů na pixel. Lze ji použít jako aktuální rastrový obrázek paměťové zařízení, který je kompatibilní s určenému `pDC`.  
  
 Pokud `pDC` kontextu paměti zařízení, je vrácena rastrového obrázku má stejný formát jako aktuálně vybrané rastrový obrázek v tomto kontextu zařízení. "Paměti kontextu zařízení" je blok paměti, která představuje prostor pro zobrazení. Může sloužit k přípravě bitové kopie v paměti před kopírováním je na povrch skutečné zobrazení kompatibilní zařízení.  
  
 Při vytváření kontextu zařízení paměti GDI automaticky vybere černobílý uložených rastrový obrázek pro ni.  
  
 Vzhledem k tomu, že kontextu barva paměti zařízení může mít barvu nebo černobílý bitmap vybrána, formát bitmapy vrácený `CreateCompatibleBitmap` funkce není vždy stejná; však formát kompatibilní rastrový obrázek kontextu nonmemory zařízení je vždy v Formát zařízení.  
  
 Po dokončení se `CBitmap` objektu vytvořeny s `CreateCompatibleBitmap` fungovat, nejprve vyberte bitovou mapu mimo kontext zařízení a pak odstraňte `CBitmap` objektu.  
  
##  <a name="creatediscardablebitmap"></a>CBitmap::CreateDiscardableBitmap  
 Inicializuje discardable rastrový obrázek, který je kompatibilní s kontextu zařízení identifikovaný `pDC`.  
  
```  
BOOL CreateDiscardableBitmap(
    CDC* pDC,  
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Určuje kontextu zařízení.  
  
 `nWidth`  
 Určuje šířku bitovou mapu (v bits).  
  
 `nHeight`  
 Určuje výšku (v bitech) bitové mapy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Bitmapy má stejný počet barevných rovin nebo stejný formát jako kontext zadané zařízení bitů na pixel. Aplikaci můžete vybrat tento rastrový obrázek jako aktuální rastrový obrázek paměti zařízení, který je kompatibilní s určenému `pDC`.  
  
 Windows zahodit rastrového obrázku vytvořeného pomocí této funkce pouze v případě, že aplikace nebyla vybrána do kontextu zobrazení. Pokud Windows zahodí bitové mapy, pokud není vybrána a později se aplikace pokusí, vyberte [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) funkce vrátí **NULL**.  
  
 Po dokončení se `CBitmap` objektu vytvořeny s `CreateDiscardableBitmap` fungovat, nejprve vyberte bitovou mapu mimo kontext zařízení a pak odstraňte `CBitmap` objektu.  
  
##  <a name="fromhandle"></a>CBitmap::FromHandle  
 Vrátí ukazatel na `CBitmap` objektu, pokud Zadaný popisovač pro rastrový obrázek GDI systému Windows.  
  
```  
static CBitmap* PASCAL FromHandle(HBITMAP hBitmap);
```  
  
### <a name="parameters"></a>Parametry  
 `hBitmap`  
 Určuje rastrový obrázek GDI systému Windows.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `CBitmap` objekt, je-li úspěšná, jinak hodnota **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `CBitmap` objekt není už připojený k popisovač dočasného `CBitmap` objekt se vytvoří a připojené. Toto dočasný `CBitmap` je objekt platný pouze dokud příště aplikace má čas nečinnosti v jeho událostí smyčky, na který čas všechny dočasné obrázek objekty jsou odstraněny. Jinými slovy to je, že dočasný objekt platí pouze při zpracování zprávy jeden interval.  
  
##  <a name="getbitmap"></a>CBitmap::GetBitmap  
 Načte vlastnosti bitové kopie pro připojené rastrového obrázku.  
  
```  
int GetBitmap(BITMAP* pBitMap);
```  
  
### <a name="parameters"></a>Parametry  
 `pBitMap`  
 Ukazatel na [rastrový OBRÁZEK struktura](../../mfc/reference/bitmap-structure.md) struktura, která se zobrazí vlastnosti bitové kopie. Tento parametr nesmí být `NULL`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud metoda byla úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getbitmapbits"></a>CBitmap::GetBitmapBits  
 Bitový připojené bitmapy zkopíruje do zadané vyrovnávací paměti.  
  
```  
DWORD GetBitmapBits(
    DWORD dwCount,  
    LPVOID lpBits) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `dwCount`  
 Počet bajtů, které mají zkopírovat do vyrovnávací paměti.  
  
 `lpBits`  
 Ukazatel do vyrovnávací paměti, která bude přijímat bitové mapy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet bajtů, které jsou zkopírovány do vyrovnávací paměti, pokud metoda byla úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Použití [CBitmap::GetBitmap](#getbitmap) k určení velikosti požadované vyrovnávací paměti.  
  
##  <a name="getbitmapdimension"></a>CBitmap::GetBitmapDimension  
 Vrátí šířka a výška bitové mapy.  
  
```  
CSize GetBitmapDimension() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Šířka a výška rastrového obrázku, měřená v 0,1 milimetru jednotky. Výška je v **cy** členem `CSize` objekt a šířka je v **cx** člen. Pokud rastrový obrázek šířku a výšku nebyla nastavena pomocí `SetBitmapDimension`, vrácená hodnota je 0.  
  
### <a name="remarks"></a>Poznámky  
 Výška a šířka jsou předpokládá, že byla dříve nastavena pomocí [SetBitmapDimension](#setbitmapdimension) – členská funkce.  
  
##  <a name="loadbitmap"></a>CBitmap::LoadBitmap  
 Načte prostředek rastrový obrázek s názvem podle `lpszResourceName` nebo určený podle čísla ID v `nIDResource` z spustitelný soubor aplikace.  
  
```  
BOOL LoadBitmap(LPCTSTR lpszResourceName);  
BOOL LoadBitmap(UINT nIDResource);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszResourceName`  
 Odkazuje na řetězec ukončené hodnotou null, který obsahuje název prostředku rastrového obrázku.  
  
 `nIDResource`  
 Určuje počet prostředků ID prostředku bitové mapy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Načíst rastrového obrázku je připojen k `CBitmap` objektu.  
  
 Pokud bitmapy identifikovaný `lpszResourceName` neexistuje nebo pokud dojde k načtení rastrového obrázku není dostatek paměti, funkce vrátí hodnotu 0.  
  
 Můžete použít [CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) funkce Odstranit bitové mapy načteny `LoadBitmap` funkce, nebo `CBitmap` destruktor odstraní objekt za vás.  
  
> [!CAUTION]
>  Před odstraněním objekt, ujistěte se, že není vybrána v kontextu zařízení.  
  
 Následující rastrových obrázků, které byly přidány do systému Windows verze 3.1 nebo novější:  
  
 **OBM_UPARRROWIOBM_DNARROWIOBM_RGARROWIOBM_LFARROWI**  
  
 Tyto rastrové obrázky nejsou k dispozici v ovladače zařízení pro Windows verze 3.0 a starší. Úplný seznam rastrové obrázky a zobrazení jejich vzhled najdete v části Windows SDK.  
  
##  <a name="loadmappedbitmap"></a>CBitmap::LoadMappedBitmap  
 Volání této funkce člen se načíst rastrový obrázek a mapování barvy na aktuální barvy systému.  
  
```  
BOOL LoadMappedBitmap(
    UINT nIDBitmap,  
    UINT nFlags = 0,  
    LPCOLORMAP lpColorMap = NULL,  
    int nMapSize = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDBitmap`  
 ID prostředku bitové mapy.  
  
 `nFlags`  
 Příznak pro rastrový obrázek. Může být nula nebo **CMB_MASKED**.  
  
 `lpColorMap`  
 Ukazatel **COLORMAP** struktura, která obsahuje barvu informace potřebné k mapování rastrových obrázků. Pokud tento parametr je **NULL**, funkce, která používá výchozí mapování barev.  
  
 *nMapSize*  
 Počet barev mapy na kterou odkazuje `lpColorMap`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení `LoadMappedBitmap` namapujete barvy běžně používané v tlačítko glyfů.  
  
 Informace o vytváření namapované rastrového obrázku, najdete v části funkce systému Windows [CreateMappedBitmap](http://go.microsoft.com/fwlink/linkid=230562) a [COLORMAP](http://msdn.microsoft.com/library/windows/desktop/bb760448) struktura ve Windows SDK.  
  
##  <a name="loadoembitmap"></a>CBitmap::LoadOEMBitmap  
 Načte předdefinované bitmapy používaná systémem Windows.  
  
```  
BOOL LoadOEMBitmap(UINT nIDBitmap);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDBitmap`  
 Identifikační číslo předdefinované rastrového obrázku. Možné hodnoty jsou uvedeny níže ze systému WINDOWS. V:  
  
|||  
|-|-|  
|**OBM_BTNCORNERS**|**OBM_OLD_RESTORE**|  
|**OBM_BTSIZE**|**OBM_OLD_RGARROW**|  
|**OBM_CHECK**|**OBM_OLD_UPARROW**|  
|**OBM_CHECKBOXES**|**OBM_OLD_ZOOM**|  
|**OBM_CLOSE**|**OBM_REDUCE**|  
|**OBM_COMBO**|**OBM_REDUCED**|  
|**OBM_DNARROW**|**OBM_RESTORE**|  
|**OBM_DNARROWD**|**OBM_RESTORED**|  
|**OBM_DNARROWI**|**OBM_RGARROW**|  
|**OBM_LFARROW**|**OBM_RGARROWD**|  
|**OBM_LFARROWD**|**OBM_RGARROWI**|  
|**OBM_LFARROWI**|**OBM_SIZE**|  
|**OBM_MNARROW**|**OBM_UPARROW**|  
|**OBM_OLD_CLOSE**|**OBM_UPARROWD**|  
|**OBM_OLD_DNARROW**|**OBM_UPARROW**|  
|**OBM_OLD_LFARROW**|**OBM_ZOOM**|  
|**OBM_OLD_REDUCE**|**OBM_ZOOMD**|  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Bitmap – názvy, které začínají **OBM_OLD** představují rastrové obrázky používané verze Windows starší než 3.0.  
  
 Všimněte si, že konstanta **OEMRESOURCE** musí být definovaná před včetně systému WINDOWS. H, aby bylo možné používat **OBM_** konstanty.  
  
##  <a name="operator_hbitmap"></a>CBitmap::operator HBITMAP  
 Tento operátor. použijte k získání připojené popisovač GDI systému Windows `CBitmap` objektu.  
  
```  
operator HBITMAP() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud úspěšné, popisovač pro objekt Windows GDI reprezentována `CBitmap` objektu; v opačném případě **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Operátor je operátor přetypování, který podporuje přímý použití `HBITMAP` objektu.  
  
 Další informace o použití grafických objektů najdete v tématu [obrázek objekty](http://msdn.microsoft.com/library/windows/desktop/dd144962) ve Windows SDK.  
  
##  <a name="setbitmapbits"></a>CBitmap::SetBitmapBits  
 Nastaví službu bits bitmapy bitových hodnot poskytují `lpBits`.  
  
```  
DWORD SetBitmapBits(
    DWORD dwCount,  
    const void* lpBits);
```  
  
### <a name="parameters"></a>Parametry  
 `dwCount`  
 Určuje počet bajtů, na kterou odkazuje `lpBits`.  
  
 `lpBits`  
 Odkazuje na **BAJTŮ** pole, které obsahuje hodnoty pixelů zkopírovat `CBitmap` objektu. Aby rastrového obrázku, abyste mohli k vykreslení jeho image správně musí být formátována hodnoty tak, aby odpovídala hodnoty hloubka výška a šířka barev, které jste zadali při vytvoření CBitmap instance. Další informace najdete v tématu [CBitmap::CreateBitmap](#createbitmap).  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet bajtů použitých v nastavení bits rastrového obrázku; 0, pokud funkce se nezdaří.  
  
##  <a name="setbitmapdimension"></a>CBitmap::SetBitmapDimension  
 Rastrový obrázek v jednotkách 0,1 milimetru přiřadí šířku a výšku.  
  
```  
CSize SetBitmapDimension(
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>Parametry  
 `nWidth`  
 Určuje šířku rastrový obrázek (v jednotkách 0,1 milimetru).  
  
 `nHeight`  
 Určuje výšku rastrový obrázek (v jednotkách 0,1 milimetru).  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí dimenze rastrového obrázku. Výška je v **cy** členské proměnné `CSize` a šířky objektu je v **cx** členské proměnné.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní GDI nepoužívá tyto hodnoty, s výjimkou a vracet je aplikace zavolá [GetBitmapDimension](#getbitmapdimension) – členská funkce.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC MDI](../../visual-cpp-samples.md)   
 [CGdiObject – třída](../../mfc/reference/cgdiobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)

