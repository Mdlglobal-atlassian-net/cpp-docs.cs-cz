---
title: CMemFile – třída
ms.date: 11/04/2016
f1_keywords:
- CMemFile
- AFX/CMemFile
- AFX/CMemFile::CMemFile
- AFX/CMemFile::Attach
- AFX/CMemFile::Detach
- AFX/CMemFile::Alloc
- AFX/CMemFile::Free
- AFX/CMemFile::GrowFile
- AFX/CMemFile::Memcpy
- AFX/CMemFile::Realloc
helpviewer_keywords:
- CMemFile [MFC], CMemFile
- CMemFile [MFC], Attach
- CMemFile [MFC], Detach
- CMemFile [MFC], Alloc
- CMemFile [MFC], Free
- CMemFile [MFC], GrowFile
- CMemFile [MFC], Memcpy
- CMemFile [MFC], Realloc
ms.assetid: 20e86515-e465-4f73-b2ea-e49789d63165
ms.openlocfilehash: 1bd88ad17bdb047de4c344ab96f3d9aecbe23c31
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752631"
---
# <a name="cmemfile-class"></a>CMemFile – třída

[Třída CFile](../../mfc/reference/cfile-class.md)-, která podporuje paměťové soubory.

## <a name="syntax"></a>Syntaxe

```
class CMemFile : public CFile
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMemFile::CMemFile](#cmemfile)|Vytvoří objekt souboru paměti.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMemFile::Připojit](#attach)|Připojí blok paměti k `CMemFile`.|
|[CMemFile::Detach](#detach)|Odpojí blok paměti od `CMemFile` a vrátí ukazatel na blok odpojené paměti.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CMemFile::Alloc](#alloc)|Přepište změnit chování přidělení paměti.|
|[CMemFile::Volný](#free)|Přepsat změnit chování umístění paměti deallocation.|
|[CMemFile::GrowFile](#growfile)|Přepište změnit chování při zvětšuje soubor.|
|[CMemFile::Memcpy](#memcpy)|Přepsáním můžete změnit chování kopírování paměti při čtení a zápisu souborů.|
|[CMemFile::Realloc](#realloc)|Přepsání změnit chování přerozdělení paměti.|

## <a name="remarks"></a>Poznámky

Tyto paměťové soubory se chovají jako diskové soubory s tím rozdílem, že soubor je uložen v paměti RAM, nikoli na disku. Paměťový soubor je užitečný pro rychlé dočasné úložiště nebo pro přenos nezpracovaných bajtů nebo serializovaných objektů mezi nezávislými procesy.

`CMemFile`objekty mohou automaticky přidělit vlastní paměť nebo můžete `CMemFile` k objektu připojit vlastní blok paměti voláním [Attach](#attach). V obou případech paměti pro růst souboru `nGrowBytes`paměti automaticky přidělena v `nGrowBytes` krocích po velikosti, pokud není nula.

Blok paměti bude automaticky odstraněn při `CMemFile` zničení objektu, pokud byla `CMemFile` paměť původně přidělena objektem; v opačném případě jste zodpovědní za zrušení přidělení paměti, kterou jste připojili k objektu.

K bloku paměti můžete přistupovat prostřednictvím ukazatele zadaného `CMemFile` při odpojení od objektu voláním [odpojit](#detach).

Nejběžnější použití `CMemFile` je vytvořit `CMemFile` objekt a použít jej voláním [CFile](../../mfc/reference/cfile-class.md) členské funkce. Všimněte si, že vytvoření `CMemFile` automaticky otevře: nemusíte volat [CFile::Open](../../mfc/reference/cfile-class.md#open), který se používá pouze pro soubory na disku. Protože `CMemFile` nepoužívá soubor disku, datový člen `CFile::m_hFile` se nepoužívá.

Členské `CFile` funkce [Duplicate](../../mfc/reference/cfile-class.md#duplicate), [LockRange](../../mfc/reference/cfile-class.md#lockrange)a [UnlockRange](../../mfc/reference/cfile-class.md#unlockrange) nejsou implementovány pro `CMemFile`. Pokud voláte tyto `CMemFile` funkce na objekt, získáte [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

`CMemFile`používá funkce knihovny za běhu [malloc](../../c-runtime-library/reference/malloc.md), [realloc](../../c-runtime-library/reference/realloc.md)a [free](../../c-runtime-library/reference/free.md) to allocate, reallocate a reallocate memory; a vnitřní [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md) blokovat kopírování paměti při čtení a zápisu. Pokud chcete změnit toto chování nebo `CMemFile` chování při zvětšuje `CMemFile` soubor, odvodit vlastní třídy z a přepsat příslušné funkce.

Další informace `CMemFile`o tématu naleznete v článcích Soubory ve knihovně [MFC](../../mfc/files-in-mfc.md) a [Správa paměti (MFC)](../../mfc/memory-management.md) a zpracování [souborů](../../c-runtime-library/file-handling.md) v *odkazu knihovny run-time*.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Soubor C](../../mfc/reference/cfile-class.md)

`CMemFile`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="cmemfilealloc"></a><a name="alloc"></a>CMemFile::Alloc

Tato funkce je `CMemFile` volána členskými funkcemi.

```
virtual BYTE* Alloc(SIZE_T nBytes);
```

### <a name="parameters"></a>Parametry

*nBajtu bajtů*<br/>
Počet bajtů paměti, které mají být přiděleny.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na blok paměti, který byl přidělen, nebo NULL, pokud se přidělení nezdařilo.

### <a name="remarks"></a>Poznámky

Přepsat tuto funkci implementovat vlastní přidělení paměti. Pokud tuto funkci přepíšete, budete pravděpodobně chtít přepsat také [Free](#free) a [Realloc.](#realloc)

Výchozí implementace používá funkci knihovny za běhu [malloc](../../c-runtime-library/reference/malloc.md) k přidělení paměti.

## <a name="cmemfileattach"></a><a name="attach"></a>CMemFile::Připojit

Voláním této funkce připojíte `CMemFile`blok paměti k aplikaci .

```cpp
void Attach(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>Parametry

*lpBuffer*<br/>
Ukazatel na vyrovnávací paměť, `CMemFile`která má být připojena k .

*nVelikost vyrovnávací paměti*<br/>
Celé číslo, které určuje velikost vyrovnávací paměti v bajtů.

*nGrowBytes*<br/>
Přírůstek přidělení paměti v bajtů.

### <a name="remarks"></a>Poznámky

To `CMemFile` způsobí, že použití bloku paměti jako soubor paměti.

Pokud *nGrowBytes* je `CMemFile` 0, nastaví délku souboru *na nBufferSize*. To znamená, že data v bloku paměti `CMemFile` před připojením k budou použita jako soubor. Paměťové soubory vytvořené tímto způsobem nelze pěstovat.

Vzhledem k tomu, že soubor `CMemFile` nelze zvětšit, dávejte pozor, abyste nezpůsobili pokus o jeho růst. `CMemFile` Například nevolejte přepsání [CFile:Write](../../mfc/reference/cfile-class.md#write) pro zápis za konec nebo nevolejte [CFile:SetLength](../../mfc/reference/cfile-class.md#setlength) s délkou delší než *nBufferSize*.

Pokud *nGrowBytes* je větší `CMemFile` než 0, bude ignorovat obsah bloku paměti, které jste připojili. Budete muset napsat obsah paměťového souboru od `CMemFile` začátku `CFile::Write`pomocí přepsání aplikace . Pokud se pokusíte zapsat za konec souboru nebo `CMemFile` zvětšit `CFile::SetLength` `CMemFile` soubor voláním přepsání , zvýší přidělení paměti v přírůstcích *nGrowBytes*. Rozšíření přidělení paměti se nezdaří, pokud `Attach` blok paměti, do které předáte, nebyl přidělen metodou kompatibilní s [Alloc](#alloc). Chcete-li být kompatibilní `Alloc`s výchozí implementací aplikace , je nutné přidělit paměť s funkcí knihovny za běhu [malloc](../../c-runtime-library/reference/malloc.md) nebo [calloc](../../c-runtime-library/reference/calloc.md).

## <a name="cmemfilecmemfile"></a><a name="cmemfile"></a>CMemFile::CMemFile

První přetížení otevře prázdný soubor paměti.

```
CMemFile(UINT nGrowBytes = 1024);

CMemFile(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>Parametry

*nGrowBytes*<br/>
Přírůstek přidělení paměti v bajtů.

*lpBuffe*r Ukazatel na vyrovnávací paměť, která přijímá informace o velikosti *nBufferSize*.

*nVelikost vyrovnávací paměti*<br/>
Celé číslo, které určuje velikost vyrovnávací paměti souboru v bajtech.

### <a name="remarks"></a>Poznámky

Všimněte si, že soubor je otevřen konstruktorem a že byste neměli volat [CFile::Open](../../mfc/reference/cfile-class.md#open).

Druhé přetížení funguje stejně, jako kdybyste použili první konstruktor a okamžitě volal [Připojit](#attach) se stejnými parametry. Podrobnosti viz `Attach`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#36](../../atl-mfc-shared/reference/codesnippet/cpp/cmemfile-class_1.cpp)]

## <a name="cmemfiledetach"></a><a name="detach"></a>CMemFile::Detach

Volání této funkce získat ukazatel na blok `CMemFile`paměti používá .

```
BYTE* Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na blok paměti, který obsahuje obsah paměťového souboru.

### <a name="remarks"></a>Poznámky

Volání této funkce také `CMemFile`zavře . K bloku paměti můžete `CMemFile` znovu připojit voláním [Připojit](#attach). Chcete-li soubor znovu připojit a použít data v něm, měli byste před voláním `Detach`zavolejte [CFile::GetLength,](../../mfc/reference/cfile-class.md#getlength) abyste získali délku souboru . Všimněte si, že pokud `CMemFile` připojíte blok paměti, `nGrowBytes` takže můžete použít jeho data ( == 0), pak nebudete moci zvětšit soubor paměti.

## <a name="cmemfilefree"></a><a name="free"></a>CMemFile::Volný

Tato funkce je `CMemFile` volána členskými funkcemi.

```
virtual void Free(BYTE* lpMem);
```

### <a name="parameters"></a>Parametry

*lpMem*<br/>
Ukazatel na paměť, která má být přidělena.

### <a name="remarks"></a>Poznámky

Přepsat tuto funkci implementovat vlastní paměti deallocation. Pokud tuto funkci přepíšete, budete pravděpodobně chtít přepsat také [Alloc](#alloc) a [Realloc.](#realloc)

## <a name="cmemfilegrowfile"></a><a name="growfile"></a>CMemFile::GrowFile

Tato funkce je volána `CMemFile` několika členskými funkcemi.

```
virtual void GrowFile(SIZE_T dwNewLen);
```

### <a name="parameters"></a>Parametry

*dwNewLen*<br/>
Nová velikost paměťového souboru.

### <a name="remarks"></a>Poznámky

Můžete přepsat, pokud chcete změnit, `CMemFile` jak roste jeho soubor. Výchozí implementace volá [Realloc](#realloc) růst existující blok (nebo [Alloc](#alloc) vytvořit blok paměti), přidělování paměti `nGrowBytes` v násobcích hodnoty zadané v konstruktoru nebo [Připojit](#attach) volání.

## <a name="cmemfilememcpy"></a><a name="memcpy"></a>CMemFile::Memcpy

Tato funkce je `CMemFile` volána přepsáním [CFile::Read](../../mfc/reference/cfile-class.md#read) a [CFile::Write](../../mfc/reference/cfile-class.md#write) pro přenos dat do a z paměťového souboru.

```
virtual BYTE* Memcpy(
    BYTE* lpMemTarget,
    const BYTE* lpMemSource,
    SIZE_T nBytes);
```

### <a name="parameters"></a>Parametry

*lpMemTarget*<br/>
Ukazatel na blok paměti, do kterého bude zkopírována zdrojová paměť.

*lpMemsource*<br/>
Ukazatel na blok zdrojové paměti.

*nBajtu bajtů*<br/>
Počet bajtů, které mají být zkopírovány.

### <a name="return-value"></a>Návratová hodnota

Kopie *lpMemTarget*.

### <a name="remarks"></a>Poznámky

Přepsat tuto funkci, pokud chcete změnit `CMemFile` způsob, jakým se tyto kopie paměti.

## <a name="cmemfilerealloc"></a><a name="realloc"></a>CMemFile::Realloc

Tato funkce je `CMemFile` volána členskými funkcemi.

```
virtual BYTE* Realloc(
    BYTE* lpMem,
    SIZE_T nBytes);
```

### <a name="parameters"></a>Parametry

*lpMem*<br/>
Ukazatel na blok paměti, který má být přerozdělen.

*nBajtu bajtů*<br/>
Nová velikost pro blok paměti.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na blok paměti, který byl přerozdělen (a případně přesunut) nebo NULL, pokud se přerozdělení nezdařilo.

### <a name="remarks"></a>Poznámky

Přepsat tuto funkci implementovat vlastní přerozdělení paměti. Pokud tuto funkci přepíšete, budete pravděpodobně chtít přepsat také [Alloc](#alloc) a [Free.](#free)

## <a name="see-also"></a>Viz také

[CFile – třída](../../mfc/reference/cfile-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
