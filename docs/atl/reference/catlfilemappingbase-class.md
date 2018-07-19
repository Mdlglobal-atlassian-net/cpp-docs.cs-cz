---
title: Catlfilemappingbase – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
dev_langs:
- C++
helpviewer_keywords:
- CAtlFileMappingBase class
ms.assetid: be555723-2790-4f57-a8fb-be4d68460775
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cfc59e4652c7c758e7fb5b3ee8a228963a6b6f7d
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37883242"
---
# <a name="catlfilemappingbase-class"></a>Catlfilemappingbase – třída
Tato třída reprezentuje soubor mapovaných do paměti.  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CAtlFileMappingBase
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)|Konstruktor|  
|[Catlfilemappingbase –:: ~ catlfilemappingbase –](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlFileMappingBase::CopyFrom](#copyfrom)|Voláním této metody lze kopírovat z objektu mapování souboru.|  
|[CAtlFileMappingBase::GetData](#getdata)|Volejte tuto metodu za účelem získání dat z objektu mapování souboru.|  
|[CAtlFileMappingBase::GetHandle](#gethandle)|Voláním této metody vrátí popisovač souboru.|  
|[CAtlFileMappingBase::GetMappingSize](#getmappingsize)|Volejte tuto metodu za účelem získání velikost mapování z objektu mapování souboru.|  
|[CAtlFileMappingBase::MapFile](#mapfile)|Voláním této metody lze vytvořit objekt mapování souboru.|  
|[CAtlFileMappingBase::MapSharedMem](#mapsharedmem)|Volejte tuto metodu za účelem vytvoření objektu mapování souboru, který umožňuje plný přístup do všech procesů.|  
|[CAtlFileMappingBase::OpenMapping](#openmapping)|Voláním této metody vrátí popisovač pro objekt mapování souboru.|  
|[CAtlFileMappingBase::Unmap](#unmap)|Volejte tuto metodu za účelem unmap objekt mapování souboru.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlFileMappingBase::operator =](#operator_eq)|Nastaví aktuální objekt mapování souboru na jiný objekt mapování souboru.|  
  
## <a name="remarks"></a>Poznámky  
 Mapování souboru je přidružení obsah souboru s částí virtuálního adresového prostoru procesu. Tato třída poskytuje metody pro vytváření objektů mapování souborů, které umožňují aplikacím snadný přístup k a sdílet data.  
  
 Další informace najdete v tématu [mapování souboru](http://msdn.microsoft.com/library/windows/desktop/aa366556) v sadě Windows SDK.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlfile.h  
  
##  <a name="catlfilemappingbase"></a>  CAtlFileMappingBase::CAtlFileMappingBase  
 Konstruktor  
  
```
CAtlFileMappingBase(CAtlFileMappingBase& orig);  
CAtlFileMappingBase() throw();
```  
  
### <a name="parameters"></a>Parametry  
 *ORIG*  
 Původní objekt mapování souboru ke zkopírování do vytvoření nového objektu.  
  
### <a name="remarks"></a>Poznámky  
 Vytvoří nový objekt mapování souboru, případně můžete použít existující objekt. Je stále potřeba volat [CAtlFileMappingBase::MapFile](#mapfile) otevřít nebo vytvořit objekt mapování souboru pro určitý soubor.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#71](../../atl/codesnippet/cpp/catlfilemappingbase-class_1.cpp)]  
  
##  <a name="dtor"></a>  Catlfilemappingbase –:: ~ catlfilemappingbase –  
 Destruktor.  
  
```
~CAtlFileMappingBase() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny prostředky přidělené třídy a volání [CAtlFileMappingBase::Unmap](#unmap) metody.  
  
##  <a name="copyfrom"></a>  CAtlFileMappingBase::CopyFrom  
 Voláním této metody lze kopírovat z objektu mapování souboru.  
  
```
HRESULT CopyFrom(CAtlFileMappingBase& orig) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *ORIG*  
 Původní objekt mapování souboru bude kopírováno.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="getdata"></a>  CAtlFileMappingBase::GetData  
 Volejte tuto metodu za účelem získání dat z objektu mapování souboru.  
  
```
void* GetData() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na data.  
  
##  <a name="gethandle"></a>  CAtlFileMappingBase::GetHandle  
 Voláním této metody vrátí popisovač pro objekt mapování souboru.  
  
```
HANDLE GetHandle() throw ();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí popisovač pro objekt mapování souboru.  
  
##  <a name="getmappingsize"></a>  CAtlFileMappingBase::GetMappingSize  
 Volejte tuto metodu za účelem získání velikost mapování z objektu mapování souboru.  
  
```
SIZE_T GetMappingSize() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí velikost mapování.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase).  
  
##  <a name="mapfile"></a>  CAtlFileMappingBase::MapFile  
 Volejte tuto metodu za účelem otevřete nebo vytvořte objekt mapování souboru pro určený soubor.  
  
```
HRESULT MapFile(
    HANDLE hFile,
    SIZE_T nMappingSize = 0,
    ULONGLONG nOffset = 0,
    DWORD dwMappingProtection = PAGE_READONLY,
    DWORD dwViewDesiredAccess = FILE_MAP_READ) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *hfile –*  
 Popisovač souboru, ve kterém chcete vytvořit objekt mapování. *hfile –* musí být platný a nejde ji nastavit na INVALID_HANDLE_VALUE.  
  
 *nMappingSize*  
 Velikost mapování. Pokud je 0, je maximální velikost objektu mapování souboru rovná aktuální velikosti souboru identifikovaný *hfile –.*  
  
 *nOffset*  
 Posunu souboru, kde má začít mapování. Hodnota posunutí musí být násobkem členitosti přidělení paměti v systému.  
  
 *dwMappingProtection*  
 Ochrana požadovanou pro zobrazení souborů při mapování souboru. Zobrazit *flProtect* v [CreateFileMapping](http://msdn.microsoft.com/library/windows/desktop/aa366537) v sadě Windows SDK.  
  
 *dwViewDesiredAccess*  
 Určuje typ přístupu k zobrazení souborů a proto ochrany na stránkách namapovány v souboru. Zobrazit *dwDesiredAccess* v [mapviewoffileex –](http://msdn.microsoft.com/library/windows/desktop/aa366763) v sadě Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Po vytvoření objektu mapování souboru, velikost souboru nesmí překročit velikost objekt mapování souboru. Pokud ano, ne veškerý obsah souboru nebudou k dispozici pro sdílení. Další podrobnosti najdete v tématu [CreateFileMapping](http://msdn.microsoft.com/library/windows/desktop/aa366537) a [mapviewoffileex –](http://msdn.microsoft.com/library/windows/desktop/aa366763) v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase).  
  
##  <a name="mapsharedmem"></a>  CAtlFileMappingBase::MapSharedMem  
 Volejte tuto metodu za účelem vytvoření objektu mapování souboru, který umožňuje plný přístup do všech procesů.  
  
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
 *nMappingSize*  
 Velikost mapování. Pokud je 0, je maximální velikost objektu mapování souboru rovná aktuální velikosti objekt mapování souboru identifikovaný *szName*.  
  
 *szName*  
 Název objektu mapování.  
  
 *pbAlreadyExisted*  
 Odkazuje na hodnotu BOOL, která je nastavena na hodnotu TRUE, pokud objekt mapování již existuje.  
  
 *lpsa*  
 Ukazatel `SECURITY_ATTRIBUTES` struktura, která určuje, zda lze Vrácený popisovač Zdědit podřízenými procesy. Zobrazit *lpAttributes* v [CreateFileMapping](http://msdn.microsoft.com/library/windows/desktop/aa366537) v sadě Windows SDK.  
  
 *dwMappingProtection*  
 Ochrana požadovaného pro zobrazení souborů, když je namapován soubor. Zobrazit *flProtect* v `CreateFileMapping` v sadě Windows SDK.  
  
 *dwViewDesiredAccess*  
 Určuje typ přístupu k zobrazení souborů a proto ochrany na stránkách namapovány v souboru. Zobrazit *dwDesiredAccess* v [mapviewoffileex –](http://msdn.microsoft.com/library/windows/desktop/aa366763) v sadě Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 `MapShareMem` Umožňuje existující objekt mapování souboru, vytvořil [CreateFileMapping](http://msdn.microsoft.com/library/windows/desktop/aa366537), chcete-li být sdílen mezi procesy.  
  
##  <a name="openmapping"></a>  CAtlFileMappingBase::OpenMapping  
 Volejte tuto metodu za účelem otevření pojmenovaný objekt mapování souboru pro určený soubor.  
  
```
HRESULT OpenMapping(
    LPCTSTR szName,
    SIZE_T nMappingSize,
    ULONGLONG nOffset = 0,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *szName*  
 Název objektu mapování. Pokud není otevřený popisovač pro objekt mapování souboru s tímto názvem a popisovač zabezpečení pro objekt mapování není v konfliktu s *dwViewDesiredAccess* parametru, otevřených operace úspěšná.  
  
 *nMappingSize*  
 Velikost mapování. Pokud je 0, je maximální velikost objektu mapování souboru rovná aktuální velikosti objekt mapování souboru identifikovaný *szName*.  
  
 *nOffset*  
 Posunu souboru, kde má začít mapování. Hodnota posunutí musí být násobkem členitosti přidělení paměti v systému.  
  
 *dwViewDesiredAccess*  
 Určuje typ přístupu k zobrazení souborů a proto ochrany na stránkách namapovány v souboru. Zobrazit *dwDesiredAccess* v [mapviewoffileex –](http://msdn.microsoft.com/library/windows/desktop/aa366763) v sadě Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 V sestavení ladění dojde k chybě kontrolního výrazu, pokud vstupní parametry jsou neplatné.  
  
##  <a name="operator_eq"></a>  CAtlFileMappingBase::operator =  
 Nastaví aktuální objekt mapování souboru na jiný objekt mapování souboru.  
  
```
CAtlFileMappingBase& operator=(CAtlFileMappingBase& orig);
```  
  
### <a name="parameters"></a>Parametry  
 *ORIG*  
 Aktuální objekt mapování souboru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odkaz na aktuální objekt.  
  
##  <a name="unmap"></a>  CAtlFileMappingBase::Unmap  
 Volejte tuto metodu za účelem unmap objekt mapování souboru.  
  
```
HRESULT Unmap() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [UnmapViewOfFile](http://msdn.microsoft.com/library/windows/desktop/aa366882) v sadě Windows SDK pro další podrobnosti.  
  
## <a name="see-also"></a>Viz také  
 [Catlfilemapping – třída](../../atl/reference/catlfilemapping-class.md)   
 [Přehled tříd](../../atl/atl-class-overview.md)
