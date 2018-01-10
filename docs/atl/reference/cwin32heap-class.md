---
title: "Třída CWin32Heap | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
helpviewer_keywords: CWin32Heap class
ms.assetid: 69176022-ed98-4e3b-96d8-116b0c58ac95
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 67856242c63639101185eb6f6dcfd4902f0ef48c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cwin32heap-class"></a>CWin32Heap – třída
Tato třída implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) pomocí funkce přidělení haldy Win32.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CWin32Heap : public IAtlMemMgr
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CWin32Heap::CWin32Heap](#cwin32heap)|Konstruktor|  
|[CWin32Heap:: ~ CWin32Heap](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CWin32Heap::Allocate](#allocate)|Blok paměti přidělí z objektu haldy.|  
|[CWin32Heap::Attach](#attach)|Připojí objektu haldy existující haldě.|  
|[CWin32Heap::Detach](#detach)|Umožňuje odpojit objektu haldy z existující haldy.|  
|[CWin32Heap::Free](#free)|Uvolní dříve přidělené z halda paměti.|  
|[CWin32Heap::GetSize](#getsize)|Vrátí velikost bloku paměti přidělené z objektu haldy.|  
|[CWin32Heap::Reallocate](#reallocate)|Blok paměti přidělí z objektu haldy.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CWin32Heap::m_bOwnHeap](#m_bownheap)|Příznak, který se používá k určení aktuální vlastnictví haldy popisovače.|  
|[CWin32Heap::m_hHeap](#m_hheap)|Popisovač objektu haldy.|  
  
## <a name="remarks"></a>Poznámky  
 `CWin32Heap`implementuje metody přidělení paměti pomocí funkce přidělení haldy Win32 včetně [HeapAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366597) a [HeapFree](http://msdn.microsoft.com/library/windows/desktop/aa366701). Na rozdíl od jiných třídy haldy `CWin32Heap` vyžaduje platný haldy popisovač poskytované předtím, než se přidělí paměť: jiné třídy výchozí k používání haldy procesu. Popisovač můžete zadat konstruktoru nebo na [CWin32Heap::Attach](#attach) metoda. Najdete v článku [CWin32Heap::CWin32Heap](#cwin32heap) metoda další podrobnosti.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IAtlMemMgr`  
  
 `CWin32Heap`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlmem.h  
  
##  <a name="allocate"></a>CWin32Heap::Allocate  
 Blok paměti přidělí z objektu haldy.  
  
```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nBytes`  
 Požadovaný počet bajtů v nového bloku paměti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na nově přidělených paměti bloku.  
  
### <a name="remarks"></a>Poznámky  
 Volání [CWin32Heap::Free](#free) nebo [CWin32Heap::Reallocate](#reallocate) k bezplatným je paměť přidělená touto metodou.  
  
 Implementovaná pomocí [HeapAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366597).  
  
##  <a name="attach"></a>CWin32Heap::Attach  
 Připojí objektu haldy existující haldě.  
  
```
void Attach(HANDLE hHeap, bool bTakeOwnership) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `hHeap`  
 Popisovač existující haldy.  
  
 `bTakeOwnership`  
 Příznak naznačuje v případě `CWin32Heap` objektu je převzít vlastnictví prostředků haldě.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `bTakeOwnership` má hodnotu TRUE, `CWin32Heap` objektu je zodpovědná za zpracování haldy odstranění.  
  
##  <a name="cwin32heap"></a>CWin32Heap::CWin32Heap  
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
 `hHeap`  
 Existující objekt haldy  
  
 `dwFlags`  
 Příznaky použité při vytváření haldy  
  
 *nInitialSize*  
 Počáteční velikost haldy  
  
 `nMaxSize`  
 Maximální velikost haldy  
  
### <a name="remarks"></a>Poznámky  
 Před přidělování paměti, je potřeba zadat `CWin32Heap` objektu s popisovačem haldy platný. Nejsnáze toho dosáhnete pomocí haldy procesu:  
  
 [!code-cpp[NVC_ATL_Utilities#92](../../atl/codesnippet/cpp/cwin32heap-class_1.cpp)]  
  
 Je také možné zadat do konstruktoru existující popisovač haldy; v tomto případě nový objekt nepřevezme vlastnictví haldy. Původní popisovač haldy pořád bude platit při `CWin32Heap` je odstraněn objekt.  
  
 Existující haldy lze také připojit k novému objektu pomocí [CWin32Heap::Attach](#attach).  
  
 Pokud se halda vyžaduje tam, kde se všechny operace provádějí z jednoho vlákna, je nejlepší vytvořit tento objekt takto:  
  
 [!code-cpp[NVC_ATL_Utilities#93](../../atl/codesnippet/cpp/cwin32heap-class_2.cpp)]  
  
 Parametr **HEAP_NO_SERIALIZE** Určuje, že vzájemné vyloučení nebude používat při funkce hald přidělit a volné paměti, podle zvýšení výkonu.  
  
 Třetí parametr má výchozí hodnotu 0, což umožňuje, aby halda narůstala podle potřeby. V tématu [HeapCreate](http://msdn.microsoft.com/library/windows/desktop/aa366599\(v=vs.85\).aspx) vysvětlení velikostí paměti a značky.  
  
##  <a name="dtor"></a>CWin32Heap:: ~ CWin32Heap  
 Destruktor.  
  
```
~CWin32Heap() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Zničí haldy popisovač, pokud `CWin32Heap` objekt má vlastnictví haldě.  
  
##  <a name="detach"></a>CWin32Heap::Detach  
 Umožňuje odpojit objektu haldy z existující haldy.  
  
```
HANDLE Detach() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí popisovač haldě, do které byl objekt dříve připojit.  
  
##  <a name="free"></a>CWin32Heap::Free  
 Uvolní paměť z haldy podle dříve přidělená [CWin32Heap::Allocate](#allocate) nebo [CWin32Heap::Reallocate](#reallocate).  
  
```
virtual void Free(void* p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Ukazatel na oblast paměti uvolnit. NULL není platná hodnota a neprovede žádnou akci.  
  
##  <a name="getsize"></a>CWin32Heap::GetSize  
 Vrátí velikost bloku paměti přidělené z objektu haldy.  
  
```
virtual size_t GetSize(void* p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Ukazatel na oblast paměti, jejíž aktuální velikost metodu obdrží. Toto je ukazatel vrácený [CWin32Heap::Allocate](#allocate) nebo [CWin32Heap::Reallocate](#reallocate).  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí velikost v bajtech přidělenou paměť bloku.  
  
##  <a name="m_bownheap"></a>CWin32Heap::m_bOwnHeap  
 Příznak používá k určení aktuální vlastnictví zpracování haldy uložené v [m_hHeap](#m_hheap).  
  
```
bool m_bOwnHeap;
```  
  
##  <a name="m_hheap"></a>CWin32Heap::m_hHeap  
 Popisovač objektu haldy.  
  
```
HANDLE m_hHeap;
```  
  
### <a name="remarks"></a>Poznámky  
 Proměnná se používá k ukládání popisovač pro objektu haldy.  
  
##  <a name="reallocate"></a>CWin32Heap::Reallocate  
 Blok paměti přidělí z objektu haldy.  
  
```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Ukazatel na oblast paměti a znovu přidělte.  
  
 `nBytes`  
 Novou velikost v bajtech přidělené bloku. Blok můžete provedeny, větší nebo menší.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na nově přidělených paměti bloku.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `p` má hodnotu NULL, se předpokládá, že bloku paměti dosud nebyl přidělen a [CWin32Heap::Allocate](#allocate) je volána s argumentem z `nBytes`.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [IAtlMemMgr – třída](../../atl/reference/iatlmemmgr-class.md)   
 [CLocalHeap – třída](../../atl/reference/clocalheap-class.md)   
 [CGlobalHeap – třída](../../atl/reference/cglobalheap-class.md)   
 [CCRTHeap – třída](../../atl/reference/ccrtheap-class.md)   
 [CComHeap – třída](../../atl/reference/ccomheap-class.md)
