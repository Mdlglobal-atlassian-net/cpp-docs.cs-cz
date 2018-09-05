---
title: Cheapptrbase – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CHeapPtrBase
- ATLCORE/ATL::CHeapPtrBase
- ATLCORE/ATL::CHeapPtrBase::AllocateBytes
- ATLCORE/ATL::CHeapPtrBase::Attach
- ATLCORE/ATL::CHeapPtrBase::Detach
- ATLCORE/ATL::CHeapPtrBase::Free
- ATLCORE/ATL::CHeapPtrBase::ReallocateBytes
- ATLCORE/ATL::CHeapPtrBase::m_pData
dev_langs:
- C++
helpviewer_keywords:
- CHeapPtrBase class
ms.assetid: 501ac1b2-fb34-4c72-b7e6-a4f1fc8fda21
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 849e7ced8889cb46195946cca68243c37e1299a2
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43760120"
---
# <a name="cheapptrbase-class"></a>Cheapptrbase – třída

Tato třída je základem pro několik tříd haldy inteligentního ukazatele.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T, class Allocator = CCRTAllocator>  
class CHeapPtrBase
```

#### <a name="parameters"></a>Parametry

*T*  
Typ objektu ukládaly na haldě.

*Allocator –*  
Třída přidělení paměti pro použití. Ve výchozím nastavení se rutiny CRT používají k přidělují a uvolňují paměť.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Cheapptrbase –:: ~ cheapptrbase –](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CHeapPtrBase::AllocateBytes](#allocatebytes)|Volejte tuto metodu za účelem přidělení paměti.|
|[CHeapPtrBase::Attach](#attach)|Volejte tuto metodu za účelem převzít vlastnictví stávajícího ukazatele.|
|[CHeapPtrBase::Detach](#detach)|Volejte tuto metodu za účelem uvolní vlastnictví ukazatele.|
|[CHeapPtrBase::Free](#free)|Volejte tuto metodu za účelem odstranění objektu, na které odkazují `CHeapPtrBase`.|
|[CHeapPtrBase::ReallocateBytes](#reallocatebytes)|Voláním této metody lze znovu přidělit paměti.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CHeapPtrBase::operator T *](#operator_t_star)|Operátor přetypování.|
|[CHeapPtrBase::operator &](#operator_amp)|& – Operátor.|
|[CHeapPtrBase::operator ->](#operator_ptr)|Operátor pointer-to-member.|  

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CHeapPtrBase::m_pData](#m_pdata)|Členské proměnné ukazatele data.|

## <a name="remarks"></a>Poznámky

Tato třída je základem pro několik tříd haldy inteligentního ukazatele. Odvozené třídy, například [cheapptr –](../../atl/reference/cheapptr-class.md) a [ccomheapptr –](../../atl/reference/ccomheapptr-class.md), přidat svoje vlastní konstruktory a operátory. Zobrazit tyto třídy implementace příklady.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcore.h

##  <a name="allocatebytes"></a>  CHeapPtrBase::AllocateBytes

Volejte tuto metodu za účelem přidělení paměti.

```
bool AllocateBytes(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*nBytes*  
Počet bajtů paměti k přidělení.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud úspěšně je paměť přidělená, false jinak.

### <a name="remarks"></a>Poznámky

V sestavení pro ladění k selhání kontrolního výrazu dojde, pokud [CHeapPtrBase::m_pData](#m_pdata) členská proměnná aktuálně ukazuje na existující hodnotu; to znamená, že není rovna hodnotě NULL.

##  <a name="attach"></a>  CHeapPtrBase::Attach

Volejte tuto metodu za účelem převzít vlastnictví stávajícího ukazatele.

```
void Attach(T* pData) throw();
```

### <a name="parameters"></a>Parametry

*pData*  
`CHeapPtrBase` Objektu bude převzít vlastnictví tohoto ukazatele.

### <a name="remarks"></a>Poznámky

Když `CHeapPtrBase` objekt převezme vlastnictví ukazatele, automaticky odstraní ukazatel a jakékoli přiděleného objemu dat při dostane mimo rozsah.

V sestavení pro ladění k selhání kontrolního výrazu dojde, pokud [CHeapPtrBase::m_pData](#m_pdata) členská proměnná aktuálně ukazuje na existující hodnotu; to znamená, že není rovna hodnotě NULL.

##  <a name="dtor"></a>  Cheapptrbase –:: ~ cheapptrbase –

Destruktor.

```
~CHeapPtrBase() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky.

##  <a name="detach"></a>  CHeapPtrBase::Detach

Volejte tuto metodu za účelem uvolní vlastnictví ukazatele.

```
T* Detach() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí kopii ukazatele.

### <a name="remarks"></a>Poznámky

Uvolní vlastnictví ukazatele, nastaví [CHeapPtrBase::m_pData](#m_pdata) členskou proměnnou na hodnotu NULL a vrátí kopii ukazatele.

##  <a name="free"></a>  CHeapPtrBase::Free

Volejte tuto metodu za účelem odstranění objektu, na které odkazují `CHeapPtrBase`.

```
void Free() throw();
```

### <a name="remarks"></a>Poznámky

Objekt, který odkazuje `CHeapPtrBase` je uvolněn a [CHeapPtrBase::m_pData](#m_pdata) členská proměnná je nastavena na hodnotu NULL.

##  <a name="m_pdata"></a>  CHeapPtrBase::m_pData

Členské proměnné ukazatele data.

```
T* m_pData;
```

### <a name="remarks"></a>Poznámky

Tato členská proměnná uchovává informace o ukazatel.

##  <a name="operator_amp"></a>  CHeapPtrBase::operator &amp;

& – Operátor.

```
T** operator&() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí adresu objektu, na které odkazují `CHeapPtrBase` objektu.

##  <a name="operator_ptr"></a>  CHeapPtrBase::operator-&gt;

Operátor pointer-to-member.

```
T* operator->() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu [CHeapPtrBase::m_pData](#m_pdata) členské proměnné.

### <a name="remarks"></a>Poznámky

Operátor volání metody ve třídě, na které odkazují `CHeapPtrBase` objektu. V sestavení pro ladění k selhání kontrolního výrazu dojde, pokud `CHeapPtrBase` odkazuje na hodnotu NULL.

##  <a name="operator_t_star"></a>  CHeapPtrBase::operator T *

Operátor přetypování.

```  
operator T*() const throw();
```

### <a name="remarks"></a>Poznámky

Vrátí [CHeapPtrBase::m_pData](#m_pdata).

##  <a name="reallocatebytes"></a>  CHeapPtrBase::ReallocateBytes

Voláním této metody lze znovu přidělit paměti.

```
bool ReallocateBytes(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*nBytes*  
Nové množství paměti k přidělení v bajtech.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud úspěšně je paměť přidělená, false jinak.

## <a name="see-also"></a>Viz také

[Cheapptr – třída](../../atl/reference/cheapptr-class.md)   
[Ccomheapptr – třída](../../atl/reference/ccomheapptr-class.md)   
[Přehled tříd](../../atl/atl-class-overview.md)
