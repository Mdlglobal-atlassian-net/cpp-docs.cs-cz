---
title: Podpora vícebajtových znakových sad (MBCS)
ms.date: 11/04/2016
helpviewer_keywords:
- MBCS [C++], about MBCS
- character sets [C++], multibyte
- multibyte characters [C++]
- MBCS [C++]
ms.assetid: b498733c-a1e1-45e3-8f26-d6da3cb5f2dd
ms.openlocfilehash: c21b5b1ff059f26558749e904894cb5d15572519
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808401"
---
# <a name="support-for-multibyte-character-sets-mbcss"></a>Podpora vícebajtových znakových sad (MBCS)

Vícebajtové znakové sady (MBCS) jsou starším přístupem k potřebě podporovat znakové sady, které nelze reprezentovat jediným bajtem, jako například japonštinu a čínštinu. Při novém vývoji by měla být pro všechny textové řetězce použita sada Unicode, snad kromě systémových řetězců, které koncový uživatel neuvidí. Sada MBCS je starou technologií a pro nový vývoj se nedoporučuje.

Většina běžných implementací znakové sady MBCS je dvoubajtové znakové sady (DBCS). Obecný Visual C++ a knihovnou MFC zejména se plně podporují pro znaky DBCS.

Ukázky najdete v souborech zdrojového kódu knihovny MFC.

Pro platformy použité na trzích, jehož jazyky použít velkých znakových sad nejlepší alternativou do kódování Unicode je znakové sady MBCS. MFC podporuje znakové sady MBCS pomocí internationalizace datové typy a funkce jazyka C za běhu. Stejné byste měli dělat ve vašem kódu.

V rámci znakové sady MBCS kódování znaků v 1 nebo 2 bajty. 2bajtové znaky, první nebo vedoucí bajt signalizuje, že ho a následující bajt jsou interpretovány jako jeden znak. První bajt pochází z rozsahu vyhrazené pro použití jako úvodní bajty kódů. Které rozsahy bajtů, může být vedoucí bajt závisí na znakové stránce. Například japonské znakovou stránku 932 používá jako vedoucí bajt rozsahu 0x81 prostřednictvím 0x9F, ale korejské znaková stránka 949 používá jiný rozsah.

Vezměte v úvahu všechny následující programování vaše znakové sady MBCS.

Znaky znakové sady MBCS v znaky znakové sady MBCS prostředí se mohou objevit v řetězce, jako jsou názvy souborů a adresářů.

### <a name="editing-operations"></a>Operace úprav

Operace v aplikacích znakové sady MBCS úprav pracovat na znaky, ne v bajtech. Blikající kurzor by neměl rozdělit znaku, **šipka vpravo** klíč by měl přesunout jeden znak doprava a tak dále. **Odstranit** měli odstranit znak; **Zpět** by měl znovu.

### <a name="string-handling"></a>Zpracování řetězců

V aplikaci, která používá znakovou sadu MBCS zpracování řetězce představuje zvláštní problémy. Znaky obou šířek směšování jeden řetězec; Proto nezapomeňte zkontrolovat úvodní bajty.

### <a name="run-time-library-support"></a>Podpora knihovny run-time

Podpora knihovny run-time jazyka C a MFC jednobajtové znakové sady MBCS a Unicode programování. Jednobajtové řetězce se zpracovávají `str` řadu funkcí modulu runtime, znakové sady MBCS řetězce se zpracovávají odpovídající `_mbs` funkce a řetězců v kódu Unicode se zpracovávají odpovídající `wcs` funkce. Implementace funkce člena třídy knihovny MFC pomocí přenosné běhové funkce, které se mapují správné okolností na normální `str` produktovou řadu funkcí, znakové sady MBCS funkce nebo funkce Unicode, jak je popsáno v "Přenositelnosti znakové sady MBCS/Unicode."

### <a name="mbcsunicode-portability"></a>Přenositelnosti znakové sady MBCS/Unicode

Pomocí souboru tchar.h záhlaví, můžete vytvořit jednobajtové znakové sady MBCS a Unicode aplikace ze stejného zdroje. Tchar.h definuje předponu makra *_tcs* , které mapují na `str`, `_mbs`, nebo `wcs` funkcí, podle potřeby. Pokud chcete vytvořit znakové sady MBCS, definujte symbol `_MBCS`. Chcete-li sestavit Unicode, definujte symbol `_UNICODE`. Ve výchozím nastavení `_UNICODE` je definováno pro aplikace knihovny MFC. Další informace najdete v tématu [mapování obecného textu v souboru tchar.h](../text/generic-text-mappings-in-tchar-h.md).

> [!NOTE]
>  Chování není definováno, pokud definujete obě `_UNICODE` a `_MBCS`.

Soubory hlaviček Mbctype.h a Mbstring.h definovat specifické znakové sady MBCS funkcemi a makry, která může být nutné v některých případech. Například `_ismbblead` zjistíte, zda konkrétní bajtů v řetězci je vedoucí bajt.

Mezinárodní přenositelnost kódu vašeho programu pomocí [Unicode](../text/support-for-unicode.md) nebo vícebajtové znakové sady (MBCS).

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Povolit znakovou sadu MBCS v mé aplikaci](../text/international-enabling.md)

- [Povolit kódování Unicode a MBCS v mé aplikaci](../text/internationalization-strategies.md)

- [Vytvoření mezinárodní programu pomocí znakové sady MBCS](../text/mbcs-programming-tips.md)

- [Prohlédnout souhrnné informace o programování znakové sady MBCS](../text/mbcs-programming-tips.md)

- [Další informace o mapování obecného textu pro přenositelnost šířky bajtu](../text/generic-text-mappings-in-tchar-h.md)

## <a name="see-also"></a>Viz také:

[Text a řetězce](../text/text-and-strings-in-visual-cpp.md)<br/>
[Podpora znakové sady MBCS v jazyku Visual C++](../text/mbcs-support-in-visual-cpp.md)
