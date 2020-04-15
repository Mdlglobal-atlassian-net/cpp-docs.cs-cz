---
title: Třída CAtlFileMappingBase
ms.date: 11/04/2016
f1_keywords:
- CAtlFileMappingBase
- ATLFILE/ATL::CAtlFileMappingBase
- ATLFILE/ATL::CAtlFileMappingBase::CAtlFileMappingBase
- ATLFILE/ATL::CAtlFileMappingBase::CopyFrom
- ATLFILE/ATL::CAtlFileMappingBase::GetData
- ATLFILE/ATL::CAtlFileMappingBase::GetHandle
- ATLFILE/ATL::CAtlFileMappingBase::GetMappingSize
- ATLFILE/ATL::CAtlFileMappingBase::MapFile
- ATLFILE/ATL::CAtlFileMappingBase::MapSharedMem
- ATLFILE/ATL::CAtlFileMappingBase::OpenMapping
- ATLFILE/ATL::CAtlFileMappingBase::Unmap
helpviewer_keywords:
- CAtlFileMappingBase class
ms.assetid: be555723-2790-4f57-a8fb-be4d68460775
ms.openlocfilehash: ae790cf1248c78ff9aa70c0e586f86af6c8f3b9a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318946"
---
# <a name="catlfilemappingbase-class"></a>Třída CAtlFileMappingBase

Tato třída představuje soubor mapovaný v paměti.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CAtlFileMappingBase
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)|Konstruktor|
|[CAtlFileMappingBase::~CAtlFileMappingBase](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlFileMappingBase::CopyFrom](#copyfrom)|Volání této metody ke kopírování z objektu mapování souborů.|
|[CAtlFileMappingBase::GetData](#getdata)|Volání této metody získat data z objektu mapování souborů.|
|[CAtlFileMappingBase::GetHandle](#gethandle)|Volání této metody vrátit popisovač souboru.|
|[CAtlFileMappingBase::GetMappingSize](#getmappingsize)|Volání této metody získat velikost mapování z objektu mapování souborů.|
|[CAtlFileMappingBase::MapFile](#mapfile)|Volání této metody k vytvoření objektu mapování souborů.|
|[CAtlFileMappingBase::MapSharedMem](#mapsharedmem)|Volání této metody k vytvoření objektu mapování souborů, který umožňuje úplný přístup ke všem procesům.|
|[CAtlFileMappingBase::OpenMapping](#openmapping)|Volání této metody vrátit popisovač objektu mapování souborů.|
|[CAtlFileMappingBase::Odmapovat](#unmap)|Volání této metody zrušit mapování objektu mapování souborů.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CAtlFileMappingBase::operátor =](#operator_eq)|Nastaví aktuální objekt mapování souborů na jiný objekt mapování souborů.|

## <a name="remarks"></a>Poznámky

Mapování souborů je přidružení obsahu souboru k části virtuálního adresového prostoru procesu. Tato třída poskytuje metody pro vytváření objektů mapování souborů, které umožňují programům snadný přístup a sdílení dat.

Další informace naleznete v [tématu Mapování souborů](/windows/win32/Memory/file-mapping) v sadě Windows SDK.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlfile.h

## <a name="catlfilemappingbasecatlfilemappingbase"></a><a name="catlfilemappingbase"></a>CAtlFileMappingBase::CAtlFileMappingBase

Konstruktor

```
CAtlFileMappingBase(CAtlFileMappingBase& orig);
CAtlFileMappingBase() throw();
```

### <a name="parameters"></a>Parametry

*Orig*<br/>
Původní objekt mapování souborů, který chcete zkopírovat, chcete-li vytvořit nový objekt.

### <a name="remarks"></a>Poznámky

Vytvoří nový objekt mapování souborů, volitelně pomocí existujícího objektu. Je stále nutné volat [CAtlFileMappingBase::MapFile](#mapfile) otevřít nebo vytvořit objekt mapování souborů pro určitý soubor.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#71](../../atl/codesnippet/cpp/catlfilemappingbase-class_1.cpp)]

## <a name="catlfilemappingbasecatlfilemappingbase"></a><a name="dtor"></a>CAtlFileMappingBase::~CAtlFileMappingBase

Destruktor.

```
~CAtlFileMappingBase() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny prostředky přidělené třídou a zavolá metodu [CAtlFileMappingBase::Unmap.](#unmap)

## <a name="catlfilemappingbasecopyfrom"></a><a name="copyfrom"></a>CAtlFileMappingBase::CopyFrom

Volání této metody ke kopírování z objektu mapování souborů.

```
HRESULT CopyFrom(CAtlFileMappingBase& orig) throw();
```

### <a name="parameters"></a>Parametry

*Orig*<br/>
Původní objekt mapování souborů, ze který chcete kopírovat.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="catlfilemappingbasegetdata"></a><a name="getdata"></a>CAtlFileMappingBase::GetData

Volání této metody získat data z objektu mapování souborů.

```
void* GetData() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na data.

## <a name="catlfilemappingbasegethandle"></a><a name="gethandle"></a>CAtlFileMappingBase::GetHandle

Volání této metody vrátit popisovač objektu mapování souborů.

```
HANDLE GetHandle() throw ();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač objektu mapování souborů.

## <a name="catlfilemappingbasegetmappingsize"></a><a name="getmappingsize"></a>CAtlFileMappingBase::GetMappingSize

Volání této metody získat velikost mapování z objektu mapování souborů.

```
SIZE_T GetMappingSize() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí velikost mapování.

### <a name="example"></a>Příklad

Viz příklad pro [CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase).

## <a name="catlfilemappingbasemapfile"></a><a name="mapfile"></a>CAtlFileMappingBase::MapFile

Volání této metody otevřít nebo vytvořit objekt mapování souborů pro zadaný soubor.

```
HRESULT MapFile(
    HANDLE hFile,
    SIZE_T nMappingSize = 0,
    ULONGLONG nOffset = 0,
    DWORD dwMappingProtection = PAGE_READONLY,
    DWORD dwViewDesiredAccess = FILE_MAP_READ) throw();
```

### <a name="parameters"></a>Parametry

*hSoubor*<br/>
Zpracovat soubor, ze kterého chcete vytvořit objekt mapování. *hSoubor* musí být platný a nelze jej nastavit na INVALID_HANDLE_VALUE.

*nMappingSize*<br/>
Velikost mapování. Pokud 0, maximální velikost objektu mapování souborů se rovná aktuální velikost souboru identifikované *hFile.*

*nOffset*<br/>
Posun souboru, kde má mapování začínat. Hodnota posunu musí být násobkem rozlišovací schopnosti přidělení paměti systému.

*ochrana dwMappingProtection*<br/>
Ochrana požadovaná pro zobrazení souboru při mapování souboru. Viz *flProtect* v [programu CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga) v sadě Windows SDK.

*dwViewDesiredAccess*<br/>
Určuje typ přístupu k zobrazení souborů a tedy ochranu stránek mapovaných souborem. Viz *dwDesiredAccess* v [MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) v sdk systému Windows.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Po vytvoření objektu mapování souborů nesmí velikost souboru překročit velikost objektu mapování souborů. Pokud ano, nebude k dispozici veškerý obsah souboru ke sdílení. Další podrobnosti naleznete v [tématech CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga) a [MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) v sadě Windows SDK.

### <a name="example"></a>Příklad

Viz příklad pro [CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase).

## <a name="catlfilemappingbasemapsharedmem"></a><a name="mapsharedmem"></a>CAtlFileMappingBase::MapSharedMem

Volání této metody k vytvoření objektu mapování souborů, který umožňuje úplný přístup ke všem procesům.

```
HRESULT MapSharedMem(
    SIZE_T nMappingSize,
    LPCTSTR szName,
    BOOL* pbAlreadyExisted = NULL,
    LPSECURITY_ATTRIBUTES lpsa = NULL,
    DWORD dwMappingProtection = PAGE_READWRITE,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```

### <a name="parameters"></a>Parametry

*nMappingSize*<br/>
Velikost mapování. Pokud 0, maximální velikost objektu mapování souborů se rovná aktuální velikosti objektu mapování souborů identifikovaného *szName*.

*szJméno*<br/>
Název objektu mapování.

*pbAlreadyExisted*<br/>
Odkazuje na hodnotu BOOL, která je nastavena na hodnotu PRAVDA, pokud objekt mapování již existoval.

*LPSA*<br/>
Ukazatel na `SECURITY_ATTRIBUTES` strukturu, která určuje, zda vrácený popisovač může být zděděn podřízenými procesy. Viz *lpAttributes* in [CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga) v sadě Windows SDK.

*ochrana dwMappingProtection*<br/>
Ochrana požadovaná pro zobrazení souboru, když je soubor mapován. Viz *flProtect* in `CreateFileMapping` v sadě Windows SDK.

*dwViewDesiredAccess*<br/>
Určuje typ přístupu k zobrazení souborů a tedy ochranu stránek mapovaných souborem. Viz *dwDesiredAccess* v [MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) v sdk systému Windows.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

`MapShareMem`umožňuje sdílení existujícího objektu mapování souborů vytvořeného pomocí [funkce CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga)mezi procesy.

## <a name="catlfilemappingbaseopenmapping"></a><a name="openmapping"></a>CAtlFileMappingBase::OpenMapping

Voláním této metody otevřete pojmenovaný objekt mapování souborů pro zadaný soubor.

```
HRESULT OpenMapping(
    LPCTSTR szName,
    SIZE_T nMappingSize,
    ULONGLONG nOffset = 0,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```

### <a name="parameters"></a>Parametry

*szJméno*<br/>
Název objektu mapování. Pokud je otevřený popisovač objektu mapování souborů podle tohoto názvu a popisovač zabezpečení na objektu mapování není v konfliktu s parametrem *dwViewDesiredAccess,* otevřená operace proběhne úspěšně.

*nMappingSize*<br/>
Velikost mapování. Pokud 0, maximální velikost objektu mapování souborů se rovná aktuální velikosti objektu mapování souborů identifikovaného *szName*.

*nOffset*<br/>
Posun souboru, kde má mapování začínat. Hodnota posunu musí být násobkem rozlišovací schopnosti přidělení paměti systému.

*dwViewDesiredAccess*<br/>
Určuje typ přístupu k zobrazení souborů a tedy ochranu stránek mapovaných souborem. Viz *dwDesiredAccess* v [MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) v sdk systému Windows.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

V sestaveních ladění dojde k chybě kontrolního výrazu, pokud jsou vstupní parametry neplatné.

## <a name="catlfilemappingbaseoperator-"></a><a name="operator_eq"></a>CAtlFileMappingBase::operátor =

Nastaví aktuální objekt mapování souborů na jiný objekt mapování souborů.

```
CAtlFileMappingBase& operator=(CAtlFileMappingBase& orig);
```

### <a name="parameters"></a>Parametry

*Orig*<br/>
Aktuální objekt mapování souborů.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na aktuální objekt.

## <a name="catlfilemappingbaseunmap"></a><a name="unmap"></a>CAtlFileMappingBase::Odmapovat

Volání této metody zrušit mapování objektu mapování souborů.

```
HRESULT Unmap() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Další podrobnosti najdete v [tématu UnmapViewOfFile](/windows/win32/api/memoryapi/nf-memoryapi-unmapviewoffile) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Třída CAtlFileMapping](../../atl/reference/catlfilemapping-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
