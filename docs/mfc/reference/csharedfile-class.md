---
title: Csharedfile – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSharedFile
- AFXADV/CSharedFile
- AFXADV/CSharedFile::CSharedFile
- AFXADV/CSharedFile::Detach
- AFXADV/CSharedFile::SetHandle
dev_langs:
- C++
helpviewer_keywords:
- CSharedFile [MFC], CSharedFile
- CSharedFile [MFC], Detach
- CSharedFile [MFC], SetHandle
ms.assetid: 5d000422-9ede-4318-a8c9-f7412b674f39
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3d570204a997def3b295e7ba0fb3b08b9a15677b
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37853725"
---
# <a name="csharedfile-class"></a>Csharedfile – třída
[Cmemfile –](../../mfc/reference/cmemfile-class.md)-odvozenou třídu, která podporuje sdílené soubory z paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CSharedFile : public CMemFile  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CSharedFile::CSharedFile](#csharedfile)|Vytvoří `CSharedFile` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CSharedFile::Detach](#detach)|Zavře sdílené paměti soubor a vrátí popisovač bloku paměti.|  
|[CSharedFile::SetHandle](#sethandle)|Připojí soubor sdílené paměti na blok paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Soubory z paměti se chovat jako soubory disku s tím rozdílem, že je soubor uložený v paměti RAM, nikoli na disku. Soubor paměti je užitečné pro rychlé dočasné úložiště nebo při přenosech nezpracovaná bajtů nebo serializovat objekty mezi nezávislé procesy.  
  
 Soubory sdílené paměti liší od jiné soubory z paměti, že je paměť přidělená k [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) funkce Windows. `CSharedFile` Třídy ukládá data v bloku globálně přidělená paměť (vytvořené pomocí `GlobalAlloc`), a tento blok paměti je možné sdílet pomocí DDE, schránku nebo jiných OLE/COM jednotné operace přenosu dat, například pomocí `IDataObject`.  
  
 `GlobalAlloc` Vrátí HGLOBAL zpracování místo ukazatel na paměti, jako je například ukazatele vrácené [malloc](../../c-runtime-library/reference/malloc.md). Popisovač HGLOBAL je potřeba v určitých aplikacích. Například dávat data do schránky, budete potřebovat popisovač HGLOBAL.  
  
 Pamatujte, že `CSharedFile` nemá použití mapované paměti souborů a dat nelze sdílet přímo mezi procesy.  
  
 `CSharedFile` objekty mohou automaticky přidělit paměť, vlastní nebo můžete připojit vlastní bloku paměti `CSharedFile` objektu voláním [CSharedFile::SetHandle](#sethandle). V obou případech je přidělena paměť pro soubor paměti automaticky rostoucí `nGrowBytes`-zvýší velikost, pokud `nGrowBytes` není nula.  
  
 Další informace najdete v článku [soubory v prostředí MFC](../../mfc/files-in-mfc.md) a [zpracování souborů](../../c-runtime-library/file-handling.md) v *Run-Time Library Reference*.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [Cfile –](../../mfc/reference/cfile-class.md)  
  
 [Cmemfile –](../../mfc/reference/cmemfile-class.md)  
  
 `CSharedFile`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxadv.h  
  
##  <a name="csharedfile"></a>  CSharedFile::CSharedFile  
 Vytvoří `CSharedFile` objektu a přiděluje paměť pro něj.  
  
```  
CSharedFile(
    UINT nAllocFlags = GMEM_DDESHARE | GMEM_MOVEABLE,  
    UINT nGrowBytes = 4096);
```  
  
### <a name="parameters"></a>Parametry  
 *nAllocFlags*  
 Příznaky určující, jak má přidělit paměť. Zobrazit [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) seznam platných hodnot příznaku.  
  
 *nGrowBytes*  
 Zvýšení přidělení paměti v bajtech.  
  
##  <a name="detach"></a>  CSharedFile::Detach  
 Voláním této funkce a zavřete soubor paměti odpojit od bloku paměti.  
  
```  
HGLOBAL Detach();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Obslužná rutina bloku paměti, který obsahuje obsah souboru paměti.  
  
### <a name="remarks"></a>Poznámky  
 Můžete znovu otevřít ho voláním [SetHandle](#sethandle), pomocí popisovač vrácený **odpojit**.  
  
##  <a name="sethandle"></a>  CSharedFile::SetHandle  
 Voláním této funkce připojit blok globální paměti, aby `CSharedFile` objektu.  
  
```  
void SetHandle(
    HGLOBAL hGlobalMemory,  
    BOOL bAllowGrow = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *hGlobalMemory*  
 Zpracování do globální paměti, připojí se k `CSharedFile`.  
  
 *bAllowGrow*  
 Určuje, zda blok paměti může růst.  
  
### <a name="remarks"></a>Poznámky  
 Pokud *bAllowGrow* nenulovou velikost bloku paměti mění podle potřeby, například pokud se pokus o provedené zapsat počet bajtů k souboru, než byly přiděleny bloku paměti.  
  
## <a name="see-also"></a>Viz také  
 [Cmemfile – třída](../../mfc/reference/cmemfile-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CMemFile – třída](../../mfc/reference/cmemfile-class.md)
