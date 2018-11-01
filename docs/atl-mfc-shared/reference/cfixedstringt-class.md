---
title: Cfixedstringt – třída
ms.date: 11/04/2016
f1_keywords:
- CFixedStringT
- CSTRINGT/ATL::CFixedStringT
- CSTRINGT/ATL::CFixedStringT::CFixedStringT
helpviewer_keywords:
- CFixedStringT class
- shared classes, CFixedStringT
ms.assetid: 6d4171ba-3104-493a-a6cc-d515f4ba9a4b
ms.openlocfilehash: 25556b45f93898acbb8b8b4f9263231b5b3ce2e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473785"
---
# <a name="cfixedstringt-class"></a>Cfixedstringt – třída

Tato třída reprezentuje objekt řetězce s pevnou znak vyrovnávací paměti.

## <a name="syntax"></a>Syntaxe

```
template<class StringType, int t_nChars>
class CFixedStringT : private CFixedStringMgr, public StringType
```

#### <a name="parameters"></a>Parametry

*StringType*<br/>
Použít jako základní třídu pro řetězec pevné délky objekt a může být kterýkoli `CStringT`– na základě typu. Mezi příklady patří `CString`, `CStringA`, a `CStringW`.

*t_nChars*<br/>
Počet znaků, které jsou uloženy ve vyrovnávací paměti.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CFixedStringT::CFixedStringT](#cfixedstringt)|Konstruktor pro objekt řetězce.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CFixedStringT::operator =](#eq)|Přiřadí novou hodnotu `CFixedStringT` objektu.|

## <a name="remarks"></a>Poznámky

Tato třída je příkladem třídu vlastního řetězce na základě `CStringT`. I když je velmi podobné, se liší v implementaci dvou tříd. Hlavní rozdíly mezi `CFixedStringT` a `CStringT` jsou:

- Počáteční znak vyrovnávací paměti přidělené jako součást objektu a má velikost *t_nChars*. Díky tomu `CFixedString` objektu tak, aby obsadily blok souvislé paměti z důvodů výkonu. Ale pokud obsah `CFixedStringT` objekt překročí *t_nChars*, je dynamicky přidělené vyrovnávací paměti.

- Vyrovnávací paměti pro znaky pro `CFixedStringT` objektu je vždy stejnou délku ( *t_nChars*). Neexistuje žádné omezení velikosti vyrovnávací paměti pro `CStringT` objekty.

- Správce paměti pro `CFixedStringT` upravíte tak, že sdílení [cstringdata –](../../atl-mfc-shared/reference/cstringdata-class.md) objektu mezi dvěma nebo více `CFixedStringT` objectsis není povolený. `CStringT` objekty není nutné toto omezení.

Další informace o přizpůsobení sady `CFixedStringT` a správa paměti pro řetězec objektů naleznete v tématu [Správa paměti a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IAtlStringMgr`

`StringType`

`CFixedStringMgr`

`CFixedStringT`

## <a name="requirements"></a>Požadavky

**Záhlaví:** cstringt.h

##  <a name="cfixedstringt"></a>  CFixedStringT::CFixedStringT

Vytvoří `CFixedStringT` objektu.

```
CFixedStringT() throw();
explicit CFixedStringT(IAtlStringMgr* pStringMgr) throw();
CFixedStringT(const CFixedStringT<StringType, t_nChars>& str);
CFixedStringT(const StringType& str);
CFixedStringT(const StringType::XCHAR* psz);
explicit CFixedStringT(const StringType::YCHAR* psz);
explicit CFixedStringT(const unsigned char* psz);
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Řetězec zakončený hodnotou null ke zkopírování do tohoto `CFixedStringT` objektu.

*str*<br/>
Existující `CFixedStringT` objektu, které se mají zkopírovat do tohoto `CFixedStringT` objektu.

*pStringMgr*<br/>
Ukazatel na správce paměti `CFixedStringT` objektu. Další informace o `IAtlStringMgr` a správa paměti pro `CFixedStringT`, naleznete v tématu [Správa paměti a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

### <a name="remarks"></a>Poznámky

Protože se konstruktory kopírují do nového úložiště přidělené vstupních dat, je třeba si uvědomit, tato paměť, může způsobit výjimky. Všimněte si, že některé z těchto konstruktorů fungovat jako funkce pro převod.

##  <a name="operator__eq"></a>  CFixedStringT::operator =

Znovu inicializuje existující `CFixedStringT` objektu s novými daty.

```
CFixedStringT<StringType, t_nChars>& operator=(
    const CFixedStringT<StringType, t_nChars>& str);
CFixedStringT<StringType, t_nChars>& operator=(const char* psz);
CFixedStringT<StringType, t_nChars>& operator=(const wchar_t* psz);
CFixedStringT<StringType, t_nChars>& operator=(const unsigned char* psz);
CFixedStringT<StringType, t_nChars>& operator=(const StringType& str);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Řetězec zakončený hodnotou null ke zkopírování do tohoto `CFixedStringT` objektu.

*psz*<br/>
Existující `CFixedStringT` ke zkopírování do tohoto `CFixedStringT` objektu.

### <a name="remarks"></a>Poznámky

Je třeba si uvědomit, tato paměť výjimky může dojít při každém použití operátoru přiřazení, protože často přiděleno nové úložiště pro uložení výsledný `CFixedStringT` objektu.

## <a name="see-also"></a>Viz také

[CStringT – třída](../../atl-mfc-shared/reference/cstringt-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Sdílené třídy ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)

