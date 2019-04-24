---
title: Implementace z vlastního správce řetězců (rozšířený způsob)
ms.date: 11/04/2016
helpviewer_keywords:
- IAtlStringMgr class, using
ms.assetid: 64ab7da9-47c1-4c4a-9cd7-4cc37e7f3f57
ms.openlocfilehash: 3854ffe205aa8e6cb9cfb800b9aa1473094fffaf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62235496"
---
# <a name="implementation-of-a-custom-string-manager-advanced-method"></a>Implementace z vlastního správce řetězců (rozšířený způsob)

V situacích, specializované můžete implementovat vlastní řetězec správce, který mění více než jen haldy, které se používá k přidělení paměti. V takovém případě je nutné ručně implementovat [iatlstringmgr –](../atl-mfc-shared/reference/iatlstringmgr-class.md) rozhraní jako správce vlastní řetězec.

Pokud to chcete udělat, je důležité se napřed seznámit jak [CStringT](../atl-mfc-shared/reference/cstringt-class.md) rozhraní používá ke správě jeho data řetězce. Každá instance `CStringT` má ukazatel [cstringdata –](../atl-mfc-shared/reference/cstringdata-class.md) struktury. Tato struktura proměnné délky obsahuje důležité informace o řetězec (jako je délka), a také skutečné znaková data řetězce. Každý správce vlastní řetězec zodpovídá za přidělování a uvolňování tyto struktury na žádost `CStringT`.

`CStringData` Struktura zahrnuje čtyři pole:

- [pStringMgr](../atl-mfc-shared/reference/cstringdata-class.md#pstringmgr) toto pole ukazuje na `IAtlStringMgr` rozhraní používá ke správě těchto dat řetězce. Když `CStringT` musí přerozdělit nebo uvolnit vyrovnávací paměti pro řetězec, které volá opětovné nebo bezplatný metody tohoto rozhraní předání `CStringData` strukturu jako parametr. Při přidělování `CStringData` struktura v správce řetězec je nutné nastavit toto pole tak, aby odkazoval vašemu nadřízenému vlastní řetězec.

- [nDataLength](../atl-mfc-shared/reference/cstringdata-class.md#ndatalength) toto pole obsahuje aktuální logické délku řetězce uloženy ve vyrovnávací paměti, s výjimkou ukončujícího znaku null. `CStringT` aktualizuje toto pole při změně délku řetězce. Při přidělování `CStringData` strukturu, správce řetězec musíte nastavit toto pole na hodnotu nula. Při opětovném přidělování `CStringData` strukturu, správce vlastní řetězec ponechte toto pole beze změny.

- [nAllocLength](../atl-mfc-shared/reference/cstringdata-class.md#nalloclength) toto pole obsahuje maximální počet znaků (s výjimkou ukončujícího znaku null), které mohou být uloženy ve vyrovnávací paměti pro tento řetězec bez přerozdělení ho. Pokaždé, když `CStringT` zvýšit logické délku řetězce, je potřeba nejprve ověří, toto pole a ujistěte se, že není dostatek místa ve vyrovnávací paměti. Pokud kontrola selže, `CStringT` zavolá vedoucímu vlastní řetězec aby mohla znovu přidělit vyrovnávací paměť. Při přidělování nebo změna přiřazení `CStringData` strukturu, je potřeba nastavit pole Minimální počet znaků požadovaných v *nChars* parametr [IAtlStringMgr::Allocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#allocate) nebo [IAtlStringMgr::Reallocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#reallocate). Pokud existuje více místa ve vyrovnávací paměti, než je požadováno, můžete nastavit tuto hodnotu tak, aby odrážely skutečné množství volného místa. Díky tomu `CStringT` rozrůstá řetězec tak, aby vyplnil celou přidělené místo na předtím, než bylo potřeba volat zpět do správce řetězců tak, aby mohla znovu přidělit vyrovnávací paměť.

- [nRefs](../atl-mfc-shared/reference/cstringdata-class.md#nrefs) toto pole obsahuje aktuální počet odkazů vyrovnávací paměti pro řetězec. Pokud je hodnota jednoho a pak jednu instanci `CStringT` používá vyrovnávací paměti. Kromě toho instance smí číst a upravovat obsah vyrovnávací paměti. Pokud je hodnota větší než, více instancí `CStringT` můžete použít vyrovnávací paměti. Protože je sdílený vyrovnávací paměti pro znaky, `CStringT` instance můžete pouze číst obsah vyrovnávací paměti. Chcete-li upravit obsah, `CStringT` nejprve vytvoří kopii tohoto vyrovnávací paměti. Pokud je hodnota záporná, jenom jeden výskyt `CStringT` používá vyrovnávací paměti. V takovém případě se považuje za vyrovnávací paměti uzamčen. Když `CStringT` instance používá uzamčené vyrovnávací paměti žádné další výskyty `CStringT` může sdílet vyrovnávací paměti. Tyto instance místo toho vytvořte kopii vyrovnávací paměti před práce s obsahem. Kromě toho `CStringT` instance pomocí uzamčené vyrovnávací paměti nebude pokoušet o sdílení vyrovnávací paměti jiných `CStringT` přiřazenou instanci. V takovém případě `CStringT` instance jiný řetězec zkopíruje do uzamčené vyrovnávací paměti.

   Při přidělování `CStringData` strukturu, je nutné nastavit toto pole tak, aby odrážely typ sdílení, která je pro vyrovnávací paměť. Pro většinu implementací nastavte tuto hodnotu do jednoho. To umožňuje obvyklé chování kopírování při zápisu sdílení. Nicméně pokud váš správce řetězců nepodporuje sdílení vyrovnávací paměti pro řetězec, nastavte pole na uzamčeném stavu. To přinutí `CStringT` pouze použití této vyrovnávací paměti pro instanci `CStringT` , které ho přidělilo.

## <a name="see-also"></a>Viz také:

[Správa paměti pomocí CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)
