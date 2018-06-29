---
title: Třída CSharedFile | Microsoft Docs
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
ms.openlocfilehash: df3c052f3cefb3aa7d2a55e81fd5f7813632ceb1
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2018
ms.locfileid: "37078280"
---
# <a name="csharedfile-class"></a>CSharedFile – třída
[CMemFile](../../mfc/reference/cmemfile-class.md)-odvozené třídy, který podporuje sdílené paměti soubory.  
  
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
|[CSharedFile::Detach](#detach)|Zavře sdílené paměti soubor a vrátí popisovač jeho bloku paměti.|  
|[CSharedFile::SetHandle](#sethandle)|Připojí sdílené paměti soubor na blok paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Soubory paměti chovat jako soubory disku s tím rozdílem, že je soubor uložený v paměti RAM místo na disku. Soubor paměti je užitečná pro rychlé dočasné úložiště nebo přenos nezpracovaná bajtů nebo serializovat objekty mezi nezávislé procesy.  
  
 Soubory sdílené paměti se liší z jiných souborů paměti, že se přidělí paměť pro ně s [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) funkce systému Windows. `CSharedFile` Třída ukládá data v bloku globálně přidělenou paměť (vytvořený `GlobalAlloc`), a tento blok paměti je možné sdílet pomocí DDE, schránku nebo jiných OLE/COM uniform operace přenosu dat, například pomocí `IDataObject`.  
  
 `GlobalAlloc` Vrátí `HGLOBAL` zpracování nikoli ukazatel na paměti, jako je například ukazatel vrácený [malloc –](../../c-runtime-library/reference/malloc.md). `HGLOBAL` Popisovač je potřeba v některých aplikací. Například dávat data do schránky. je třeba `HGLOBAL` zpracování.  
  
 Pamatujte, že `CSharedFile` nepodporuje používané mapované paměti soubory a data nelze sdílet přímo mezi procesy.  
  
 `CSharedFile` objekty lze automaticky přidělit vlastní paměti nebo můžete připojit vlastní blok paměti k `CSharedFile` objekt voláním [CSharedFile::SetHandle](#sethandle). V obou případech se přidělí paměť pro rostoucí soubor paměti automaticky v `nGrowBytes`– velikost se zvýší, pokud `nGrowBytes` není nula.  
  
 Další informace najdete v článku [soubory v prostředí MFC](../../mfc/files-in-mfc.md) a [zpracování souborů](../../c-runtime-library/file-handling.md) v *referenční dokumentace běhové knihovny*.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cfile –](../../mfc/reference/cfile-class.md)  
  
 [CMemFile](../../mfc/reference/cmemfile-class.md)  
  
 `CSharedFile`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxadv.h  
  
##  <a name="csharedfile"></a>  CSharedFile::CSharedFile  
 Vytvoří `CSharedFile` objektu a přidělí paměť.  
  
```  
CSharedFile(
    UINT nAllocFlags = GMEM_DDESHARE | GMEM_MOVEABLE,  
    UINT nGrowBytes = 4096);
```  
  
### <a name="parameters"></a>Parametry  
 *nAllocFlags*  
 Příznaky, která určuje, jak se přidělit paměť. V tématu [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) seznam platných hodnot příznaku.  
  
 *nGrowBytes*  
 Přírůstek přidělení paměti v bajtech.  
  
##  <a name="detach"></a>  CSharedFile::Detach  
 Volání této funkce a zavřete soubor paměti jej odpojte od bloku paměti.  
  
```  
HGLOBAL Detach();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač bloku paměti, který obsahuje obsah souboru paměti.  
  
### <a name="remarks"></a>Poznámky  
 Můžete ho znovu otevřít voláním [SetHandle](#sethandle), pomocí popisovač vrácený **odpojení**.  
  
##  <a name="sethandle"></a>  CSharedFile::SetHandle  
 Volání této funkce připojit blok globální paměti, která se `CSharedFile` objektu.  
  
```  
void SetHandle(
    HGLOBAL hGlobalMemory,  
    BOOL bAllowGrow = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *hGlobalMemory*  
 Popisovač globální paměť pro připojení k `CSharedFile`.  
  
 *bAllowGrow*  
 Určuje, zda blok paměti může zvětšovat.  
  
### <a name="remarks"></a>Poznámky  
 Pokud *bAllowGrow* přišla nenulové hodnoty, velikost bloku paměti je vyšší, podle potřeby, například pokud se pokus o žádost o další bajty k zápisu do souboru, než se přidělilo bloku paměti.  
  
## <a name="see-also"></a>Viz také  
 [CMemFile – třída](../../mfc/reference/cmemfile-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CMemFile – třída](../../mfc/reference/cmemfile-class.md)
