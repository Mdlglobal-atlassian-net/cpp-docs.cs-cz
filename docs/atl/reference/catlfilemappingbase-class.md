---
title: CAtlFileMappingBase Class
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
ms.openlocfilehash: 3d9627c7a19cccc0cd3aec46d71b23c8a84711bf
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497774"
---
# <a name="catlfilemappingbase-class"></a>CAtlFileMappingBase Class

Tato třída reprezentuje soubor mapované paměti.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CAtlFileMappingBase
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)|Konstruktor|
|[CAtlFileMappingBase::~CAtlFileMappingBase](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CAtlFileMappingBase::CopyFrom](#copyfrom)|Voláním této metody můžete kopírovat z objektu mapování souborů.|
|[CAtlFileMappingBase::GetData](#getdata)|Voláním této metody získáte data z objektu mapování souborů.|
|[CAtlFileMappingBase::GetHandle](#gethandle)|Voláním této metody vrátíte popisovač souboru.|
|[CAtlFileMappingBase::GetMappingSize](#getmappingsize)|Voláním této metody získáte velikost mapování z objektu mapování souborů.|
|[CAtlFileMappingBase::MapFile](#mapfile)|Zavolejte tuto metodu pro vytvoření objektu mapování souborů.|
|[CAtlFileMappingBase::MapSharedMem](#mapsharedmem)|Voláním této metody vytvoříte objekt mapování souborů, který umožňuje úplný přístup ke všem procesům.|
|[CAtlFileMappingBase::OpenMapping](#openmapping)|Voláním této metody vrátí popisovač objektu mapování souborů.|
|[CAtlFileMappingBase::Unmap](#unmap)|Zavolejte tuto metodu pro odmapování objektu mapování souborů.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CAtlFileMappingBase:: operator =](#operator_eq)|Nastaví aktuální objekt mapování souboru na jiný objekt mapování souborů.|

## <a name="remarks"></a>Poznámky

Mapování souborů je přidružení obsahu souboru k části virtuálního adresního prostoru procesu. Tato třída poskytuje metody pro vytváření objektů mapování souborů, které umožňují programům snadný přístup k datům a jejich sdílení.

Další informace najdete v tématu [mapování souborů](/windows/win32/Memory/file-mapping) v Windows SDK.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlfile. h

##  <a name="catlfilemappingbase"></a>CAtlFileMappingBase::CAtlFileMappingBase

Konstruktor

```
CAtlFileMappingBase(CAtlFileMappingBase& orig);
CAtlFileMappingBase() throw();
```

### <a name="parameters"></a>Parametry

*orig*<br/>
Původní objekt mapování souboru ke zkopírování pro vytvoření nového objektu.

### <a name="remarks"></a>Poznámky

Vytvoří nový objekt mapování souborů, volitelně pomocí existujícího objektu. Pro otevření nebo vytvoření objektu mapování souborů pro konkrétní soubor je stále nutné zavolat [CAtlFileMappingBase:: souboru mapování](#mapfile) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#71](../../atl/codesnippet/cpp/catlfilemappingbase-class_1.cpp)]

##  <a name="dtor"></a>  CAtlFileMappingBase::~CAtlFileMappingBase

Destruktor.

```
~CAtlFileMappingBase() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny prostředky přidělené třídou a zavolá metodu [CAtlFileMappingBase:: demapování](#unmap) .

##  <a name="copyfrom"></a>CAtlFileMappingBase::CopyFrom

Voláním této metody můžete kopírovat z objektu mapování souborů.

```
HRESULT CopyFrom(CAtlFileMappingBase& orig) throw();
```

### <a name="parameters"></a>Parametry

*orig*<br/>
Původní objekt mapování souboru, ze kterého se má kopírovat.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="getdata"></a>CAtlFileMappingBase:: GetData

Voláním této metody získáte data z objektu mapování souborů.

```
void* GetData() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na data.

##  <a name="gethandle"></a>CAtlFileMappingBase:: GetHandle

Voláním této metody vrátí popisovač objektu mapování souborů.

```
HANDLE GetHandle() throw ();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač objektu mapování souboru.

##  <a name="getmappingsize"></a>CAtlFileMappingBase::GetMappingSize

Voláním této metody získáte velikost mapování z objektu mapování souborů.

```
SIZE_T GetMappingSize() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí velikost mapování.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlFileMappingBase:: CAtlFileMappingBase](#catlfilemappingbase).

##  <a name="mapfile"></a>CAtlFileMappingBase:: souboru mapování

Voláním této metody otevřete nebo vytvořte objekt mapování souborů pro zadaný soubor.

```
HRESULT MapFile(
    HANDLE hFile,
    SIZE_T nMappingSize = 0,
    ULONGLONG nOffset = 0,
    DWORD dwMappingProtection = PAGE_READONLY,
    DWORD dwViewDesiredAccess = FILE_MAP_READ) throw();
```

### <a name="parameters"></a>Parametry

*hFile*<br/>
Zpracovat soubor, ze kterého se má vytvořit objekt mapování *hfile* musí být platná a nemůže být nastavená na INVALID_HANDLE_VALUE.

*nMappingSize*<br/>
Velikost mapování Pokud je hodnota 0, je maximální velikost objektu mapování souborů stejná jako aktuální velikost souboru identifikovaného *hfile.*

*nOffset*<br/>
Posun souboru, kde má být mapování zahájeno. Hodnota posunu musí být násobkem členitosti přidělení paměti systému.

*dwMappingProtection*<br/>
Ochrana požadovaná pro zobrazení souboru při mapování souboru. Viz *flProtect* v [CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappingw) ve Windows SDK.

*dwViewDesiredAccess*<br/>
Určuje typ přístupu k zobrazení souboru, a proto ochranu stránek mapovaných souborem. Viz *dwDesiredAccess* v [MapViewOfFileEx –](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) ve Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Po vytvoření objektu mapování souborů nesmí velikost souboru přesáhnout velikost objektu mapování souborů;. Pokud k tomu dojde, ne veškerý obsah souboru bude k dispozici pro sdílení. Další podrobnosti najdete v tématu [CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappingw) a [MapViewOfFileEx –](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) v Windows SDK.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CAtlFileMappingBase:: CAtlFileMappingBase](#catlfilemappingbase).

##  <a name="mapsharedmem"></a>CAtlFileMappingBase::MapSharedMem

Voláním této metody vytvoříte objekt mapování souborů, který umožňuje úplný přístup ke všem procesům.

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
Velikost mapování Pokud je hodnota 0, je maximální velikost objektu mapování souborů stejná jako aktuální velikost objektu mapování souborů identifikovaných pomocí *szName*.

*szName*<br/>
Název objektu mapování

*pbAlreadyExisted*<br/>
Odkazuje na hodnotu BOOL, která je nastavena na hodnotu TRUE, pokud objekt mapování již existoval.

*lpsa*<br/>
Ukazatel na `SECURITY_ATTRIBUTES` strukturu, která určuje, zda vrácený popisovač mohou být děděny podřízenými procesy. Viz *lpAttributes* v [CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappingw) ve Windows SDK.

*dwMappingProtection*<br/>
Ochrana požadovaná pro zobrazení souboru, když je soubor namapován. Viz *flProtect* v `CreateFileMapping` tématu Windows SDK.

*dwViewDesiredAccess*<br/>
Určuje typ přístupu k zobrazení souboru, a proto ochranu stránek mapovaných souborem. Viz *dwDesiredAccess* v [MapViewOfFileEx –](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) ve Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

`MapShareMem`umožňuje sdílet existující objekt mapování souborů vytvořený pomocí [CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappingw), aby bylo možné mezi procesy sdílet.

##  <a name="openmapping"></a>CAtlFileMappingBase::OpenMapping

Voláním této metody otevřete pojmenovaný objekt mapování souborů pro zadaný soubor.

```
HRESULT OpenMapping(
    LPCTSTR szName,
    SIZE_T nMappingSize,
    ULONGLONG nOffset = 0,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```

### <a name="parameters"></a>Parametry

*szName*<br/>
Název objektu mapování Pokud existuje otevřený popisovač objektu mapování souborů s tímto názvem a popisovač zabezpečení u objektu Mapping není v konfliktu s parametrem *dwViewDesiredAccess* , operace otevření bude úspěšná.

*nMappingSize*<br/>
Velikost mapování Pokud je hodnota 0, je maximální velikost objektu mapování souborů stejná jako aktuální velikost objektu mapování souborů identifikovaných pomocí *szName*.

*nOffset*<br/>
Posun souboru, kde má být mapování zahájeno. Hodnota posunu musí být násobkem členitosti přidělení paměti systému.

*dwViewDesiredAccess*<br/>
Určuje typ přístupu k zobrazení souboru, a proto ochranu stránek mapovaných souborem. Viz *dwDesiredAccess* v [MapViewOfFileEx –](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) ve Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

V sestavení ladění dojde k chybě kontrolního výrazu, pokud jsou vstupní parametry neplatné.

##  <a name="operator_eq"></a>CAtlFileMappingBase:: operator =

Nastaví aktuální objekt mapování souboru na jiný objekt mapování souborů.

```
CAtlFileMappingBase& operator=(CAtlFileMappingBase& orig);
```

### <a name="parameters"></a>Parametry

*orig*<br/>
Aktuální objekt mapování souborů.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na aktuální objekt.

##  <a name="unmap"></a>CAtlFileMappingBase:: unmapování

Zavolejte tuto metodu pro odmapování objektu mapování souborů.

```
HRESULT Unmap() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Další podrobnosti najdete v tématu [UnmapViewOfFile](/windows/win32/api/memoryapi/nf-memoryapi-unmapviewoffile) v Windows SDK.

## <a name="see-also"></a>Viz také:

[CAtlFileMapping – třída](../../atl/reference/catlfilemapping-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
