---
title: Cwin32heap – třída
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
ms.openlocfilehash: 35c12a58adc846e0db6d7ee23f19984acbcfa861
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62276910"
---
# <a name="cwin32heap-class"></a>Cwin32heap – třída

Tato třída implementuje [iatlmemmgr –](../../atl/reference/iatlmemmgr-class.md) pomocí funkcí přidělení haldy Win32.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

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
|[CWin32Heap::Allocate](#allocate)|Přiděluje blok paměti z haldy objektu.|
|[CWin32Heap::Attach](#attach)|Objekt haldy se připojí k existující haldu.|
|[CWin32Heap::Detach](#detach)|Odpojí objekt haldy od existující haldu.|
|[CWin32Heap::Free](#free)|Uvolní paměť přidělenou dříve z haldy.|
|[CWin32Heap::GetSize](#getsize)|Vrátí velikost bloku paměti přidělené z objektu haldy.|
|[CWin32Heap::Reallocate](#reallocate)|Znovu alokuje blok paměti z haldy objektu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CWin32Heap::m_bOwnHeap](#m_bownheap)|Příznak, který se používá k určení aktuální vlastnictví popisovač haldy.|
|[CWin32Heap::m_hHeap](#m_hheap)|Popisovač objektu haldy.|

## <a name="remarks"></a>Poznámky

`CWin32Heap` implementuje metody přidělení paměti pomocí funkcí přidělení haldy Win32 včetně [HeapAlloc](/windows/desktop/api/heapapi/nf-heapapi-heapalloc) a [HeapFree](/windows/desktop/api/heapapi/nf-heapapi-heapfree). Na rozdíl od jiných tříd haldy `CWin32Heap` vyžaduje platným popisovačem haldy poskytované předtím, než je paměť přidělena: ostatní výchozí třídy pomocí haldy procesu. Popisovač lze je zadat do konstruktoru nebo položky [CWin32Heap::Attach](#attach) metody. Zobrazit [CWin32Heap::CWin32Heap](#cwin32heap) metoda pro další podrobnosti.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [iatlmemmgr –](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IAtlMemMgr`

`CWin32Heap`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlmem.h

##  <a name="allocate"></a>  CWin32Heap::Allocate

Přiděluje blok paměti z haldy objektu.

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*nBytes*<br/>
Požadovaný počet bajtů v nového bloku paměti.

### <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na nově přidělenou paměť bloku.

### <a name="remarks"></a>Poznámky

Volání [CWin32Heap::Free](#free) nebo [CWin32Heap::Reallocate](#reallocate) k uvolnění paměti přidělené touto metodou.

Implementované pomocí [HeapAlloc](/windows/desktop/api/heapapi/nf-heapapi-heapalloc).

##  <a name="attach"></a>  CWin32Heap::Attach

Objekt haldy se připojí k existující haldu.

```
void Attach(HANDLE hHeap, bool bTakeOwnership) throw();
```

### <a name="parameters"></a>Parametry

*hHeap*<br/>
Existující popisovač haldy.

*bTakeOwnership*<br/>
A pokud příznak indikující `CWin32Heap` objekt je převzít vlastnictví zdroje haldy.

### <a name="remarks"></a>Poznámky

Pokud *bTakeOwnership* má hodnotu TRUE, `CWin32Heap` objektu je odpovědný za odstranění popisovač haldy.

##  <a name="cwin32heap"></a>  CWin32Heap::CWin32Heap

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

Před přidělením paměti, je potřeba zadat `CWin32Heap` objekt s platným popisovačem haldy. Nejsnáze toho dosáhnete pomocí haldy procesu:

[!code-cpp[NVC_ATL_Utilities#92](../../atl/codesnippet/cpp/cwin32heap-class_1.cpp)]

Je také možné zadat do konstruktoru existující popisovač haldy; v tomto případě nový objekt nepřevezme vlastnictví haldy. Původní popisovač haldy bude stále platit `CWin32Heap` objekt odstranit.

Existující haldu lze také připojit k novému objektu pomocí [CWin32Heap::Attach](#attach).

Pokud se halda vyžaduje tam, kde se všechny operace provádějí z jednoho vlákna, je nejlepší vytvořit tento objekt takto:

[!code-cpp[NVC_ATL_Utilities#93](../../atl/codesnippet/cpp/cwin32heap-class_2.cpp)]

Parametr HEAP_NO_SERIALIZE Určuje, že nebude používat vzájemné vyloučení, pokud funkce haldy přidělují a uvolňují paměť, zvýšení výkonu.

Třetí parametr má výchozí hodnotu 0, což umožňuje, aby halda narůstala podle potřeby. Zobrazit [HeapCreate](/windows/desktop/api/heapapi/nf-heapapi-heapcreate) vysvětlení velikostí paměti a příznaků.

##  <a name="dtor"></a>  CWin32Heap:: ~ CWin32Heap

Destruktor.

```
~CWin32Heap() throw();
```

### <a name="remarks"></a>Poznámky

Zničí popisovač haldy, pokud `CWin32Heap` objekt má vlastnictví haldy.

##  <a name="detach"></a>  CWin32Heap::Detach

Odpojí objekt haldy od existující haldu.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač haldy, do které byl objekt dříve připojen.

##  <a name="free"></a>  CWin32Heap::Free

Uvolní paměť přidělenou dříve z haldy ve [CWin32Heap::Allocate](#allocate) nebo [CWin32Heap::Reallocate](#reallocate).

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Ukazatele na blok paměti pro uvolnění. Hodnota NULL je platnou hodnotu a nemá žádný účinek.

##  <a name="getsize"></a>  CWin32Heap::GetSize

Vrátí velikost bloku paměti přidělené z objektu haldy.

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Ukazatele na blok paměti, jejichž velikost se získat metodu. Toto je vrácený ukazatel [CWin32Heap::Allocate](#allocate) nebo [CWin32Heap::Reallocate](#reallocate).

### <a name="return-value"></a>Návratová hodnota

Vrátí velikost v bajtech bloku přidělené paměti.

##  <a name="m_bownheap"></a>  CWin32Heap::m_bOwnHeap

Příznak, který používá k určení aktuální vlastnictví popisovač haldy, které jsou uložené v [m_hHeap](#m_hheap).

```
bool m_bOwnHeap;
```

##  <a name="m_hheap"></a>  CWin32Heap::m_hHeap

Popisovač objektu haldy.

```
HANDLE m_hHeap;
```

### <a name="remarks"></a>Poznámky

Proměnná se používá k ukládání popisovač pro objekt haldy.

##  <a name="reallocate"></a>  CWin32Heap::Reallocate

Znovu alokuje blok paměti z haldy objektu.

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Ukazatele na blok paměti, aby mohla znovu přidělit.

*nBytes*<br/>
Nová velikost v bajtech přiděleného bloku. Blok provádět větší nebo menší.

### <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na nově přidělenou paměť bloku.

### <a name="remarks"></a>Poznámky

Pokud *p* má hodnotu NULL, předpokládá se, že blok paměti dosud nebyl přidělen a [CWin32Heap::Allocate](#allocate) je volána s argumentem *nBytes*.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../../atl/atl-class-overview.md)<br/>
[IAtlMemMgr – třída](../../atl/reference/iatlmemmgr-class.md)<br/>
[CLocalHeap – třída](../../atl/reference/clocalheap-class.md)<br/>
[CGlobalHeap – třída](../../atl/reference/cglobalheap-class.md)<br/>
[CCRTHeap – třída](../../atl/reference/ccrtheap-class.md)<br/>
[CComHeap – třída](../../atl/reference/ccomheap-class.md)
