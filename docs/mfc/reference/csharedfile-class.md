---
title: CSharedFile – třída
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
ms.openlocfilehash: 74a34ec169868d3e28f78f33da38dbda21ef23b3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502602"
---
# <a name="csharedfile-class"></a>CSharedFile – třída

Třída odvozená [CMemFile](../../mfc/reference/cmemfile-class.md), která podporuje sdílené paměťové soubory.

## <a name="syntax"></a>Syntaxe

```
class CSharedFile : public CMemFile
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CSharedFile::CSharedFile](#csharedfile)|`CSharedFile` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CSharedFile::Detach](#detach)|Zavře sdílený soubor paměti a vrátí popisovač jeho bloku paměti.|
|[CSharedFile::SetHandle](#sethandle)|Připojí soubor sdílené paměti k bloku paměti.|

## <a name="remarks"></a>Poznámky

Soubory paměti se chovají podobně jako soubory na disku. Rozdílem je, že soubor paměti je uložený v paměti RAM místo na disku. Soubor paměti je vhodný pro rychlé dočasné úložiště nebo pro přenos nezpracovaných bajtů nebo serializovaných objektů mezi nezávislými procesy.

Sdílené paměťové soubory se liší od ostatních paměťových souborů, které jsou pro ně pro ně přiděleny pomocí funkce [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) systému Windows. Třída ukládá data do globálně přiděleného bloku paměti (vytvořeného pomocí `GlobalAlloc`) a tento blok paměti lze sdílet pomocí DDE, schránky nebo jiných operací OLE/com Uniform data transferu, například pomocí `IDataObject`. `CSharedFile`

`GlobalAlloc`Vrátí popisovač HGLOBAL spíše než ukazatel na paměť, jako je například ukazatel, který vrátil. [](../../c-runtime-library/reference/malloc.md) V některých aplikacích je potřeba popisovač HGLOBAL. Například pro vložení dat do schránky potřebujete popisovač HGLOBAL.

`CSharedFile`nepoužívá soubory mapované paměti a data nelze mezi procesy sdílet přímo.

`CSharedFile`objekty mohou automaticky přidělit vlastní paměť. Nebo můžete k `CSharedFile` objektu připojit vlastní blok paměti voláním [CSharedFile:: SetHandle](#sethandle). V obou případech je paměť pro rozmístění souboru paměti automaticky přidělena `nGrowBytes`v přírůstcích po velikosti, `nGrowBytes` Pokud není nula.

Další informace naleznete v článku [soubory v knihovně MFC](../../mfc/files-in-mfc.md) a [zpracování souborů](../../c-runtime-library/file-handling.md) v *Referenční příručce ke knihovně run-time*.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CFile –](../../mfc/reference/cfile-class.md)

[CMemFile](../../mfc/reference/cmemfile-class.md)

`CSharedFile`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxadv. h

##  <a name="csharedfile"></a>CSharedFile::CSharedFile

`CSharedFile` Vytvoří objekt a přidělí paměti pro něj.

```
CSharedFile(
    UINT nAllocFlags = GMEM_DDESHARE | GMEM_MOVEABLE,
    UINT nGrowBytes = 4096);
```

### <a name="parameters"></a>Parametry

*nAllocFlags*<br/>
Příznaky označující, jak má být paměť přidělena. Seznam platných hodnot příznaků najdete v tématu [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) .

*nGrowBytes*<br/>
Přírůstek přidělení paměti v bajtech.

##  <a name="detach"></a>CSharedFile::D etach

Voláním této funkce zavřete soubor paměti a odpojte ho od bloku paměti.

```
HGLOBAL Detach();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač bloku paměti, který obsahuje obsah souboru paměti.

### <a name="remarks"></a>Poznámky

Můžete jej znovu otevřít voláním [SetHandle](#sethandle)pomocí popisovače vráceného funkcí **detach**.

##  <a name="sethandle"></a>CSharedFile::SetHandle

Voláním této funkce připojíte blok globální paměti k `CSharedFile` objektu.

```
void SetHandle(
    HGLOBAL hGlobalMemory,
    BOOL bAllowGrow = TRUE);
```

### <a name="parameters"></a>Parametry

*hGlobalMemory*<br/>
Popisovač globální paměti, která má být připojena k `CSharedFile`.

*bAllowGrow*<br/>
Určuje, zda je povolený blok paměti pro růst.

### <a name="remarks"></a>Poznámky

Pokud je *bAllowGrow* nenulové, velikost bloku paměti se v případě potřeby zvyšuje, například pokud se pokusíte zapsat více bajtů souboru, než je velikost bloku paměti.

## <a name="see-also"></a>Viz také:

[CMemFile – třída](../../mfc/reference/cmemfile-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CMemFile – třída](../../mfc/reference/cmemfile-class.md)
