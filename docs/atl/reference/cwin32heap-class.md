---
title: CWin32Heap – třída
ms.date: 11/04/2016
f1_keywords:
- CWin32Heap
- ATLMEM/ATL::CWin32Heap
- ATLMEM/ATL::CWin32Heap::CWin32Heap
- ATLMEM/ATL::CWin32Heap::Allocate
- ATLMEM/ATL::CWin32Heap::Attach
- ATLMEM/ATL::CWin32Heap::Detach
- ATLMEM/ATL::CWin32Heap::Free
- ATLMEM/ATL::CWin32Heap::GetSize
- ATLMEM/ATL::CWin32Heap::Reallocate
- ATLMEM/ATL::CWin32Heap::m_bOwnHeap
- ATLMEM/ATL::CWin32Heap::m_hHeap
helpviewer_keywords:
- CWin32Heap class
ms.assetid: 69176022-ed98-4e3b-96d8-116b0c58ac95
ms.openlocfilehash: ce3585310198ee3e2d7b2b8b829f4202b1021284
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496204"
---
# <a name="cwin32heap-class"></a>CWin32Heap – třída

Tato třída implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) pomocí funkcí přidělení haldy Win32.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CWin32Heap : public IAtlMemMgr
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CWin32Heap:: CWin32Heap](#cwin32heap)|Konstruktor|
|[CWin32Heap:: ~ CWin32Heap](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CWin32Heap:: allocate](#allocate)|Přidělí blok paměti z objektu haldy.|
|[CWin32Heap:: Attach](#attach)|Připojí objekt haldy k existující haldě.|
|[CWin32Heap::Detach](#detach)|Odpojí objekt haldy od existující haldy.|
|[CWin32Heap:: Free](#free)|Uvolní paměť, která byla dříve přidělena z haldy.|
|[CWin32Heap:: GetSize](#getsize)|Vrací velikost bloku paměti přiděleného z objektu haldy.|
|[CWin32Heap:: realokaci](#reallocate)|Znovu přidělí blok paměti z objektu haldy.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CWin32Heap::m_bOwnHeap](#m_bownheap)|Příznak sloužící k určení aktuálního vlastnictví obslužné rutiny haldy.|
|[CWin32Heap::m_hHeap](#m_hheap)|Zpracování objektu haldy.|

## <a name="remarks"></a>Poznámky

`CWin32Heap`implementuje metody přidělování paměti pomocí funkcí přidělení haldy Win32, včetně [HeapAlloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc) a [HeapFree](/windows/win32/api/heapapi/nf-heapapi-heapfree). Na rozdíl od jiných tříd `CWin32Heap` haldy vyžaduje před přidělením paměti platný popisovač haldy: jiné třídy jsou standardně použity pro použití haldy procesu. Popisovač lze dodávat do konstruktoru nebo do metody [CWin32Heap:: Attach](#attach) . Další podrobnosti naleznete v metodě [CWin32Heap:: CWin32Heap](#cwin32heap) .

## <a name="example"></a>Příklad

Podívejte se na příklad pro [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IAtlMemMgr`

`CWin32Heap`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlmem. h

##  <a name="allocate"></a>CWin32Heap:: allocate

Přidělí blok paměti z objektu haldy.

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*nBytes*<br/>
Požadovaný počet bajtů v novém bloku paměti.

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na nově přidělený blok paměti.

### <a name="remarks"></a>Poznámky

Zavolejte [CWin32Heap:: Free](#free) nebo [CWin32Heap:: realokaci](#reallocate) pro uvolnění paměti přidělené touto metodou.

Implementováno pomocí [HeapAlloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc).

##  <a name="attach"></a>CWin32Heap:: Attach

Připojí objekt haldy k existující haldě.

```
void Attach(HANDLE hHeap, bool bTakeOwnership) throw();
```

### <a name="parameters"></a>Parametry

*hHeap*<br/>
Existující popisovač haldy.

*bTakeOwnership*<br/>
Příznak označující, `CWin32Heap` zda má objekt převzít vlastnictví pro prostředky haldy.

### <a name="remarks"></a>Poznámky

Pokud má *bTakeOwnership* hodnotu true, `CWin32Heap` je objekt zodpovědný za odstranění popisovače haldy.

##  <a name="cwin32heap"></a>CWin32Heap:: CWin32Heap

Konstruktor

```
CWin32Heap() throw();
CWin32Heap( HANDLE  hHeap) throw();
CWin32Heap(
    DWORD  dwFlags,
    size_t nInitialSize,
    size_t nMaxSize = 0);
```

### <a name="parameters"></a>Parametry

*hHeap*<br/>
Existující objekt haldy

*dwFlags*<br/>
Příznaky použité při vytváření haldy

*nInitialSize*<br/>
Počáteční velikost haldy

*nMaxSize*<br/>
Maximální velikost haldy

### <a name="remarks"></a>Poznámky

Před přidělením paměti je nutné poskytnout `CWin32Heap` objekt s platným popisovačem haldy. Nejsnáze toho dosáhnete pomocí haldy procesu:

[!code-cpp[NVC_ATL_Utilities#92](../../atl/codesnippet/cpp/cwin32heap-class_1.cpp)]

Je také možné zadat do konstruktoru existující popisovač haldy; v tomto případě nový objekt nepřevezme vlastnictví haldy. Původní popisovač haldy bude i nadále platný při `CWin32Heap` odstranění objektu.

Existující haldu lze také připojit k novému objektu pomocí [CWin32Heap:: Attach](#attach).

Pokud se halda vyžaduje tam, kde se všechny operace provádějí z jednoho vlákna, je nejlepší vytvořit tento objekt takto:

[!code-cpp[NVC_ATL_Utilities#93](../../atl/codesnippet/cpp/cwin32heap-class_2.cpp)]

Parametr HEAP_NO_SERIALIZE určuje, že vzájemné vyloučení nebude použito, pokud funkce haldy přidělují a uvolňuje paměť, s ohledem na zvýšení výkonu.

Třetí parametr má výchozí hodnotu 0, což umožňuje, aby halda narůstala podle potřeby. Vysvětlení velikostí a příznaků paměti najdete v tématu [HeapCreate](/windows/win32/api/heapapi/nf-heapapi-heapcreate) .

##  <a name="dtor"></a>CWin32Heap:: ~ CWin32Heap

Destruktor.

```
~CWin32Heap() throw();
```

### <a name="remarks"></a>Poznámky

Odstraní popisovač haldy, pokud `CWin32Heap` má objekt vlastnictví haldy.

##  <a name="detach"></a>CWin32Heap::D etach

Odpojí objekt haldy od existující haldy.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač haldy, ke které byl objekt dříve připojen.

##  <a name="free"></a>CWin32Heap:: Free

Uvolní paměť, která byla dříve přidělena z haldy pomocí [CWin32Heap:: allocate](#allocate) nebo [CWin32Heap:: Reallocate](#reallocate).

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Ukazatel na blok paměti, který je zdarma. Hodnota NULL je platná a neprovádí žádnou akci.

##  <a name="getsize"></a>CWin32Heap:: GetSize

Vrací velikost bloku paměti přiděleného z objektu haldy.

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Ukazatel na blok paměti, jehož velikost bude metoda získávat. Toto je ukazatel vrácený funkcí [CWin32Heap:: allocate](#allocate) nebo [CWin32Heap:: Reallocate](#reallocate).

### <a name="return-value"></a>Návratová hodnota

Vrátí velikost přiděleného bloku paměti (v bajtech).

##  <a name="m_bownheap"></a>CWin32Heap:: m_bOwnHeap

Příznak sloužící k určení aktuálního vlastnictví popisovače haldy uložené v [m_hHeap](#m_hheap).

```
bool m_bOwnHeap;
```

##  <a name="m_hheap"></a>CWin32Heap:: m_hHeap

Zpracování objektu haldy.

```
HANDLE m_hHeap;
```

### <a name="remarks"></a>Poznámky

Proměnná, která slouží k uložení popisovače do objektu haldy.

##  <a name="reallocate"></a>CWin32Heap:: realokaci

Znovu přidělí blok paměti z objektu haldy.

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Ukazatel na blok paměti, který se má znovu přidělit.

*nBytes*<br/>
Nová velikost přiděleného bloku v bajtech Blok může být větší nebo menší.

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na nově přidělený blok paměti.

### <a name="remarks"></a>Poznámky

Pokud má *p* hodnotu null, předpokládá se, že blok paměti ještě není přidělený, a [CWin32Heap:: allocate](#allocate) se volá s argumentem *nBytes*.

## <a name="see-also"></a>Viz také:

[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[IAtlMemMgr – třída](../../atl/reference/iatlmemmgr-class.md)<br/>
[CLocalHeap – třída](../../atl/reference/clocalheap-class.md)<br/>
[CGlobalHeap – třída](../../atl/reference/cglobalheap-class.md)<br/>
[CCRTHeap – třída](../../atl/reference/ccrtheap-class.md)<br/>
[CComHeap – třída](../../atl/reference/ccomheap-class.md)
