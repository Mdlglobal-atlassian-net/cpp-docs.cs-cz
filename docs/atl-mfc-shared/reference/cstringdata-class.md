---
title: Cstringdata – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CStringData
- ATLSIMPSTR/ATL::CStringData
- ATLSIMPSTR/ATL::AddRef
- ATLSIMPSTR/ATL::data
- ATLSIMPSTR/ATL::IsLocked
- ATLSIMPSTR/ATL::IsShared
- ATLSIMPSTR/ATL::Lock
- ATLSIMPSTR/ATL::Release
- ATLSIMPSTR/ATL::Unlock
- ATLSIMPSTR/ATL::nAllocLength
- ATLSIMPSTR/ATL::nDataLength
- ATLSIMPSTR/ATL::nRefs
- ATLSIMPSTR/ATL::pStringMgr
dev_langs:
- C++
helpviewer_keywords:
- CStringData class
- shared classes, CStringData
ms.assetid: 4e31b5ca-3dbe-4fd5-b692-8211fbfb2593
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: effc4166fa25cec03ea62a5dd35a5396d2d2a3f2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419786"
---
# <a name="cstringdata-class"></a>Cstringdata – třída

Tato třída reprezentuje data objektu string.

## <a name="syntax"></a>Syntaxe

```
struct CStringData
```

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[AddRef](#addref)|Zvýší počet odkazů na objekt řetězce data.|
|[data](#data)|Načte znaková data objektu string.|
|[Uzamčeno](#islocked)|Určuje, pokud je vyrovnávací paměti s přidruženými řetězcovými objekt uzamčen.|
|[IsShared](#isshared)|Určuje, pokud vyrovnávací paměť objektu přidruženými řetězcovými se momentálně sdílí.|
|[Zámek](#lock)|Zamkne vyrovnávací paměti s přidruženými řetězcovými objektu.|
|[Vydaná verze](#release)|Uvolní objekt zadaného řetězce.|
|[Odemknutí](#unlock)|Odemkne vyrovnávací paměti s přidruženými řetězcovými objektu.|

### <a name="data-members"></a>Datové členy

|||
|-|-|
|[nAllocLength](#nalloclength)|Délka přiděleného objemu dat v `XCHAR`s (bez ukončujícího znaku null)|
|[nDataLength](#ndatalength)|Délka aktuálně používaných dat v `XCHAR`s (bez ukončujícího znaku null)|
|[nRefs](#nrefs)|Aktuální počet odkazů objektu.|
|[pStringMgr](#pstringmgr)|Ukazatel na řetězec správce tohoto objektu řetězce.|

## <a name="remarks"></a>Poznámky

Tato třída by měla sloužit pouze implementace vlastního řetězce vedoucí vývojáři. Další informace o Správci vlastního řetězce, naleznete v tématu [Správa paměti a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)

Tato třída zapouzdří různých typů informací a data související s vyšší objektu řetězce, jako například [CStringT](../../atl-mfc-shared/reference/cstringt-class.md), [csimplestringt –](../../atl-mfc-shared/reference/csimplestringt-class.md), nebo [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md) objekty. Každý objekt vyšší řetězec obsahuje ukazatel na jeho přidruženého `CStringData` objektu povoluje více řetězcových objektů tak, aby odkazoval na stejný datový objekt řetězce. Tento vztah je reprezentována počet odkazů (`nRefs`) z `CStringData` objektu.

> [!NOTE]
>  V některých případech, typu řetězec (například `CFixedString`) nebude sdílet data objektu řetězce s více než jeden objekt vyšší řetězec. Další informace najdete v části [Správa paměti a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

Tato data tvoří:

- Správce paměti (typu [iatlstringmgr –](../../atl-mfc-shared/reference/iatlstringmgr-class.md)) řetězce.

- Aktuální délka ( [nDataLength](#ndatalength)) řetězce.

- Přidělené délka ( [nAllocLength](#nalloclength)) řetězce. Z důvodů výkonu může se lišit od aktuální délka řetězce

- Aktuální počet odkazů ( [nRefs](#nrefs)) z `CStringData` objektu. Tato hodnota se používá při určování, kolik řetězcových objektů sdílejí stejné `CStringData` objektu.

- Vyrovnávací paměti pro skutečné znaky ( [data](#data)) řetězce.

   > [!NOTE]
   > Vyrovnávací paměti pro skutečné znaky z objektu string je přidělen správcem řetězec a připojí se k němu `CStringData` objektu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsimpstr.h

##  <a name="addref"></a>  CStringData::AddRef

Zvýší počet odkazů na objekt řetězce.

```
void AddRef() throw();
```

### <a name="remarks"></a>Poznámky

Zvýší počet odkazů na objekt řetězce.

> [!NOTE]
>  Tato metoda není volána na řetězec s počet odkazů záporná, protože záporný počet indikuje, že vyrovnávací paměti pro řetězec je uzamčen.

##  <a name="data"></a>  CStringData::data

Vrací ukazatel na znak vyrovnávací paměti objektu string.

```
void* data() throw();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na znak vyrovnávací paměti objektu typu string.

### <a name="remarks"></a>Poznámky

Voláním této funkce vrátí aktuální znak vyrovnávací paměť na objekt přidružený řetězce.

> [!NOTE]
>  Není tuto vyrovnávací paměť přidělaná `CStringData` objektu, ale správce řetězců v případě potřeby. Při přidělování, vyrovnávací paměti je připojen datový objekt řetězce.

##  <a name="islocked"></a>  CStringData::IsLocked

Určuje, pokud je uzamčen vyrovnávací paměti pro znaky.

```
bool IsLocked() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je uzamčen vyrovnávací paměti; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Voláním této funkce k určení, pokud je aktuálně uzamčen vyrovnávací paměti pro znaky z objektu typu string.

##  <a name="isshared"></a>  CStringData::IsShared

Určuje, zda je sdílená vyrovnávací paměti pro znaky.

```
bool IsShared() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je sdílené vyrovnávací paměti; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Voláním této funkce k určení, pokud vyrovnávací paměti pro znaky řetězce datového objektu se momentálně sdílí mezi více řetězcových objektů.

##  <a name="lock"></a>  CStringData::Lock

Zamkne vyrovnávací paměti pro znaky přidruženými řetězcovými objektu.

```
void Lock() throw();
```

### <a name="remarks"></a>Poznámky

Voláním této funkce k uzamčení vyrovnávací paměti pro znaky řetězce datového objektu. Zamknutí a odemknutí se používá při vývojář vyžadují přímý přístup k vyrovnávací paměti pro znaky. Dobrým příkladem uzamčení prokazuje [LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) a [UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) metody `CSimpleStringT`.

> [!NOTE]
>  Vyrovnávací paměti pro znaky lze uzamknout, pouze pokud vyrovnávací paměť není sdílen vyšší řetězcových objektů.

##  <a name="nalloclength"></a>  CStringData::nAllocLength

Délka vyrovnávací paměti přidělené znak.

```
int nAllocLength;
```

### <a name="remarks"></a>Poznámky

Ukládá délku vyrovnávací paměti přiděleného objemu dat v `XCHAR`s (bez ukončujícího znaku null).

##  <a name="ndatalength"></a>  CStringData::nDataLength

Aktuální délka na objekt řetězce.

```
int nDataLength;
```

### <a name="remarks"></a>Poznámky

Ukládá délku aktuálně používaných dat v `XCHAR`s (bez ukončujícího znaku null).

##  <a name="nrefs"></a>  CStringData::nRefs

Počet odkazů řetězec datového objektu.

```
long nRefs;
```

### <a name="remarks"></a>Poznámky

Ukládá počet odkazů na objekt řetězce data. Tento počet označuje počet vyšší řetězcových objektů, které jsou spojeny s datový objekt řetězec. Záporná hodnota označuje, že je aktuálně uzamčena na objekt řetězce data.

##  <a name="pstringmgr"></a>  CStringData::pStringMgr

Správce paměti přidruženými řetězcovými objektu.

```
IAtlStringMgr* pStringMgr;
```

### <a name="remarks"></a>Poznámky

Ukládá správce paměti pro objekt přidruženými řetězcovými. Další informace o nástroje pro správu paměti a řetězce, naleznete v tématu [Správa paměti a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

##  <a name="release"></a>  CStringData::Release

Sníží počet referenční řetězce datového objektu.

```
void Release() throw();
```

### <a name="remarks"></a>Poznámky

Voláním této funkce snížen počet odkazů uvolnění `CStringData` struktury, pokud narazí na počet odkazů nuly. To se obvykle provádí při objektu řetězce se odstraní a proto již musí odkazovat na objekt řetězce data.

Například následující kód by volat `CStringData::Release` datový objekt řetězec přidružené `str1`:

[!code-cpp[NVC_ATLMFC_Utilities#104](../../atl-mfc-shared/codesnippet/cpp/cstringdata-class_1.cpp)]

##  <a name="unlock"></a>  CStringData::Unlock

Odemkne vyrovnávací paměti pro znaky přidruženými řetězcovými objektu.

```
void Unlock() throw();
```

### <a name="remarks"></a>Poznámky

Voláním této funkce k odemknutí vyrovnávací paměti pro znaky řetězce datového objektu. Po odemknutí vyrovnávací paměť je ke sdílení a může být odkaz počítají.

> [!NOTE]
>  Každé volání `Lock` musí odpovídat příslušnému volání `Unlock`.

Zamknutí a odemknutí se používá, když vývojář musí zajistit, že nebudou sdílet data řetězce. Dobrým příkladem uzamčení prokazuje [LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) a [UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) metody `CSimpleStringT`.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Sdílené třídy ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)

