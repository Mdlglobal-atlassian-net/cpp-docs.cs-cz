---
title: "Třída CAtlFileMappingBase | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
helpviewer_keywords: CAtlFileMappingBase class
ms.assetid: be555723-2790-4f57-a8fb-be4d68460775
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4b5e0dd90894e052d4b9bcff08e7e12234dde8f4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="catlfilemappingbase-class"></a>CAtlFileMappingBase – třída
Tato třída reprezentuje soubor mapované paměti.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CAtlFileMappingBase
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)|Konstruktor|  
|[CAtlFileMappingBase:: ~ CAtlFileMappingBase](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlFileMappingBase::CopyFrom](#copyfrom)|Voláním této metody lze kopírovat z objekt mapování souboru.|  
|[CAtlFileMappingBase::GetData](#getdata)|Volejte tuto metodu za účelem načtení dat z objektu mapování souboru.|  
|[CAtlFileMappingBase::GetHandle](#gethandle)|Volejte tuto metodu vrátit popisovač souboru.|  
|[CAtlFileMappingBase::GetMappingSize](#getmappingsize)|Volejte tuto metodu za účelem načtení velikost mapování z objektu mapování souboru.|  
|[CAtlFileMappingBase::MapFile](#mapfile)|Voláním této metody lze vytvořit objekt mapování souboru.|  
|[CAtlFileMappingBase::MapSharedMem](#mapsharedmem)|Voláním této metody lze vytvořit objekt mapování souboru, která umožňuje úplný přístup do všech procesů.|  
|[CAtlFileMappingBase::OpenMapping](#openmapping)|Volejte tuto metodu za účelem vrací popisovač objektu mapování souboru.|  
|[CAtlFileMappingBase::Unmap](#unmap)|Volejte tuto metodu za účelem zrušit mapování objekt mapování souboru.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlFileMappingBase::operator =](#operator_eq)|Nastaví aktuální objekt mapování souboru k jinému objektu mapování souboru.|  
  
## <a name="remarks"></a>Poznámky  
 Mapování souboru je obsah souboru přidružení část virtuální adresní prostor procesu. Tato třída poskytuje metody pro vytváření objektů mapování souboru, které umožňují programy snadný přístup a sdílet data.  
  
 Další informace najdete v tématu [mapování souboru](http://msdn.microsoft.com/library/windows/desktop/aa366556) ve Windows SDK.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlfile.h  
  
##  <a name="catlfilemappingbase"></a>CAtlFileMappingBase::CAtlFileMappingBase  
 Konstruktor  
  
```
CAtlFileMappingBase(CAtlFileMappingBase& orig);  
CAtlFileMappingBase() throw();
```  
  
### <a name="parameters"></a>Parametry  
 `orig`  
 Původní objekt mapování souboru zkopírujte do vytvořte nový objekt.  
  
### <a name="remarks"></a>Poznámky  
 Vytvoří nový objekt mapování souboru, volitelně pomocí existujícího objektu. Je stále nutné volat [CAtlFileMappingBase::MapFile](#mapfile) otevřít nebo vytvořit objekt mapování souboru pro určitého souboru.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#71](../../atl/codesnippet/cpp/catlfilemappingbase-class_1.cpp)]  
  
##  <a name="dtor"></a>CAtlFileMappingBase:: ~ CAtlFileMappingBase  
 Destruktor.  
  
```
~CAtlFileMappingBase() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny prostředky přidělené třídy a volání [CAtlFileMappingBase::Unmap](#unmap) metoda.  
  
##  <a name="copyfrom"></a>CAtlFileMappingBase::CopyFrom  
 Voláním této metody lze kopírovat z objekt mapování souboru.  
  
```
HRESULT CopyFrom(CAtlFileMappingBase& orig) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `orig`  
 Původní objekt mapování souboru pro kopírování z.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` na úspěch nebo Chyba `HRESULT` při selhání.  
  
##  <a name="getdata"></a>CAtlFileMappingBase::GetData  
 Volejte tuto metodu za účelem načtení dat z objektu mapování souboru.  
  
```
void* GetData() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na data.  
  
##  <a name="gethandle"></a>CAtlFileMappingBase::GetHandle  
 Volejte tuto metodu za účelem vrací popisovač objektu mapování souboru.  
  
```
HANDLE GetHandle() throw ();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí popisovač objekt mapování souboru.  
  
##  <a name="getmappingsize"></a>CAtlFileMappingBase::GetMappingSize  
 Volejte tuto metodu za účelem načtení velikost mapování z objektu mapování souboru.  
  
```
SIZE_T GetMappingSize() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí velikost mapování.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase).  
  
##  <a name="mapfile"></a>CAtlFileMappingBase::MapFile  
 Voláním této metody lze otevřít nebo vytvořit objekt mapování souboru pro zadaný soubor.  
  
```
HRESULT MapFile(
    HANDLE hFile,
    SIZE_T nMappingSize = 0,
    ULONGLONG nOffset = 0,
    DWORD dwMappingProtection = PAGE_READONLY,
    DWORD dwViewDesiredAccess = FILE_MAP_READ) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `hFile`  
 Popisovač souboru, ve kterém vytvoříte objekt mapování. `hFile`musí být platný a nelze ji nastavit na INVALID_HANDLE_VALUE.  
  
 `nMappingSize`  
 Velikost mapování. Pokud je 0, maximální velikost objektu mapování souboru je rovna aktuální velikosti souboru se identifikovanou pomocí *hfile –.*  
  
 `nOffset`  
 Posun souboru, kde je mapování začít. Hodnota posunutí musí být násobkem členitosti přidělení paměti systému.  
  
 `dwMappingProtection`  
 Ochrana požadovaných pro zobrazení souborů, když je mapovaný soubor. V tématu `flProtect` v [CreateFileMapping](http://msdn.microsoft.com/library/windows/desktop/aa366537) ve Windows SDK.  
  
 `dwViewDesiredAccess`  
 Určuje typ přístupu k zobrazení souboru a tedy ochranu stránek mapovat pomocí souboru. V tématu `dwDesiredAccess` v [MapViewOfFileEx](http://msdn.microsoft.com/library/windows/desktop/aa366763) ve Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` na úspěch nebo Chyba `HRESULT` při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Po vytvoření objektu mapování souboru, velikost souboru nesmí překročit velikost objektu mapování souboru; Pokud ano, ne všechny jeho obsah bude k dispozici pro sdílení. Další podrobnosti najdete v tématu [CreateFileMapping](http://msdn.microsoft.com/library/windows/desktop/aa366537) a [MapViewOfFileEx](http://msdn.microsoft.com/library/windows/desktop/aa366763) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase).  
  
##  <a name="mapsharedmem"></a>CAtlFileMappingBase::MapSharedMem  
 Voláním této metody lze vytvořit objekt mapování souboru, která umožňuje úplný přístup do všech procesů.  
  
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
 `nMappingSize`  
 Velikost mapování. Pokud je 0, maximální velikost objektu mapování souboru je rovna aktuální velikosti objektu mapování souboru identifikovaný`szName.`  
  
 `szName`  
 Název objektu mapování.  
  
 *pbAlreadyExisted*  
 Odkazuje na BOOL hodnotu, která je nastavena na hodnotu TRUE, pokud objekt mapování už existuje.  
  
 `lpsa`  
 Ukazatel na **SECURITY_ATTRIBUTES** struktura, která určuje, zda může být vrácená popisovač zděděn podřízené procesy. V tématu *lpAttributes* v [CreateFileMapping](http://msdn.microsoft.com/library/windows/desktop/aa366537) ve Windows SDK.  
  
 `dwMappingProtection`  
 Ochrana požadovaných pro zobrazení souborů, když je mapovaný soubor. V tématu `flProtect` v **CreateFileMapping** ve Windows SDK.  
  
 `dwViewDesiredAccess`  
 Určuje typ přístupu k zobrazení souboru a tedy ochranu stránek mapovat pomocí souboru. V tématu `dwDesiredAccess` v [MapViewOfFileEx](http://msdn.microsoft.com/library/windows/desktop/aa366763) ve Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` na úspěch nebo Chyba `HRESULT` při selhání.  
  
### <a name="remarks"></a>Poznámky  
 **MapShareMem** umožňuje existující objekt mapování souboru, vytvořené [CreateFileMapping](http://msdn.microsoft.com/library/windows/desktop/aa366537)můžete sdílet mezi procesy.  
  
##  <a name="openmapping"></a>CAtlFileMappingBase::OpenMapping  
 Voláním této metody lze otevřít objekt mapování souboru s názvem pro zadaný soubor.  
  
```
HRESULT OpenMapping(
    LPCTSTR szName,
    SIZE_T nMappingSize,
    ULONGLONG nOffset = 0,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `szName`  
 Název objektu mapování. Je-li otevřít popisovač pro objekt mapování souboru s tímto názvem a popisovač zabezpečení pro objekt mapování není v konfliktu s `dwViewDesiredAccess` parametr, otevřete operace úspěšná.  
  
 `nMappingSize`  
 Velikost mapování. Pokud je 0, maximální velikost objektu mapování souboru je rovna aktuální velikosti objektu mapování souboru identifikovaný`szName.`  
  
 `nOffset`  
 Posun souboru, kde je mapování začít. Hodnota posunutí musí být násobkem členitosti přidělení paměti systému.  
  
 `dwViewDesiredAccess`  
 Určuje typ přístupu k zobrazení souboru a tedy ochranu stránek mapovat pomocí souboru. V tématu `dwDesiredAccess` v [MapViewOfFileEx](http://msdn.microsoft.com/library/windows/desktop/aa366763) ve Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` na úspěch nebo Chyba `HRESULT` při selhání.  
  
### <a name="remarks"></a>Poznámky  
 V sestavení pro ladění dojde k chybě assertion, pokud vstupní parametry jsou neplatné.  
  
##  <a name="operator_eq"></a>CAtlFileMappingBase::operator =  
 Nastaví aktuální objekt mapování souboru k jinému objektu mapování souboru.  
  
```
CAtlFileMappingBase& operator=(CAtlFileMappingBase& orig);
```  
  
### <a name="parameters"></a>Parametry  
 `orig`  
 Aktuální objekt mapování souboru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odkaz na aktuální objekt.  
  
##  <a name="unmap"></a>CAtlFileMappingBase::Unmap  
 Volejte tuto metodu za účelem zrušit mapování objekt mapování souboru.  
  
```
HRESULT Unmap() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` na úspěch nebo Chyba `HRESULT` při selhání.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [UnmapViewOfFile](http://msdn.microsoft.com/library/windows/desktop/aa366882) ve Windows SDK pro další podrobnosti.  
  
## <a name="see-also"></a>Viz také  
 [CAtlFileMapping – třída](../../atl/reference/catlfilemapping-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
