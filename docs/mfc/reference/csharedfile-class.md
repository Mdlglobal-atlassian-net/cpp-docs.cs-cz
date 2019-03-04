---
title: Csharedfile – třída
ms.date: 11/04/2016
f1_keywords:
- CSharedFile
- AFXADV/CSharedFile
- AFXADV/CSharedFile::CSharedFile
- AFXADV/CSharedFile::Detach
- AFXADV/CSharedFile::SetHandle
helpviewer_keywords:
- CSharedFile [MFC], CSharedFile
- CSharedFile [MFC], Detach
- CSharedFile [MFC], SetHandle
ms.assetid: 5d000422-9ede-4318-a8c9-f7412b674f39
ms.openlocfilehash: e86e64c1de232aba0c17a0fdfb3600e480567a57
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273072"
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

Soubory sdílené paměti liší od jiné soubory z paměti, že je paměť přidělená k [GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc) funkce Windows. `CSharedFile` Třídy ukládá data v bloku globálně přidělená paměť (vytvořené pomocí `GlobalAlloc`), a tento blok paměti je možné sdílet pomocí DDE, schránku nebo jiných OLE/COM jednotné operace přenosu dat, například pomocí `IDataObject`.

`GlobalAlloc` Vrátí HGLOBAL zpracování místo ukazatel na paměti, jako je například ukazatele vrácené [malloc](../../c-runtime-library/reference/malloc.md). Popisovač HGLOBAL je potřeba v určitých aplikacích. Například dávat data do schránky, budete potřebovat popisovač HGLOBAL.

Pamatujte, že `CSharedFile` nemá použití mapované paměti souborů a dat nelze sdílet přímo mezi procesy.

`CSharedFile` objekty mohou automaticky přidělit paměť, vlastní nebo můžete připojit vlastní bloku paměti `CSharedFile` objektu voláním [CSharedFile::SetHandle](#sethandle). V obou případech je přidělena paměť pro soubor paměti automaticky rostoucí `nGrowBytes`-zvýší velikost, pokud `nGrowBytes` není nula.

Další informace najdete v článku [soubory v prostředí MFC](../../mfc/files-in-mfc.md) a [zpracování souborů](../../c-runtime-library/file-handling.md) v *Run-Time Library Reference*.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CMemFile](../../mfc/reference/cmemfile-class.md)

`CSharedFile`

## <a name="requirements"></a>Požadavky

**Header:** afxadv.h

##  <a name="csharedfile"></a>  CSharedFile::CSharedFile

Vytvoří `CSharedFile` objektu a přiděluje paměť pro něj.

```
CSharedFile(
    UINT nAllocFlags = GMEM_DDESHARE | GMEM_MOVEABLE,
    UINT nGrowBytes = 4096);
```

### <a name="parameters"></a>Parametry

*nAllocFlags*<br/>
Příznaky určující, jak má přidělit paměť. Zobrazit [GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc) seznam platných hodnot příznaku.

*nGrowBytes*<br/>
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

*hGlobalMemory*<br/>
Zpracování do globální paměti, připojí se k `CSharedFile`.

*bAllowGrow*<br/>
Určuje, zda blok paměti může růst.

### <a name="remarks"></a>Poznámky

Pokud *bAllowGrow* nenulovou velikost bloku paměti mění podle potřeby, například pokud se pokus o provedené zapsat počet bajtů k souboru, než byly přiděleny bloku paměti.

## <a name="see-also"></a>Viz také:

[CMemFile – třída](../../mfc/reference/cmemfile-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CMemFile – třída](../../mfc/reference/cmemfile-class.md)
