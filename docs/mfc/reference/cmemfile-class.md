---
title: Cmemfile – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 90203a2e4fc29b28e6c75193ed1db35e25044951
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50076955"
---
# <a name="cmemfile-class"></a>Cmemfile – třída

[Cfile –](../../mfc/reference/cfile-class.md)-odvozené třídy, která podporuje soubory z paměti.

## <a name="syntax"></a>Syntaxe

```
class CMemFile : public CFile
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMemFile::CMemFile](#cmemfile)|Vytvoří objekt soubor paměti.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMemFile::Attach](#attach)|Připojí blok paměti `CMemFile`.|
|[CMemFile::Detach](#detach)|Odpojí blok paměti z `CMemFile` a vrací ukazatel na blok paměti, odpojeno.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CMemFile::Alloc](#alloc)|Přepsání nastavení za účelem upravují chování při přidělování paměti.|
|[CMemFile::Free](#free)|Přepsání nastavení za účelem upravují chování při zrušení přidělení paměti.|
|[CMemFile::GrowFile](#growfile)|Přepsání nastavení za účelem upravují chování při pokusu o souboru.|
|[CMemFile::Memcpy](#memcpy)|Přepsání nastavení za účelem upravují chování při kopírování paměti při čtení a zápis do souborů.|
|[CMemFile::Realloc](#realloc)|Přepsání nastavení za účelem změnit chování realokace paměti.|

## <a name="remarks"></a>Poznámky

Tyto soubory z paměti se chovat jako soubory disku s tím rozdílem, že je soubor uložený v paměti RAM, nikoli na disku. Soubor paměti je užitečné pro rychlé dočasné úložiště nebo při přenosech nezpracovaná bajtů nebo serializovat objekty mezi nezávislé procesy.

`CMemFile` objekty mohou automaticky přidělit paměť, vlastní nebo můžete připojit vlastní bloku paměti `CMemFile` objektu voláním [připojit](#attach). V obou případech je přidělena paměť pro soubor paměti automaticky rostoucí `nGrowBytes`-zvýší velikost, pokud `nGrowBytes` není nula.

Blok paměti bude automaticky odstraněno při odstranění `CMemFile` objektu, pokud byl původně přidělí paměť `CMemFile` objektu; v opačném případě budete muset rušení přidělení paměti připojen k objektu.

Blok paměti přístupné prostřednictvím ukazatele zadaný při odpojení od `CMemFile` objektu voláním [odpojit](#detach).

Nejběžnější použití nástroje `CMemFile` je vytvořit `CMemFile` objektu a použít ho voláním [cfile –](../../mfc/reference/cfile-class.md) členské funkce. Všimněte si, že vytváření `CMemFile` automaticky otevře: Nevolejte [CFile::Open](../../mfc/reference/cfile-class.md#open), který se používá pouze pro soubory na disku. Protože `CMemFile` nepoužívá soubor na disku, datový člen `CFile::m_hFile` se nepoužívá.

`CFile` Členské funkce [duplicitní](../../mfc/reference/cfile-class.md#duplicate), [LockRange](../../mfc/reference/cfile-class.md#lockrange), a [UnlockRange](../../mfc/reference/cfile-class.md#unlockrange) nejsou implementovány pro `CMemFile`. Při volání těchto funkcí na `CMemFile` objektu, zobrazí se [cnotsupportedexception –](../../mfc/reference/cnotsupportedexception-class.md).

`CMemFile` používá funkce knihovny run-time [malloc](../../c-runtime-library/reference/malloc.md), [realloc](../../c-runtime-library/reference/realloc.md), a [bezplatné](../../c-runtime-library/reference/free.md) přidělit, přerozdělit a uvolnit paměť; a vnitřní [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md) do bloku kopírování paměti při čtení a zápisu. Pokud chcete změnit toto chování nebo chování při `CMemFile` roste souboru, odvodit vlastní třídu z `CMemFile` a přepsat odpovídající funkce.

Další informace o `CMemFile`, najdete v článcích [soubory v prostředí MFC](../../mfc/files-in-mfc.md) a [správy paměti (MFC)](../../mfc/memory-management.md) a zobrazit [zpracování souborů](../../c-runtime-library/file-handling.md) v *za běhu Referenční dokumentace ke knihovně*.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cfile –](../../mfc/reference/cfile-class.md)

`CMemFile`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

##  <a name="alloc"></a>  CMemFile::Alloc

Tato funkce je volána `CMemFile` členské funkce.

```
virtual BYTE* Alloc(SIZE_T nBytes);
```

### <a name="parameters"></a>Parametry

*nBytes*<br/>
Počet bajtů paměti, která bude přidělena.

### <a name="return-value"></a>Návratová hodnota

Ukazatele na blok paměti, která byla přidělena, nebo hodnota NULL, pokud přidělení paměti se nezdařilo.

### <a name="remarks"></a>Poznámky

Potlačí tuto funkci, která implementuje vlastní paměť přidělení. Pokud přepíšete tuto funkci, budete pravděpodobně chtít přepsat [Free](#free) a [Realloc](#realloc) také.

Výchozí implementace používá funkce knihovny run-time [malloc](../../c-runtime-library/reference/malloc.md) přidělení paměti.

##  <a name="attach"></a>  CMemFile::Attach

Voláním této funkce připojit blok paměti `CMemFile`.

```
void Attach(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>Parametry

*lpBuffer.*<br/>
Ukazatel do vyrovnávací paměti, který má být přiřazena k `CMemFile`.

*nBufferSize*<br/>
Celé číslo, které určuje velikost vyrovnávací paměti v bajtech.

*nGrowBytes*<br/>
Zvýšení přidělení paměti v bajtech.

### <a name="remarks"></a>Poznámky

To způsobí, že `CMemFile` použít blok paměti jako soubor paměti.

Pokud *nGrowBytes* je 0, `CMemFile` nastaví délku souboru na *nBufferSize*. To znamená, že data v blok paměti dříve, než byl připojen k `CMemFile` se použije jako soubor. Nelze se zvětšil na velikost paměti soubory vytvořené tímto způsobem.

Protože soubor nelze pěstuje, dejte pozor, abyste způsobit `CMemFile` pokusu o zvětšení souboru. Například nemůžete volat `CMemFile` přepsání [CFile:Write](../../mfc/reference/cfile-class.md#write) k zápisu za koncem nebo Nevolejte [CFile:SetLength](../../mfc/reference/cfile-class.md#setlength) s delší, než *nBufferSize*.

Pokud *nGrowBytes* je větší než 0, `CMemFile` bude ignorovat obsah bloku paměti, který jste připojili. Budete mít k zápisu obsahu souboru paměti od začátku pomocí `CMemFile` přepsání `CFile::Write`. Pokud se pokusíte zapsat za koncem souboru nebo zvětšení souboru voláním `CMemFile` přepsání `CFile::SetLength`, `CMemFile` se zvýší přidělení paměti v přírůstcích po *nGrowBytes*. Stále se rozšiřující přidělení paměti se nezdaří, pokud blok paměti, můžete předat `Attach` nepřidělil kompatibilní s metodou [alokační](#alloc). Aby byl kompatibilní s výchozí implementace `Alloc`, musíte přidělit paměť pomocí funkce knihovny run-time [malloc](../../c-runtime-library/reference/malloc.md) nebo [calloc](../../c-runtime-library/reference/calloc.md).

##  <a name="cmemfile"></a>  CMemFile::CMemFile

První přetížení se otevře soubor prázdný paměti.

```
CMemFile(UINT nGrowBytes = 1024);

CMemFile(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>Parametry

*nGrowBytes*<br/>
Zvýšení přidělení paměti v bajtech.

*lpBuffe*r ukazatel do vyrovnávací paměti, která bude přijímat informace o velikosti *nBufferSize*.

*nBufferSize*<br/>
Celé číslo, které určuje velikost vyrovnávací paměti souboru v bajtech.

### <a name="remarks"></a>Poznámky

Mějte na paměti, že je soubor otevřen v konstruktoru a jestli byste neměli volat [CFile::Open](../../mfc/reference/cfile-class.md#open).

Druhé přetížení funguje stejné, jako kdyby jste použili první konstruktor a okamžitě volá [připojit](#attach) se stejnými parametry. Zobrazit `Attach` podrobnosti.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#36](../../atl-mfc-shared/reference/codesnippet/cpp/cmemfile-class_1.cpp)]

##  <a name="detach"></a>  CMemFile::Detach

Voláním této funkce získání ukazatele na blok paměti, která je používána ve `CMemFile`.

```
BYTE* Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatele na blok paměti, který obsahuje obsah souboru paměti.

### <a name="remarks"></a>Poznámky

Volání této funkce také zavře `CMemFile`. Můžete znovu připojit blok paměti určený k `CMemFile` voláním [připojit](#attach). Pokud chcete soubor znovu připojit a používat data, měli byste zavolat [CFile::GetLength](../../mfc/reference/cfile-class.md#getlength) získat délku souboru před voláním `Detach`. Všimněte si, že pokud připojíte blok paměti určený k `CMemFile` tak, aby jeho data je možné použít ( `nGrowBytes` == 0), nebude moct zvětšení souboru paměti.

##  <a name="free"></a>  CMemFile::Free

Tato funkce je volána `CMemFile` členské funkce.

```
virtual void Free(BYTE* lpMem);
```

### <a name="parameters"></a>Parametry

*lpMem*<br/>
Ukazatel na uvolnění paměti.

### <a name="remarks"></a>Poznámky

Přepsání této funkce zrušení přidělení paměti pro vlastní implementaci. Pokud přepíšete tuto funkci, budete pravděpodobně chtít přepsat [alokační](#alloc) a [Realloc](#realloc) také.

##  <a name="growfile"></a>  CMemFile::GrowFile

Tato funkce je volána více `CMemFile` členské funkce.

```
virtual void GrowFile(SIZE_T dwNewLen);
```

### <a name="parameters"></a>Parametry

*dwNewLen*<br/>
Nová velikost souboru paměti.

### <a name="remarks"></a>Poznámky

Můžete přepsat, pokud chcete změnit způsob `CMemFile` roste jeho souboru. Výchozí implementace volá [Realloc](#realloc) rozšířit existující blok (nebo [alokační](#alloc) vytvořit blok paměti), přidělení paměti v násobcích `nGrowBytes` hodnotu zadanou v konstruktoru nebo [Připojit](#attach) volání.

##  <a name="memcpy"></a>  CMemFile::Memcpy

Tato funkce je volána `CMemFile` přepsání [CFile::Read](../../mfc/reference/cfile-class.md#read) a [CFile::Write](../../mfc/reference/cfile-class.md#write) k přenosu dat do a ze souboru paměti.

```
virtual BYTE* Memcpy(
    BYTE* lpMemTarget,
    const BYTE* lpMemSource,
    SIZE_T nBytes);
```

### <a name="parameters"></a>Parametry

*lpMemTarget*<br/>
Ukazatele na blok paměti, do které budou zkopírovány paměti zdroje.

*lpMemSource*<br/>
Ukazatele na blok paměti zdroje.

*nBytes*<br/>
Počet bajtů, které mají být zkopírovány.

### <a name="return-value"></a>Návratová hodnota

Kopie *lpMemTarget*.

### <a name="remarks"></a>Poznámky

Přepsat tuto funkci, pokud chcete změnit způsob, který `CMemFile` dělá tyto kopie v paměti.

##  <a name="realloc"></a>  CMemFile::Realloc

Tato funkce je volána `CMemFile` členské funkce.

```
virtual BYTE* Realloc(
    BYTE* lpMem,
    SIZE_T nBytes);
```

### <a name="parameters"></a>Parametry

*lpMem*<br/>
Ukazatele na blok paměti určený k znovu přidělit.

*nBytes*<br/>
Nová velikost bloku paměti.

### <a name="return-value"></a>Návratová hodnota

Ukazatele na blok paměti, který byl a nevyčerpané prostředky (pravděpodobně přesunut), nebo hodnota NULL, pokud přerozdělení se nezdařilo.

### <a name="remarks"></a>Poznámky

Tuto funkci implementovat vlastní paměti realokace přepište. Pokud přepíšete tuto funkci, budete pravděpodobně chtít přepsat [alokační](#alloc) a [Free](#free) také.

## <a name="see-also"></a>Viz také

[CFile – třída](../../mfc/reference/cfile-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)

