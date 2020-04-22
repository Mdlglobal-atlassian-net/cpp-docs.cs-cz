---
title: Třída CWin32HeAP
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
ms.openlocfilehash: 2d79de308b1afb3059cf04ad40b63b6e603073c8
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746031"
---
# <a name="cwin32heap-class"></a>Třída CWin32HeAP

Tato třída implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) pomocí win32 funkce přidělení haldy.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CWin32Heap : public IAtlMemMgr
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CWin32Heap::CWin32Heap](#cwin32heap)|Konstruktor|
|[CWin32Heap::~CWin32Heap](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CWin32HeAP::Přidělit](#allocate)|Přidělí blok paměti z objektu haldy.|
|[CWin32HeAP::Připojit](#attach)|Připojí objekt haldy k existující haldě.|
|[CWin32Heap::Detach](#detach)|Odpojí objekt haldy od existující haldy.|
|[CWin32Heap::Zdarma](#free)|Uvolní paměť dříve přidělené z haldy.|
|[CWin32Heap::GetSize](#getsize)|Vrátí velikost bloku paměti přiděleného z objektu haldy.|
|[CWin32HeAP::Přerozdělit](#reallocate)|Přerozdělí blok paměti z objektu haldy.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CWin32Heap::m_bOwnHeap](#m_bownheap)|Příznak používaný k určení aktuálního vlastnictví popisovače haldy.|
|[CWin32Heap::m_hHeap](#m_hheap)|Zpracovat objekt haldy.|

## <a name="remarks"></a>Poznámky

`CWin32Heap`implementuje metody přidělení paměti pomocí win32 funkce přidělení haldy, včetně [HeapAlloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc) a [HeapFree](/windows/win32/api/heapapi/nf-heapapi-heapfree). Na rozdíl od `CWin32Heap` jiných haldy třídy vyžaduje platný popisovač haldy, které mají být poskytnuty před přidělením paměti: ostatní třídy výchozí použití haldy procesu. Popisovač může být dodánkonstruktoru nebo [CWin32Heap::Attach](#attach) method. Další podrobnosti naleznete v metodě [CWin32Heap::CWin32Heap.](#cwin32heap)

## <a name="example"></a>Příklad

Viz příklad pro [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IAtlMemMgr`

`CWin32Heap`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlmem.h

## <a name="cwin32heapallocate"></a><a name="allocate"></a>CWin32HeAP::Přidělit

Přidělí blok paměti z objektu haldy.

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*nBajtu bajtů*<br/>
Požadovaný počet bajtů v novém bloku paměti.

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na nově přidělený blok paměti.

### <a name="remarks"></a>Poznámky

Volání [CWin32Heap::Free](#free) nebo [CWin32Heap::Reallocate](#reallocate) uvolnit paměť přidělené touto metodou.

Implementováno pomocí [HeapAlloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc).

## <a name="cwin32heapattach"></a><a name="attach"></a>CWin32HeAP::Připojit

Připojí objekt haldy k existující haldě.

```cpp
void Attach(HANDLE hHeap, bool bTakeOwnership) throw();
```

### <a name="parameters"></a>Parametry

*h Hromada*<br/>
Existující popisovač haldy.

*bTakeOwnership*<br/>
Příznak označující, `CWin32Heap` pokud je objekt převzít vlastnictví nad prostředky haldy.

### <a name="remarks"></a>Poznámky

Pokud *bTakeOwnership* je `CWin32Heap` PRAVDA, objekt je zodpovědný za odstranění popisovače haldy.

## <a name="cwin32heapcwin32heap"></a><a name="cwin32heap"></a>CWin32Heap::CWin32Heap

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

*h Hromada*<br/>
Existující objekt haldy

*dwFlags*<br/>
Příznaky použité při vytváření haldy

*nInitialSize*<br/>
Počáteční velikost haldy

*nVelikost Max*<br/>
Maximální velikost haldy

### <a name="remarks"></a>Poznámky

Před přidělením paměti je nutné poskytnout `CWin32Heap` objektu platný popisovač haldy. Nejsnáze toho dosáhnete pomocí haldy procesu:

[!code-cpp[NVC_ATL_Utilities#92](../../atl/codesnippet/cpp/cwin32heap-class_1.cpp)]

Je také možné zadat do konstruktoru existující popisovač haldy; v tomto případě nový objekt nepřevezme vlastnictví haldy. Původní popisovač haldy bude `CWin32Heap` stále platný, když je objekt odstraněn.

Existující haldy lze také připojit k novému objektu pomocí [CWin32Heap::Attach](#attach).

Pokud se halda vyžaduje tam, kde se všechny operace provádějí z jednoho vlákna, je nejlepší vytvořit tento objekt takto:

[!code-cpp[NVC_ATL_Utilities#93](../../atl/codesnippet/cpp/cwin32heap-class_2.cpp)]

Parametr HEAP_NO_SERIALIZE určuje, že vzájemné vyloučení nebude použito při přidělení a uvolnění paměti haldy s odpovídajícím zvýšením výkonu.

Třetí parametr má výchozí hodnotu 0, což umožňuje, aby halda narůstala podle potřeby. Viz [HeapCreate](/windows/win32/api/heapapi/nf-heapapi-heapcreate) vysvětlení velikosti paměti a příznaky.

## <a name="cwin32heapcwin32heap"></a><a name="dtor"></a>CWin32Heap::~CWin32Heap

Destruktor.

```
~CWin32Heap() throw();
```

### <a name="remarks"></a>Poznámky

Zničí popisovač haldy, `CWin32Heap` pokud má objekt vlastnictví haldy.

## <a name="cwin32heapdetach"></a><a name="detach"></a>CWin32Heap::Detach

Odpojí objekt haldy od existující haldy.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač haldy, ke které byl objekt dříve připojen.

## <a name="cwin32heapfree"></a><a name="free"></a>CWin32Heap::Zdarma

Uvolní paměť dříve přidělené z haldy [CWin32Heap::Allocate](#allocate) nebo [CWin32Heap::Reallocate](#reallocate).

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Ukazatel na blok paměti zdarma. Null je platná hodnota a neprovede žádné neprovede akci.

## <a name="cwin32heapgetsize"></a><a name="getsize"></a>CWin32Heap::GetSize

Vrátí velikost bloku paměti přiděleného z objektu haldy.

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Ukazatel na blok paměti, jehož velikost metoda získá. Toto je ukazatel vrácený [CWin32Heap::Allocate](#allocate) nebo [CWin32Heap::Reallocate](#reallocate).

### <a name="return-value"></a>Návratová hodnota

Vrátí velikost bloku přidělené paměti v bajtech.

## <a name="cwin32heapm_bownheap"></a><a name="m_bownheap"></a>CWin32Heap::m_bOwnHeap

Příznak slouží k určení aktuální vlastnictví popisovače haldy uložené v [m_hHeap](#m_hheap).

```
bool m_bOwnHeap;
```

## <a name="cwin32heapm_hheap"></a><a name="m_hheap"></a>CWin32Heap::m_hHeap

Zpracovat objekt haldy.

```
HANDLE m_hHeap;
```

### <a name="remarks"></a>Poznámky

Proměnná slouží k uložení popisovače do objektu haldy.

## <a name="cwin32heapreallocate"></a><a name="reallocate"></a>CWin32HeAP::Přerozdělit

Přerozdělí blok paměti z objektu haldy.

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Ukazatel na blok paměti přerozdělit.

*nBajtu bajtů*<br/>
Nová velikost v bajtů přiděleného bloku. Blok může být větší nebo menší.

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na nově přidělený blok paměti.

### <a name="remarks"></a>Poznámky

Pokud *p* je NULL, předpokládá se, že blok paměti ještě nebyla přidělena a [CWin32Heap::Allocate](#allocate) je volána, s argumentem *nBytes*.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Třída IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)<br/>
[Třída CLocalHeap](../../atl/reference/clocalheap-class.md)<br/>
[Třída CGlobalHeap](../../atl/reference/cglobalheap-class.md)<br/>
[Třída CCRTHeAP](../../atl/reference/ccrtheap-class.md)<br/>
[Třída CComHeap](../../atl/reference/ccomheap-class.md)
