---
title: 'CFixedStringT: Příklad z vlastního správce řetězců'
ms.date: 11/04/2016
helpviewer_keywords:
- CFixedStringT class, using a custom string manager
ms.assetid: 1cf11fd7-51b8-4b94-87af-02bc25f47dd6
ms.openlocfilehash: 2b6da5d4166b220ef63500d0154ab32dc72b40f4
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57740701"
---
# <a name="cfixedstringt-example-of-a-custom-string-manager"></a>CFixedStringT: Příklad z vlastního správce řetězců

Jedním z příkladů vlastní řetězec správce používá třída implementuje knihovny ATL [CFixedStringT](../atl-mfc-shared/reference/cfixedstringt-class.md), označované jako **CFixedStringMgr**. `CFixedStringT` je odvozen z [CStringT](../atl-mfc-shared/reference/cstringt-class.md) a implementuje řetězec, který přiděluje jeho znaková data jako součást `CFixedStringT` samotného objektu jako řetězec je menší než délka zadaná ve `t_nChars` parametrem šablony `CFixedStringT`. S tímto přístupem řetězec nemusí haldy vůbec, není-li délka řetězce překročí vyrovnávací paměť pevné velikosti. Protože `CFixedStringT` používá ne vždy haldy přidělit řetězcová data, nemůžete použít `CAtlStringMgr` jako jeho správce řetězců. Používá vlastní řetězec správce (`CFixedStringMgr`), implementující [iatlstringmgr –](../atl-mfc-shared/reference/iatlstringmgr-class.md) rozhraní. Toto rozhraní je popsán v [implementace z vlastního správce řetězců (rozšířené metody)](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md).

Konstruktor pro `CFixedStringMgr` přijímá tři parametry:

- *pData:* Ukazatel na pevné `CStringData` struktury, který se má použít.

- *nChars:* Maximální počet znaků `CStringData` struktura může obsahovat.

- *pMgr:* Ukazatel `IAtlStringMgr` rozhraní "správce zálohování řetězců".

Konstruktor ukládá hodnoty *pData* a *pMgr* v jejich příslušných členské proměnné (`m_pData` a `m_pMgr`). Potom nastaví délku vyrovnávací paměť na nulu, k dispozici délku odpovídající maximální velikosti vyrovnávací paměť pevné a počet odkazů na hodnotu -1. Určuje hodnotu počtu odkazů vyrovnávací paměť je uzamčen a použít tuto instanci `CFixedStringMgr` jako správce řetězců.

Označení vyrovnávací paměti podle uzamčené brání jiné `CStringT` instancí z obsahující sdílený odkaz do vyrovnávací paměti. Pokud jiné `CStringT` instance povoleno sdílení vyrovnávací paměti by bylo možné do vyrovnávací paměti obsažených `CFixedStringT` odstranit, zatímco ostatní řetězce stále používali vyrovnávací paměti.

`CFixedStringMgr` je úplnou implementaci daného `IAtlStringMgr` rozhraní. Implementace každou metodu je popsána samostatně.

## <a name="implementation-of-cfixedstringmgrallocate"></a>Provádění CFixedStringMgr::Allocate

Provádění `CFixedStringMgr::Allocate` nejprve zkontroluje, jestli na požadovanou velikost řetězce je menší než nebo rovna velikosti vyrovnávací paměť pevné (uložené v `m_pData` člen). Pokud pevná vyrovnávací paměť je příliš velká, `CFixedStringMgr` uzamkne pevná vyrovnávací paměť s nulovou délkou. Tak dlouho, dokud délka řetězce není nárůst velikosti vyrovnávací paměť pevné `CStringT` nebudete muset znovu přidělte vyrovnávací paměti.

Pokud požadovaná velikost řetězce je větší než vyrovnávací paměť pevné `CFixedStringMgr` požadavek předá do správce zálohování řetězců. Správce zálohování řetězců se předpokládá, že k přidělení vyrovnávací paměti z haldy. Ale před vrácením této vyrovnávací paměti `CFixedStringMgr` uzamčení vyrovnávací paměti a nahradí přípravné vyrovnávací paměti řetězce správce ukazatele s ukazatelem `CFixedStringMgr` objektu. Tím se zajistí, která se pokusí přerozdělit nebo uvolnit vyrovnávací paměti podle `CStringT` zavolá `CFixedStringMgr`.

## <a name="implementation-of-cfixedstringmgrreallocate"></a>Provádění CFixedStringMgr::ReAllocate

Provádění `CFixedStringMgr::ReAllocate` je velmi podobný jeho implementace `Allocate`.

Pokud je vyrovnávací paměť přerozděleni pevná vyrovnávací paměť a velikost požadované vyrovnávací paměti je menší než Pevná vyrovnávací paměť, se provádí bez přidělení. Nicméně pokud vyrovnávací paměť přerozděleni není pevná vyrovnávací paměť, musí být vyrovnávací paměť přidělena pomocí správce zálohování. V tomto případě správce zálohování slouží k přidělení vyrovnávací paměti.

Pokud je vyrovnávací paměť přerozděleni pevná vyrovnávací paměť a novou velikost vyrovnávací paměti je příliš velký, aby vyhovovaly pevná vyrovnávací paměť, `CFixedStringMgr` přidělí vyrovnávací paměť nového správce zálohování. Obsah vyrovnávací paměť pevné jsou poté zkopírován do nové vyrovnávací paměti.

## <a name="implementation-of-cfixedstringmgrfree"></a>Provádění CFixedStringMgr::Free

Provádění `CFixedStringMgr::Free` používá stejný vzor jako `Allocate` a `ReAllocate`. Pokud vyrovnávací paměť je uvolněna je pevná vyrovnávací paměť, metoda ji nastaví na nulovou délkou uzamčené vyrovnávací paměti. Pokud vyrovnávací paměť je uvolněna byla přidělena pomocí správce zálohování, `CFixedStringMgr` uvolnit ji využívá správce zálohování.

## <a name="implementation-of-cfixedstringmgrclone"></a>Provádění CFixedStringMgr::Clone

Provádění `CFixedStringMgr::Clone` vždy vrací ukazatel na správce zálohování místo `CFixedStringMgr` samotný. K tomu dojde, protože každá instance `CFixedStringMgr` může být přidružen pouze jednu instanci `CStringT`. Všechny ostatní instance `CStringT` pokusu o naklonování Správce by měl získat správci zálohy. místo toho. Je to proto, že správce zálohování podporuje sdílení.

## <a name="implementation-of-cfixedstringmgrgetnilstring"></a>Provádění CFixedStringMgr::GetNilString

Provádění `CFixedStringMgr::GetNilString` vrátí pevná vyrovnávací paměť. Z důvodu od vyhrazeného pracovníka korespondence `CFixedStringMgr` a `CStringT`, danou instanci `CStringT` nikdy používá více než jeden vyrovnávací paměti v čase. Nil řetězec a vyrovnávací paměti skutečné řetězce jsou proto nikdy potřebné ve stejnou dobu.

Pokaždé, když pevná vyrovnávací paměť není používán, `CFixedStringMgr` zajistí, že je inicializován s nulovou délkou. To umožňuje použít jako hodnotu nil řetězec. Jako přidání bonus `nAllocLength` členem pevná vyrovnávací paměť je vždycky nastavený na plnou velikost pevná vyrovnávací paměť. To znamená, že `CStringT` můžou růst řetězec bez volání [IAtlStringMgr::Reallocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#reallocate), i pro řetězec hodnotu nil.

## <a name="requirements"></a>Požadavky

**Záhlaví:** cstringt.h

## <a name="see-also"></a>Viz také:

[Správa paměti pomocí CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)
