---
title: CFixedStringT – třída
ms.date: 03/27/2019
f1_keywords:
- CFixedStringT
- CSTRINGT/ATL::CFixedStringT
- CSTRINGT/ATL::CFixedStringT::CFixedStringT
helpviewer_keywords:
- CFixedStringT class
- shared classes, CFixedStringT
ms.assetid: 6d4171ba-3104-493a-a6cc-d515f4ba9a4b
ms.openlocfilehash: fe096185f6f0b71ad45757cd0b75ab13c41e5f5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317829"
---
# <a name="cfixedstringt-class"></a>CFixedStringT – třída

Tato třída představuje objekt řetězce s pevnou vyrovnávací pamětí znaků.

## <a name="syntax"></a>Syntaxe

```
template<class StringType, int t_nChars>
class CFixedStringT : private CFixedStringMgr, public StringType
```

#### <a name="parameters"></a>Parametry

*Typ řetězce*<br/>
Používá se jako základní třída pro objekt `CStringT`s pevným řetězcem a může být libovolný typ založený na. Některé příklady `CString` `CStringA`zahrnují `CStringW`, , a .

*t_nChars*<br/>
Počet znaků uložených ve vyrovnávací paměti.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[cfixedstringt::cfixedstringt](#cfixedstringt)|Konstruktor pro objekt řetězce.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CFixedStringT::operátor =](#operator_eq)|Přiřadí objektu novou `CFixedStringT` hodnotu.|

## <a name="remarks"></a>Poznámky

Tato třída je příkladem vlastní třídy `CStringT`řetězce založené na . Ačkoli podobné, dvě třídy se liší v implementaci. Hlavní rozdíly mezi `CFixedStringT` `CStringT` a jsou:

- Počáteční znak vyrovnávací paměti je přidělena jako součást objektu a má velikost *t_nChars*. To umožňuje `CFixedString` objektobsadit souvislé paměti bloku pro účely výkonu. Pokud však obsah `CFixedStringT` objektu zvětšuje nad *rámec t_nChars*, vyrovnávací paměť je přidělena dynamicky.

- Vyrovnávací paměť znaků `CFixedStringT` pro objekt má vždy stejnou délku ( *t_nChars*). Neexistuje žádné omezení velikosti `CStringT` vyrovnávací paměti pro objekty.

- Správce paměti `CFixedStringT` pro je přizpůsoben tak, že sdílení [cstringdata](../../atl-mfc-shared/reference/cstringdata-class.md) objektu mezi dvěma nebo více `CFixedStringT` objekty není povoleno. `CStringT`objekty nemají toto omezení.

Další informace o přizpůsobení `CFixedStringT` a správě paměti pro objekty řetězce obecně naleznete v [tématu Správa paměti a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IAtlStringMgr`

`StringType`

`CFixedStringMgr`

`CFixedStringT`

## <a name="requirements"></a>Požadavky

**Záhlaví:** cstringt.h

## <a name="cfixedstringtcfixedstringt"></a><a name="cfixedstringt"></a>cfixedstringt::cfixedstringt

Vytvoří `CFixedStringT` objekt.

```
CFixedStringT() throw();
explicit CFixedStringT(IAtlStringMgr* pStringMgr) throw();
CFixedStringT(const CFixedStringT<StringType, t_nChars>& strSrc);
CFixedStringT(const StringType& strSrc);
CFixedStringT(const StringType::XCHAR* pszSrc);
explicit CFixedStringT(const StringType::YCHAR* pszSrc);
explicit CFixedStringT(const unsigned char* pszSrc);
```

### <a name="parameters"></a>Parametry

*pszSrc*<br/>
Řetězec s ukončeným hodnotou null, `CFixedStringT` který má být zkopírován do tohoto objektu.

*strSrc*<br/>
Existující `CFixedStringT` objekt, který má `CFixedStringT` být do tohoto objektu zkopírován.

*pStringMgr*<br/>
Ukazatel na správce paměti `CFixedStringT` objektu. Další informace `IAtlStringMgr` o správě `CFixedStringT`paměti a pro správu paměti naleznete v [tématu Správa paměti a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

### <a name="remarks"></a>Poznámky

Vzhledem k tomu, že konstruktory zkopírují vstupní data do nového přidělenéúložiště, měli byste si být vědomi, že mohou mít způsobit výjimky paměti. Některé z těchto konstruktorů fungují jako funkce převodu.

## <a name="cfixedstringtoperator-"></a><a name="operator_eq"></a>CFixedStringT::operátor =

Znovu inicializuje `CFixedStringT` existující objekt s novými daty.

```
CFixedStringT<StringType, t_nChars>& operator=(
    const CFixedStringT<StringType, t_nChars>& strSrc);
CFixedStringT<StringType, t_nChars>& operator=(const char* pszSrc);
CFixedStringT<StringType, t_nChars>& operator=(const wchar_t* pszSrc);
CFixedStringT<StringType, t_nChars>& operator=(const unsigned char* pszSrc);
CFixedStringT<StringType, t_nChars>& operator=(const StringType& strSrc);
```

### <a name="parameters"></a>Parametry

*pszSrc*<br/>
Řetězec s ukončeným hodnotou null, `CFixedStringT` který má být zkopírován do tohoto objektu.

*strSrc*<br/>
Existující `CFixedStringT` chcete-li zkopírovat `CFixedStringT` do tohoto objektu.

### <a name="remarks"></a>Poznámky

Měli byste si být vědomi toho, že k výjimkám paměti může dojít při `CFixedStringT` každém použití operátoru přiřazení, protože nové úložiště je často přiděleno pro uložení výsledného objektu.

## <a name="see-also"></a>Viz také

[CStringT – třída](../../atl-mfc-shared/reference/cstringt-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Sdílené třídy KNIHOVNY ATL/Knihovny MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
