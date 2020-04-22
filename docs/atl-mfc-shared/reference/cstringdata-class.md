---
title: CStringData – třída
ms.date: 11/04/2016
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
helpviewer_keywords:
- CStringData class
- shared classes, CStringData
ms.assetid: 4e31b5ca-3dbe-4fd5-b692-8211fbfb2593
ms.openlocfilehash: f14f1d9c269f06099bd224f582de1f55da33ff0f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746835"
---
# <a name="cstringdata-class"></a>CStringData – třída

Tato třída představuje data objektu řetězce.

## <a name="syntax"></a>Syntaxe

```
struct CStringData
```

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Přidatref](#addref)|Zintáží počet odkazů datového objektu řetězce.|
|[Dat](#data)|Načte data znaků objektu řetězce.|
|[Islocked](#islocked)|Určuje, zda je uzamčena vyrovnávací paměť přidruženého objektu řetězce.|
|[IsShared](#isshared)|Určuje, zda je vyrovnávací paměť přidruženého objektu řetězce aktuálně sdílena.|
|[Zámek](#lock)|Zamkne vyrovnávací paměť přidruženého objektu řetězce.|
|[Vydat](#release)|Uvolní zadaný objekt řetězce.|
|[Odemknout](#unlock)|Odemkne vyrovnávací paměť přidruženého objektu řetězce.|

### <a name="data-members"></a>Členové dat

|||
|-|-|
|[nDélka alloc](#nalloclength)|Délka přidělených dat `XCHAR`v s (bez ukončování null)|
|[nDélka dat](#ndatalength)|Délka aktuálně používaných `XCHAR`dat v s (bez ukončování null)|
|[nRefs](#nrefs)|Aktuální počet odkazů objektu.|
|[pStringMgr](#pstringmgr)|Ukazatel na správce řetězce tohoto objektu řetězce.|

## <a name="remarks"></a>Poznámky

Tato třída by měla být používána pouze vývojáři, kteří implementují vlastní správce řetězců. Další informace o vlastních správce řetězců naleznete v [tématu Memory Management a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)

Tato třída zapouzdřuje různé typy informací a dat spojených s objektem s vyšším řetězcem, například [CStringT](../../atl-mfc-shared/reference/cstringt-class.md), [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)nebo [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md) objekty. Každý vyšší objekt řetězce obsahuje `CStringData` ukazatel na přidružený objekt, což umožňuje více objektům řetězce přejděte na stejný datový objekt řetězce. Tento vztah je reprezentován`nRefs`počtem odkazů `CStringData` ( ) objektu.

> [!NOTE]
> V některých případech typ řetězce `CFixedString`(například ) nebude sdílet datový objekt řetězce s více než jedním vyšším objektem řetězce. Další informace naleznete v [tématu Memory Management a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

Tyto údaje se skládají z:

- Správce paměti (typu [IAtlStringMgr)](../../atl-mfc-shared/reference/iatlstringmgr-class.md)řetězce.

- Aktuální délka ( [nDataLength](#ndatalength)) řetězce.

- Přidělená délka ( [nAllocLength](#nalloclength)) řetězce. Z důvodů výkonu se to může lišit od aktuální délky řetězce.

- Aktuální počet odkazů ( [nRefs](#nrefs)) objektu. `CStringData` Tato hodnota se používá při určování, kolik `CStringData` objektů řetězce sdílejí stejný objekt.

- Skutečná znaková vyrovnávací paměť ( [data](#data)) řetězce.

   > [!NOTE]
   > Skutečná vyrovnávací paměť znaků objektu řetězce je přidělena správcem `CStringData` řetězce a je připojena k objektu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsimpstr.h

## <a name="cstringdataaddref"></a><a name="addref"></a>CStringData::Addref

Zintáží počet odkazů objektu řetězce.

```cpp
void AddRef() throw();
```

### <a name="remarks"></a>Poznámky

Zintáží počet odkazů objektu řetězce.

> [!NOTE]
> Nevolejte tuto metodu na řetězec s negativním počtem odkazů, protože záporný počet označuje, že vyrovnávací paměť řetězce je uzamčena.

## <a name="cstringdatadata"></a><a name="data"></a>CStringData::data

Vrátí ukazatel na znakovou vyrovnávací paměť objektu řetězce.

```cpp
void* data() throw();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na znak vyrovnávací paměti objektu řetězce.

### <a name="remarks"></a>Poznámky

Volání této funkce vrátí aktuální znak vyrovnávací paměti přidruženého objektu řetězce.

> [!NOTE]
> Tato vyrovnávací paměť není `CStringData` přidělena objektem, ale správcem řetězců v případě potřeby. Při přidělení je vyrovnávací paměť připojena k datovému objektu řetězce.

## <a name="cstringdataislocked"></a><a name="islocked"></a>CStringData::Uzamčeno

Určuje, zda je vyrovnávací paměť znaků uzamčena.

```
bool IsLocked() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je vyrovnávací paměť uzamčena. jinak FALSE.

### <a name="remarks"></a>Poznámky

Volání této funkce k určení, pokud je aktuálně uzamčenznakové vyrovnávací paměti objektu řetězce.

## <a name="cstringdataisshared"></a><a name="isshared"></a>CStringData::IsShared

Určuje, zda je sdílena vyrovnávací paměť znaků.

```
bool IsShared() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je vyrovnávací paměť sdílena. jinak FALSE.

### <a name="remarks"></a>Poznámky

Volání této funkce k určení, pokud znak vyrovnávací paměti datového objektu řetězce je aktuálně sdílena mezi více objektů řetězce.

## <a name="cstringdatalock"></a><a name="lock"></a>CStringData::Zamknout

Zamkne vyrovnávací paměť znaků přidruženého objektu řetězce.

```cpp
void Lock() throw();
```

### <a name="remarks"></a>Poznámky

Volání této funkce uzamkněte vyrovnávací paměť znaků datového objektu řetězce. Zamykání a odemykání se používá v případě, že vývojář vyžaduje přímý přístup k vyrovnávací paměti znaků. Dobrým příkladem uzamčení je prokázáno [LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) a `CSimpleStringT` [UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) metody .

> [!NOTE]
> Vyrovnávací paměť znaků lze uzamknout pouze v případě, že vyrovnávací paměť není sdílena mezi objekty s vyšším řetězcem.

## <a name="cstringdatanalloclength"></a><a name="nalloclength"></a>CStringData::nDélka celého těla

Délka přidělené vyrovnávací paměti znaků.

```
int nAllocLength;
```

### <a name="remarks"></a>Poznámky

Ukládá délku přidělené vyrovnávací `XCHAR`paměti dat v s (bez ukončení null).

## <a name="cstringdatandatalength"></a><a name="ndatalength"></a>CStringData::nDataLength

Aktuální délka objektu řetězce.

```
int nDataLength;
```

### <a name="remarks"></a>Poznámky

Ukládá délku aktuálně používaných `XCHAR`dat v s (bez ukončení null).

## <a name="cstringdatanrefs"></a><a name="nrefs"></a>CStringData::nRefs

Počet odkazů na datový objekt řetězce.

```
long nRefs;
```

### <a name="remarks"></a>Poznámky

Ukládá počet odkazů datového objektu řetězce. Tento počet označuje počet vyšší chod objektů, které jsou přidruženy k datovému objektu řetězce. Záporná hodnota označuje, že datový objekt řetězce je aktuálně uzamčen.

## <a name="cstringdatapstringmgr"></a><a name="pstringmgr"></a>CStringData::pStringMgr

Správce paměti přidruženého objektu řetězce.

```
IAtlStringMgr* pStringMgr;
```

### <a name="remarks"></a>Poznámky

Uloží správce paměti pro přidružený objekt řetězce. Další informace o správci paměti a řetězce naleznete v [tématu Správa paměti a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="cstringdatarelease"></a><a name="release"></a>CStringData::Uvolnění

Sníží počet odkazů na datový objekt řetězce.

```cpp
void Release() throw();
```

### <a name="remarks"></a>Poznámky

Volání této funkce snížení počtu odkazů, uvolnění `CStringData` struktury, pokud počet odkazů hity nula. To se běžně provádí při odstranění objektu řetězce, a proto již není třeba odkazovat na datový objekt řetězce.

Například následující kód by `CStringData::Release` volání pro datový `str1`objekt řetězce spojené s :

[!code-cpp[NVC_ATLMFC_Utilities#104](../../atl-mfc-shared/codesnippet/cpp/cstringdata-class_1.cpp)]

## <a name="cstringdataunlock"></a><a name="unlock"></a>CStringData::Odemknout

Odemkne vyrovnávací paměť znaků přidruženého objektu řetězce.

```cpp
void Unlock() throw();
```

### <a name="remarks"></a>Poznámky

Volání této funkce odemknout znak vyrovnávací paměti datového objektu řetězce. Jakmile je vyrovnávací paměť odemčena, je sdíletelná a lze ji počítat s odkazem.

> [!NOTE]
> Každé volání `Lock` musí být porovnáno odpovídajícím `Unlock`voláním .

Zamykání a odemykání se používá, když vývojář musí zajistit, že data řetězce nejsou sdílena. Dobrým příkladem uzamčení je prokázáno [LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) a `CSimpleStringT` [UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) metody .

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Sdílené třídy KNIHOVNY ATL/Knihovny MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
