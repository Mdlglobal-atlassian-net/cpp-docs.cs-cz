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
ms.openlocfilehash: e6a713ac9d9e906ec204d4a52b43ed51c08fd99c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318420"
---
# <a name="csharedfile-class"></a>CSharedFile – třída

[Třída odvozená cmemfile,](../../mfc/reference/cmemfile-class.md)která podporuje soubory sdílené paměti.

## <a name="syntax"></a>Syntaxe

```
class CSharedFile : public CMemFile
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CSharedFile::CSharedFile](#csharedfile)|Vytvoří `CSharedFile` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CSharedFile::Detach](#detach)|Zavře soubor sdílené paměti a vrátí popisovač jeho bloku paměti.|
|[CSharedFile::SetHandle](#sethandle)|Připojí soubor sdílené paměti k bloku paměti.|

## <a name="remarks"></a>Poznámky

Paměťové soubory se chovají jako diskové soubory. Rozdíl je v tom, že paměťový soubor je uložen v paměti RAM, nikoli na disku. Soubor paměti je užitečný pro rychlé dočasné úložiště nebo pro přenos nezpracovaných bajtů nebo serializovaných objektů mezi nezávislými procesy.

Sdílené paměťové soubory se liší od ostatních paměťových souborů v paměti pro ně je přidělena s [funkcí GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) Windows. Třída `CSharedFile` ukládá data v globálně přiděleném bloku `GlobalAlloc`paměti (vytvořeném pomocí ) a tento blok paměti lze sdílet pomocí DDE, schránky `IDataObject`nebo jiných operací přenosu dat OLE/COM, například pomocí .

`GlobalAlloc`vrátí hglobal popisovač spíše než ukazatel na paměť, jako je například ukazatel vrácený [malloc](../../c-runtime-library/reference/malloc.md). Popisovač HGLOBAL je potřeba v některých aplikacích. Chcete-li například umístit data do schránky, potřebujete popisovač HGLOBAL.

`CSharedFile`nepoužívá soubory mapované v paměti a data nelze přímo sdílet mezi procesy.

`CSharedFile`objekty mohou automaticky přidělit svou vlastní paměť. Nebo můžete k objektu `CSharedFile` připojit vlastní blok paměti voláním [CSharedFile::SetHandle](#sethandle). V obou případech paměti pro růst souboru `nGrowBytes`paměti automaticky přidělena v `nGrowBytes` krocích po velikosti, pokud není nula.

Další informace naleznete v článku [Soubory v knihovně MFC](../../mfc/files-in-mfc.md) a [Zpracování souborů](../../c-runtime-library/file-handling.md) v *odkazu knihovny run-time*.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Soubor C](../../mfc/reference/cfile-class.md)

[Soubor CMem](../../mfc/reference/cmemfile-class.md)

`CSharedFile`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxadv.h

## <a name="csharedfilecsharedfile"></a><a name="csharedfile"></a>CSharedFile::CSharedFile

Vytvoří `CSharedFile` objekt a přidělí pro něj paměť.

```
CSharedFile(
    UINT nAllocFlags = GMEM_DDESHARE | GMEM_MOVEABLE,
    UINT nGrowBytes = 4096);
```

### <a name="parameters"></a>Parametry

*nAllocFlags*<br/>
Příznaky označující, jak má být paměť přidělena. Seznam platných hodnot příznaku naleznete v tématu [GlobalAlloc.](/windows/win32/api/winbase/nf-winbase-globalalloc)

*nGrowBytes*<br/>
Přírůstek přidělení paměti v bajtů.

## <a name="csharedfiledetach"></a><a name="detach"></a>CSharedFile::Detach

Voláním této funkce zavřete paměťový soubor a odpojte jej od bloku paměti.

```
HGLOBAL Detach();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač bloku paměti, který obsahuje obsah souboru paměti.

### <a name="remarks"></a>Poznámky

Můžete znovu otevřít voláním [SetHandle](#sethandle), pomocí popisovače vrácené **odpojit**.

## <a name="csharedfilesethandle"></a><a name="sethandle"></a>CSharedFile::SetHandle

Volání této funkce připojit blok globální `CSharedFile` paměti k objektu.

```
void SetHandle(
    HGLOBAL hGlobalMemory,
    BOOL bAllowGrow = TRUE);
```

### <a name="parameters"></a>Parametry

*hGlobální paměť*<br/>
Zpracovat globální paměť, která má `CSharedFile`být připojena k .

*bAllowGrow*<br/>
Určuje, zda je povoleno růst bloku paměti.

### <a name="remarks"></a>Poznámky

Pokud *bAllowGrow* je nenulová, velikost bloku paměti se zvýší podle potřeby, například pokud se pokusíte zapsat více bajtů do souboru, než je velikost bloku paměti.

## <a name="see-also"></a>Viz také

[CMemFile – třída](../../mfc/reference/cmemfile-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CMemFile – třída](../../mfc/reference/cmemfile-class.md)
